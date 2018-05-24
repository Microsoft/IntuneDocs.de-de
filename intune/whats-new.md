---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titlesuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/08/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 81e6dba8cabb9339c7c83a3ac95fd7cf7c0a1fa7
ms.sourcegitcommit: 698bd1488be3a269bb88c077eb8d99df6e552a9a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Sie erhalten auch Informationen zu [bevorstehenden Änderungen](#whats-coming), [wichtige Hinweise](#notices) zum Dienst und Informationen zu [vorherigen Versionen](whats-new-archive.md). Einige Features werden im Laufe mehrerer Wochen bereitgestellt und sind in der ersten Woche möglicherweise nicht für alle Kunden verfügbar.

> [!Note]
> Informationen zu neuen Funktionen der hybriden Verwaltung mobiler Geräte (MDM) finden Sie auf der Seite [Neuheiten bei der hybriden Verwaltung mobiler Geräte](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### App management
  ### Device enrollment
  ### Device management
  ### Device configuration
  ### Intune apps
  ### Monitor and troubleshoot
  ### Role-based access control

-->   

## <a name="week-of-may-14-2018"></a>Woche vom 14. Mai 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Erforderliche Installation von Richtlinien, Apps, Zertifikaten und Netzwerkprofilen <!-- 1553555 -->

Administratoren können Endbenutzern den Zugriff auf Windows 10 RS4 Desktop verwehren, bis Richtlinien, Apps, Zertifikate und Netzwerkprofile während der Bereitstellung von AutoPilot-Geräten von Intune installiert wurden. Weitere Informationen finden Sie unter [Set up an enrollment status page (Einrichten einer Statusseite für die Registrierung)](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Konfigurieren von App-Schutzrichtlinien <!-- 2144597 Part 2 -->

Sie müssen jetzt im Azure-Portal nicht mehr auf das Dienstblatt Intune-App-Schutz gehen, sondern können einfach zu Intune navigieren. Es gibt derzeit nur einen Speicherort für App-Schutzrichtlinien in Intune. Beachten Sie, dass Sie bereits alle Ihre App-Schutzrichtlinien auf dem Blatt **Mobile App** in Intune unter **App-Schutzrichtlinien** finden. Diese Integration soll Ihre Cloudverwaltung vereinfachen. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden und Sie Ihre Richtlinien für den bedingten Zugriff ändern können. Sie finden die Intune App-Schutzrichtlinien (Intune App Policy Protection, APP) und die Richtlinien für den bedingten Zugriff (Conditional Access, CA) jetzt unter **Bedingter Zugriff** im Abschnitt **Verwalten** auf dem Blatt **Microsoft Intune** oder im Abschnitt **Sicherheit** auf dem Blatt **Azure Active Directory**. Weitere Informationen zum Ändern von Richtlinien für bedingten Zugriff finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Woche vom 7. Mai 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Unterstützung von Samsung Knox Mobile Enrollment (KME) <!--1112863-->

Wenn Sie Intune mit Samsung Knox Mobile Enrollment (KME) verwenden, können Sie eine große Anzahl unternehmenseigener Android-Geräte registrieren. Benutzer mit einer WLAN- oder Mobilfunknetzverbindung können die Registrierung mit nur wenigen Tippbewegungen ausführen, wenn sie ihre Geräte zum ersten Mal einschalten. Bei Verwendung der Knox Deployment App können Geräte über Bluetooth oder NFC registriert werden. Weitere Informationen finden Sie unter [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Anfordern von Hilfe im Unternehmensportal für Windows 10 <!-- 1874137 -->

Das Unternehmensportal für Windows 10 sendet App-Protokolle jetzt direkt an Microsoft, wenn der Benutzer den Workflow zum Abrufen von Hilfe zu einem Problem startet. So können Probleme, die Microsoft gemeldet werden, einfacher behoben und gelöst werden.

## <a name="week-of-april-23-2018"></a>Woche vom 23. April 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Kennungsunterstützung für die MAM-PIN unter Android<!-- 1438086 -->

Intune-Administratoren können zukünftig eine Anforderung für den Anwendungsstart festlegen, um eine Kennung anstatt einer numerischen MAM-PIN zu erzwingen. Wenn dies konfiguriert ist, muss der Benutzer eine Kennung festlegen und verwenden, wenn er dazu aufgefordert wird, bevor der Zugriff auf MAM-aktivierte Apps gewährt wird. Eine Kennung ist als numerische PIN mit mindestens einem Sonderzeichen oder einem Groß-/Kleinbuchstaben definiert. Intune unterstützt Kennungen auf ähnliche Weise wie die vorhandene numerische PIN. Es kann eine Mindestlänge über die Administratorkonsole festgelegt werden, sodass wiederholte Zeichen und Sequenzen möglich sind. Für dieses Feature ist die neueste Unternehmensportalversion unter Android erforderlich. Dieses Feature ist bereits für iOS verfügbar.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Unterstützung von branchenspezifischen Apps für macOS <!-- 1473977 -->
Microsoft Intune stellt eine Funktion zur Installation von macOS-LOB-Apps aus dem Azure-Portal bereit. Sie können eine macOS-LOB-App zu Intune hinzufügen, nachdem sie von dem in GitHub verfügbaren Tool vorab verarbeitet wurde. Wählen Sie im Azure-Portal auf dem Blatt **Intune** die Option **Mobile Apps** aus. Wählen Sie auf dem Blatt **Mobile Apps** die Option **Apps** > **Hinzufügen** aus. Wählen Sie auf dem Blatt **App hinzufügen** die Option **Branchen-App** aus. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Integrierte App-Zuweisung in Android for Work (AFW) für die Gruppen „Alle Benutzer“ und „Alle Geräte“ <!-- 1813073 -->
Sie können die integrierten Gruppen **Alle Benutzer** und **Alle Geräte** für die AFW-App-Zuweisung nutzen. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune installiert benötigte Apps, die von Benutzern deinstalliert werden. <!-- 1947010 -->
Wenn ein Endbenutzer eine benötigte App deinstalliert, installiert Intune die App automatisch innerhalb von 24 Stunden neu, anstatt auf den 7-tägigen Auswertungszyklus zu warten.

### <a name="device-configuration"></a>Gerätekonfiguration

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Geräteprofildiagramm und Statusliste zeigen alle Geräte in einer Gruppe <!-- 1449153 eeready -->
Wenn Sie ein Geräteprofil konfigurieren (**Gerätekonfiguration** > **Profile**), wählen Sie das Geräteprofil aus, z.B. iOS. Sie weisen dieses Profil einer Gruppe zu, die iOS-Geräte und Nicht-iOS-Geräte enthält. Im Grafikdiagramm ist zu sehen, dass das Profil dem iOS-Gerät *und* dem Nicht-iOS-Gerät zugewiesen wird (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**). Wenn Sie das Grafikdiagramm auf der Registerkarte **Übersicht** auswählen, werden unter **Gerätestatus** alle Geräte der Gruppe aufgeführt, nicht nur iOS-Geräte. 

Nach diesem Update wird im Grafikdiagramm (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**) nur die Anzahl für das spezifische Geräteprofil angezeigt. Wenn z.B. das Gerätekonfigurationsprofil für iOS-Geräte gilt, wird im Diagramm nur die Anzahl der iOS-Geräte aufgelistet. Wenn Sie das Grafikdiagramm auswählen und **Gerätestatus** öffnen, werden nur iOS-Geräte aufgelistet.

Während dieses Updates wird das Benutzerdiagramm vorübergehend entfernt. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Always On-VPN für Windows 10 <!--1333666 -->

Derzeit kann [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) auf Windows 10-Geräten mit einem benutzerdefinierten VPN (virtuelles privates Netzwerk), das über den OMA-URI erstellt wurde, verwendet werden.

Mit diesem Update können Administratoren Always On für VPN-Profile auf Windows 10 direkt in Intune im Azure-Portal aktivieren. Always On-VPN-Profile stellen automatisch eine Verbindung her, wenn Folgendes passiert:

- Benutzer melden sich an ihren Geräten an.
- Das Netzwerk auf dem Gerät ändert sich.
- Der Bildschirm wird auf dem Gerät wieder eingeschaltet, nachdem er ausgeschaltet war.

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Neue Druckereinstellungen für Education-Profile <!-- 1308900 -->

Für Education-Profile sind neue Einstellungen in der Kategorie **Drucker** unter **Drucker** > **Standarddrucker** > **Neue Drucker hinzufügen** verfügbar.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Anzeigen der Anrufer-ID im persönlichen Profil – Android for Work <!--1098984 -->
Wenn Sie ein persönliches Profil auf einem Gerät verwenden, sehen Endbenutzer möglicherweise keine Anrufer-ID-Details von einem Arbeitskontakt. 

Seit diesem Update gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Anrufer-ID des Arbeitskontakts im persönlichen Profil anzeigen

Wenn aktiviert (nicht konfiguriert), werden die Anruferdetails des Arbeitskontakts im persönlichen Profil angezeigt. Wenn blockiert, wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. 

Gilt für: Android-Arbeitsprofilgeräte unter Android OS 6.0 und höher.

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Neue Einstellungen für Windows Defender Credential Guard in den Endpoint Protection-Einstellungen <!--1102252 --><!--from 1802 and 1804-->

Mit diesem Update enthält [Windows Defender Central Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Gerätekonfiguration** > **Profile** > **Endpoint Protection**) die folgenden Einstellungen: 

- **Windows Defender Credential Guard**: Aktivieren des Credential Guards mit virtualisierungsbasierter Sicherheit. Wenn Sie dieses Feature aktivieren, können Sie Anmeldeinformationen beim nächsten Neustart schützen, wenn **Platform Security Level with Secure Boot** (Plattformsicherheitsstufe mit sicherem Start) und **Virtualization Based Security** (Virtualisierungsbasierte Sicherheit) aktiviert sind. Zu den Optionen gehören:
  - **Deaktiviert:** Wenn Credential Guard aktiviert war, mit aktivierter Option **Ohne Sperre aktiviert**, wird Credential Guard remote deaktiviert.

  - **Mit UEFI-Sperre aktivieren**: Gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden kann. Wenn Sie Credential Guard nach dem Aktivieren dieser Einstellung deaktivieren möchten, müssen Sie die Gruppenrichtlinie auf „Deaktiviert“ setzen. Entfernen Sie dann die Sicherheitsfunktionen von jedem Computer mit einem anwesenden Benutzer. Durch diese Schritte werden die in der UEFI vorgenommenen Konfigurationen gelöscht. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

  - **Ohne Sperre aktivieren**: Ermöglicht, Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie zu deaktivieren. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

Die folgenden, abhängigen Technologien werden automatisch aktiviert, wenn Sie Credential Guard konfigurieren: 

  - **Aktivieren der virtualisierungsbasierten Sicherheit (VBS:)** VBS wird beim nächsten Neustart aktiviert. Die virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen, und erfordert einen sicheren Start.
  - **Sicherer Start mit direktem Speicherzugriff (Direct Memory Access, DMA)**: Aktiviert VBS mit Schutzmaßnahmen wie sicherem Start und direktem Speicherzugriff. Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf ordnungsgemäß konfigurierten Geräten aktiviert. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Verwenden eines benutzerdefinierten Antragstellernames auf dem SCEP-Zertifikat <!-- 2064190 -->
Sie können den allgemeinen Namen **OnPremisesSamAccountName** für einen benutzerdefinierten Antragsteller auf einem SCEP-Zertifikatprofil verwenden. Sie können z. B. `CN={OnPremisesSamAccountName})` verwenden.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blockieren von Kamera und Bildschirmaufnahmen unter Android for Work <!-- 1098977 eeready-->
Es werden zwei neue Eigenschaften zum Blockieren beim Konfigurieren der Geräteeinschränkungen für Android-Geräte hinzugefügt: 
- Kamera: Der Zugriff auf alle Kameras auf dem Gerät wird blockiert.
- Bildschirmaufnahme: Die Bildschirmaufnahme wird blockiert,. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen.

Gilt für Android for Work.


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Neue Schritte für die Registrierung für Benutzer auf Geräten mit macOS High Sierra 10.13.2 und höher <!--1734567 -->
Mit macOS high Sierra 10.13.2 wurde das Konzept der „vom Benutzer genehmigten“ MDM-Registrierung eingeführt. Intune kann mithilfe genehmigter Registrierungen einige sicherheitsrelevante Einstellungen verwalten. Weitere Informationen finden Sie in der Dokumentation zur Apple-Unterstützung: https://support.apple.com/HT208019.

Geräte, die mithilfe des macOS-Unternehmensportals registriert wurden, werden so lange als „nicht vom Benutzer genehmigt“ angesehen, bis der Endbenutzer sie in den Systemeinstellungen manuell genehmigt. Dafür werden Benutzer im macOS-Unternehmensportal unter macOS 10.13.2 und höher nun direkt aufgefordert, ihre Registrierung am Ende des Registrierungsprozesses manuell zu genehmigen. Die Intune-Administratorkonsole meldet, ob ein registriertes Gerät vom Benutzer genehmigt wurde.



### <a name="device-management"></a>Geräteverwaltung

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) und Intune sind vollständig integriert <!-- EEready 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) zeigt die Risikostufe von Windows 10-Geräten an. In Windows Defender Security Center (ATP-Portal) können Sie eine Verbindung mit Microsoft Intune herstellen. Nach der Erstellung wird mit einer Konformitätsrichtlinie von Intune eine akzeptable Bedrohungsstufe bestimmt. Wenn die Bedrohungsstufe überschritten wird, kann eine Azure Active Directory-Richtlinie (AD) für bedingten Zugriff den Zugriff auf andere Apps in Ihrer Organisation blockieren.

Dieses Feature ermöglicht ATP, Dateien zu überprüfen, Bedrohungen zu erkennen und jedes Risiko auf Ihren Windows 10-Geräten zu melden.

Siehe [Aktivieren von Windows Defender ATP mit bedingtem Zugriff in Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Unterstützung für Geräte ohne Benutzer <!-- 1637553 -->
Intune unterstützt die Möglichkeit, Konformität auf einem benutzerlosen Gerät zu bewerten, z.B. einem Microsoft Surface Hub-Gerät. Die Konformitätsrichtlinie kann sich auf bestimmte Geräte beziehen. Die Konformität (und auch Nichtkonformität) kann für Geräte festgelegt werden, die über keinen zugewiesenen Benutzer verfügen.

#### <a name="delete-autopilot-devices----1713650---"></a>Löschen von AutoPilot-Geräten <!-- 1713650 -->
Intune-Administratoren können [AutoPilot-Geräte löschen](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Verbesserte Erfahrung bei der Gerätelöschung <!--1832333 -->
Sie müssen nicht länger Unternehmensdaten entfernen oder das Gerät auf Werkseinstellungen zurücksetzen, bevor sie es [aus Intune löschen](devices-wipe.md#delete-devices-from-the-intune-portal).

Melden Sie sich für die neue Benutzererfahrung in Intune an, und wählen Sie **Geräte** > **Alle Geräte** > Name des Geräts > **Löschen** aus.

Wenn Sie die Bestätigung zum Zurücksetzen bzw. der Deaktivierung beibehalten möchten, können Sie die Standardvorgehensweise für den Gerätelebenszyklus verwenden, indem Sie vor der Option **Löschen** die Optionen **Entfernen von Unternehmensdaten** und **Auf Werkseinstellungen zurücksetzen** ausgeben. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Wiedergeben von Sound im Modus für verlorene Geräte <!-- 1947769 -->
Wenn sich überwachte iOS-Geräte im [Modus für verlorene Geräte](device-lost-mode.md) in MDM (Mobile Device Management, Verwaltung mobiler Geräte) befinden, können Sie [einen Sound wiedergeben](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Geräte** > **Alle Geräte** > iOS-Gerät auswählen > **Übersicht** > **More** (Mehr)). Der Sound wird so lange wiedergegeben, bis der Modus für verlorene Geräte beendet wird, oder bis der Benutzer den Sound auf dem Gerät deaktiviert. Gilt für Geräte unter iOS 9.3 und höher.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Blockieren und Zulassen von Webergebnissen in auf einem Intune-Gerät durchgeführten Suchvorgängen <!--1972804-->

Administratoren können jetzt Webergebnisse bei Suchvorgängen auf Geräten blockieren.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Verbesserte Fehlermeldungen bei Uploadfehlern für MDM-Pushzertifikate <!-- 2172331 -->

In der Fehlermeldung wird erklärt, dass dieselbe Apple-ID beim Erneuern eines vorhandenen MDM-Zertifikats verwendet werden muss.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testen des Unternehmensportals für macOS auf virtuellen Computern <!-- 2216679 -->

Wir haben einen Leitfaden veröffentlicht, der IT-Administratoren beim Testen der Unternehmensportal-App für macOS auf VMs in Parallels Desktop und VMware Fusion unterstützt. Weitere Informationen finden Sie unter [Registrieren von virtuellen macOS-Computern zu Testzwecken](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Benutzeroberfläche

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Die Gerätekacheln im Windows 10-Unternehmensportal wurden verbessert <!--2213364 -->

Die Kacheln wurden aktualisiert und sind jetzt zugänglicher für Benutzer mit eingeschränktem Sehvermögen. Die Leistung wurde für Bildschirmlesetools wurde verbessert.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Senden von Diagnoseberichten in der Unternehmensportal-App für macOS <!-- 2216677 -->
Die Unternehmensportal-App für macOS-Geräte wurde aktualisiert, um die Kundenerfahrung beim Melden von auf Intune bezogene Fehler zu verbessern. Ihre Mitarbeiter können über die Unternehmensportal-App folgende Aktionen durchführen:

- Hochladen von Diagnoseberichten direkt an das Microsoft-Entwicklerteam
- Die ID eines Vorfalls per E-Mail an das IT-Supportteams Ihres Unternehmens senden

Weitere Informationen finden Sie unter [Melden von macOS-Fehlern](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune wird an Fluent Design System in der Unternehmensportal-App für Windows 10 angepasst <!-- 1195010 WNready -->
Die Intune-Unternehmensportal-App für Windows 10 wurde mit der [Navigationsansicht von Fluent Design System](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics) aktualisiert. An der Seite der App befindet sich eine statische, vertikale Liste aller Seiten der obersten Ebene. Klicken Sie auf einen beliebigen Link, um Seiten schnell anzuzeigen und zwischen ihnen zu wechseln. Dies ist das erste von mehreren Updates, die wir Ihnen im Rahmen unserer fortlaufenden Bestrebungen präsentieren werden, die Intune-Benutzeroberfläche zu optimieren. Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Woche vom 16. April 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Verwenden des Cisco AnyConnect-Clients für iOS <!-- EEready 1333708 -->

Wenn Sie ein neues VPN-Profil für iOS erstellen, stehen Ihnen jetzt zwei Optionen zur Verfügung: **Cisco AnyConnect** und **Cisco Legacy AnyConnect**. Die Cisco AnyConnect-Profile unterstützen 4.0.7x und neuere Versionen. Bereits existierende iOS Cisco AnyConnect VPN-Profile werden als **Cisco Legacy AnyConnect** bezeichnet und auch weiterhin mit Cisco AnyConnect 4.0.5x und älteren Versionen funktionieren.

> [!NOTE]
> Diese Änderung gilt nur für iOS. Es wird weiterhin nur eine Option von Cisco AnyConnect für Android-, Android for Work- und macOS-Plattformen geben.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf-registrierte macOS-Geräte können jetzt bei Intune registriert werden <!-- 2370684 -->

Die Versionen 1.3 und 1.4 des macOS-Unternehmensportals konnten nicht erfolgreich Jamf-Geräte bei Intune registrieren. Version 1.4.2 des macOS-Portals behebt dieses Problem.


## <a name="week-of-april-9-2018"></a>Woche vom 9. April 2018

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Aktualisierter Hilfebereich der Unternehmensportal-App für Android <!-- 1631531 -->

Wir haben den Hilfebereich der Unternehmensportal-App für Android aktualisiert, sodass er den Best Practices der Android-Plattform entspricht. Wenn Benutzer jetzt ein Problem in der App haben, können sie auf **Menü** > **Hilfe** tippen und Folgendes tun:
- Diagnoseprotokolle an Microsoft senden
- E-Mail, die das Problem beschreibt, und die Incident-ID an einen Supportmitarbeiter des Unternehmens senden  

Unter [Senden von Protokollen an den Support Ihres Unternehmens per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) und [Senden von Protokollen an Unternehmensportalentwickler für Android-Geräte](/intune-user-help/send-logs-to-microsoft-android) können Sie den aktualisierten Hilfebereich kennenlernen.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Neues Diagramm zum Trend von fehlgeschlagenen Registrierungen und Tabelle mit Gründen für das Fehlschlagen <!-- 1471783 -->

Auf der Seite „Enrollment Overview“ (Registrierungsübersicht) können Sie sich den Trend bei fehlgeschlagenen Registrierungen und die fünf häufigsten Gründe für das Fehlschlagen anzeigen lassen. Wenn Sie auf das Diagramm oder die Tabelle klicken, können Sie sich im Detail Informationen zu den Fehlern ansehen und erhalten Ratschläge zur Fehlerbehebung und zur Wiederherstellung.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Update zum Konfigurieren der App-Schutzrichtlinien <!-- 2144597 -->

Sie werden in Microsoft Intune im Azure-Portal kurzzeitig von dem Dienstblatt **Intune-Schutz für Apps** auf das Blatt **Mobile App** umgeleitet. Beachten Sie, dass alle Ihre App-Schutzrichtlinien bereits auf dem Blatt **Mobile App** in Intune unter der App-Konfiguration vorhanden sind. Statt Intune-App-Schutz aufzurufen, verwenden Sie einfach Intune. Im April 2018 beenden wir die Umleitung und entfernen das Dienstblatt **Intune-App-Schutz** vollständig, sodass es nur einen Ort für App-Richtlinien in Intune gibt. 

**Wie wirkt sich das auf mich aus?**
Sowohl eigenständige Intune-Kunden als auch hybride Kunden (die Intune mit Configuration Manager verwenden) sind von dieser Änderung betroffen. Diese Integration soll Ihre Cloudverwaltung vereinfachen.

**Was muss ich als Vorbereitung auf diese Änderung tun?**
Markieren Sie **Intune** und nicht das Dienstblatt **Intune-Schutz für Apps** als Favorit, und machen Sie sich in Intune mit dem Richtlinienworkflow für den App-Schutz auf der Blatt **Mobile App** vertraut. Es wird zwar für einen kurzen Zeitraum eine Umleitung eingerichtet, aber danach wird das Blatt **Intune-Schutz für App** entfernt. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden und Sie Ihre Richtlinien für den bedingten Zugriff ändern können. Weitere Informationen zum Ändern von Richtlinien für bedingten Zugriff finden Sie unter [Bedingter Zugriff in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Weitere Informationen finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Woche vom 2. April 2018

### <a name="intune-apps"></a>Intune-Apps

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Update der Benutzeroberfläche für die Unternehmensportal-App für iOS <!--1412866 -->
Für die Unternehmensportal-App für iOS wurde ein großes Update für die Benutzeroberfläche veröffentlicht. Das Update enthält eine vollständige visuelle Überarbeitung, einschließlich eines moderneren Designs und einer verbesserten Handhabung. Wir haben die Funktion der App beibehalten, haben jedoch die Benutzerfreundlichkeit und Barrierefreiheit verbessert.  

Weiterhin sind enthalten:
- Support für iPhone X
- Schnellerer App-Start und Reaktionszeiten, damit Benutzer Zeit sparen
- Zusätzliche Statusanzeigen, damit Benutzer stets mit den neuesten Statusinformationen versorgt sind
- Verbesserungen beim Uploadprozess von Protokollen. Wenn Sie also auf ein Problem stoßen, können Sie es viel einfacher melden.  

Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md).

#### <a name="protect-on-premise-exchange-data-using-intune-app-and-ca----1056954---"></a>Schützen der lokalen Exchange-Daten mithilfe von Intune-App-Schutzrichtlinien und dem bedingten Zugriff <!-- 1056954 -->
Sie können jetzt lokale Exchange-Daten mit Outlook Mobile mithilfe von Intune App-Schutzrichtlinien (App Policy Protection, APP) und dem bedingten Zugriff (Conditional Access, CA) schützen. Um eine App-Schutzrichtlinie im Azure-Portal hinzuzufügen oder zu ändern, klicken Sie auf **Microsoft Intune** > **Mobile Apps** > **App-Schutzrichtlinien**. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx) erfüllen.

## <a name="week-of-march-26-2018"></a>Woche vom 26. März 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Benachrichtigungen zu ablaufenden branchenspezifischen iOS-Apps für Microsoft Intune <!-- 748789 -->

Im Azure-Portal werden Sie von Intune über ablaufende branchenspezifische iOS-Apps benachrichtigt. Beim Hochladen einer neuen Version der branchenspezifischen iOS-App entfernt Intune die Ablaufbenachrichtigung aus der Liste. Diese Ablaufbenachrichtigung ist nur für neu hochgeladene branchenspezifische iOS-Apps aktiviert und wird 30 Tage vor Ablauf des Bereitstellungsprofils der branchenspezifischen iOS-App angezeigt. Wenn es abgelaufen ist, ändert sich die Benachrichtigung in „Abgelaufen“.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Anpassen des Unternehmsportaldesigns mit Hexadezimalcode <!--1049561 -->

Die Designfarben lassen sich in den Unternehmensportal-Apps mithilfe von Hexadezimalcode anpassen. Wenn Sie Ihren Hexadezimalcode eingeben, legt Intune fest, welche Textfarbe den stärksten Kontrast zur Hintergrundfarbe bildet. In einer Vorschau können Sie die Textfarbe und das Unternehmenslogo mit den Farben unter **Mobile Apps** > **Unternehmensportal** abgleichen.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen für Android Enterprise <!-- 1813081 -->

Android Enterprise (zuvor Android for Work) unterstützt das Einschließen und Ausschließen von Gruppen, jedoch nicht die vorab erstellte Gruppe **Alle Benutzer** und die integrierte Gruppe **Alle Geräte**. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Geräteverwaltung

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Neue Sicherheitserweiterungen für Intune <!-- 1637539 -->   

Wir haben in Intune in Azure eine Umschaltfläche eingeführt, mit der eigenständige Intune-Kunden Geräte ohne zugewiesene Richtlinien als **Konform** (Sicherheitsfeature deaktiviert) oder **Nicht konform** (Sicherheitsfeature aktiviert) einstufen können. So wird sichergestellt, dass erst nach der Auswertung der Gerätekonformität Zugriff auf Ressourcen besteht.

Die Auswirkungen dieses Features auf Sie sind davon abhängig, ob Sie bereits Konformitätsrichtlinien zugewiesen haben oder nicht.

- Wenn Sie über ein neues oder bereits bestehendes Konto verfügen und Ihren Geräten bislang noch keine Konformitätsrichtlinien zugewiesen sind, wird die Umschaltfläche automatisch auf **Konform** festgelegt. Das Feature ist in der Konsole standardmäßig deaktiviert. Daher hat es keine Auswirkungen auf Benutzer.
- Wenn Sie bereits ein vorhandenes Konto haben und über Geräte verfügen, denen eine Konformitätsrichtlinie zugewiesen ist, wird die Umschaltfläche automatisch auf **Nicht konform** festgelegt. Ab der Bereitstellung des März-Updates ist dieses Feature standardmäßig aktiviert.

Wenn Sie Konformitätsrichtlinien mit bedingtem Zugriff verwenden und das Feature aktiviert ist, wird jedes Gerät blockiert, dem nicht mindestens eine Konformitätsrichtlinie zugewiesen ist. Benutzern, die diesen Geräten zugeordnet sind und zuvor auf E-Mails zugreifen konnten, können dies nicht mehr, wenn Sie nicht allen Geräten mindestens eine Konformitätsrichtlinie zuweisen.   

Beachten Sie, dass der Standardstatus der Umschaltfläche ab dem Update vom März für Intune zwar in der Benutzeroberfläche angezeigt wird, jedoch nicht sofort durchgesetzt wird. Alle Änderungen, die Sie an der Einstellung der Umschaltfläche vornehmen, wirken sich nicht auf die Gerätekonformität aus, bis die Umschaltfläche für Ihr Konto aktiviert wird. Wir informieren Sie über das Nachrichtencenter, wenn dieser Vorgang abgeschlossen ist. Dies kann nach dem Update des Intune-Diensts vom März ein paar Tage dauern.

**Weitere Informationen**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Verbesserte Erkennung von Jailbreaks <!-- 846515 -->

Die verbesserte Erkennung von Jailbreaks ist eine neue Konformitätseinstellung, die in Intune die Auswertung von Geräten mit Jailbreaks verbessert. Durch die Einstellung verbindet sich das Gerät häufiger mit Intune. Dazu wird der Ortungsdienst des Geräts benötigt, was Auswirkungen auf den Batterieverbrauch hat.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Zurücksetzen von Kennwörtern für Android O-Geräte <!-- 1238299 -->
Sie können die Kennwörter für registrierte Android 8.0-Geräte mit Arbeitsprofilen zurücksetzen. Wenn Sie die Anforderung „Kennwort zurücksetzen“ an ein Android 8.0-Gerät senden, legt dieses ein neues Kennwort zum Entsperren des Geräts oder eine verwaltete Profilabfrage für den aktuellen Benutzer fest. Das Kennwort oder die Abfrage wird gesendet und wird sofort wirksam.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ausrichten von Konformitätsrichtlinien auf Geräte in Gerätegruppen <!--1307012 -->

Sie können Konformitätsrichtlinien gezielt für Benutzer in Benutzergruppen erstellen. Mit diesem Update können Sie auch Konformitätsrichtlinien gezielt für Geräte in Gerätegruppen erstellen. Geräte in solchen Gerätegruppen empfangen keine Konformitätsaktionen.

#### <a name="new-management-name-column----1333586---"></a>Namensspalte „New Management“ <!-- 1333586 -->
 Im Blatt „Geräte“ ist eine neu Spalte namens **Verwaltungsname** verfügbar. Dies ist ein automatisch generierter und nicht bearbeitbarer Name, der basierend auf der folgenden Formel vom Gerät zugewiesen wird:
- Standardname für alle Geräte: <username><em><devicetype></em><enrollmenttimestamp>
- Für Geräte, die durch Massenhinzufügen hinzugefügt wurden: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

Dies ist eine optionale Spalte im Blatt „Geräte“. Sie ist nicht standardmäßig, sondern nur über die Spaltenauswahl verfügbar. Diese neue Spalte hat keine Auswirkungen auf den Gerätenamen.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS-Geräte werden alle 15 Minuten zur Eingabe einer PIN aufgefordert <!--1550837 -->
Nachdem einem iOS-Gerät eine Konformitäts- oder Konfigurationsrichtlinie hinzugefügt wurde, werden Benutzer alle 15 Minuten dazu aufgefordert, eine PIN festzulegen. Diese Aufforderung erhalten Benutzer regelmäßig, bis sie eine PIN festlegen.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Planen von automatischen Updates <!--1805514 -->
Mit Intune können Sie die Installation von automatischen Updates mithilfe von [Einstellungen für Windows-Updateringe](windows-update-for-business-configure.md) steuern. Seit diesem Update können Sie sich wiederholende Updates planen, einschließlich der Woche, dem Tag und der Uhrzeit.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Verwenden eines vollständig definierten Namens als Antragsteller für das SCEP-Zertifikat <!--2221763 -->
Wenn Sie ein SCEP-Zertifikatsprofil erstellen, geben Sie den Antragstellernamen ein. Seit diesem Update können Sie den vollständig definierten Namen als Antragstellernamen verwenden. Wählen Sie für **Antragstellername** die Option **benutzerdefiniert** aus, und geben Sie dann `CN={{OnPrem_Distinguished_Name}}` ein. Damit Sie die `{{OnPrem_Distinguished_Name}}`-Variable verwenden können, stellen Sie sicher, dass das `onpremisesdistingishedname`-Benutzerattribut mithilfe von [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Azure AD synchronisiert ist.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Aktivieren der Kontaktfreigabe über Bluetooth: Android for Work <!--1098983 -->
In der Standardeinstellung verhindert Android, dass Kontakte im Arbeitsprofil mit Bluetooth-Geräten synchronisiert werden. Das Ergebnis ist, dass Arbeitsprofilkontakte nicht auf der Anrufer-ID für Bluetooth-Geräte angezeigt werden.

Seit diesem Update gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Kontaktfreigabe über Bluetooth

Der Intune-Administrator kann diese Einstellungen konfigurieren, um die Freigabe zu aktivieren. Dieses Feature ist nützlich, wenn Sie ein Gerät mit einem Bluetooth-Gerät in einem Fahrzeug koppeln möchten, das die Anrufer-ID für Freisprechgeräte anzeigt. Wenn das Feature aktiviert ist, werden Arbeitsprofilkontakte angezeigt. Wenn das Feature nicht aktiviert ist, werden Arbeitsprofilkontakte nicht angezeigt.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Konfigurieren von Gatekeeper zum Steuern der Downloadquelle der macOS-App <!-- 1690459 -->

Sie können Gatekeeper konfigurieren und Ihre Geräte schützen, indem Sie steuern, von wo die Apps heruntergeladen werden können. Sie können die folgenden Downloadquellen konfigurieren: **Mac App Store**, **Mac App Store und verifizierte Entwickler** und **Anywhere** (Alle Quellen). Außerdem können Sie konfigurieren, dass Benutzer eine App mithilfe von STRG+Klick installieren können, um diese Gatekeeper-Steuerelemente außer Kraft zu setzen.

Diese Einstellungen finden Sie unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Konfigurieren der Firewall der Mac-Anwendung <!-- 1690461 -->

Sie können die Firewall der Mac-Anwendung konfigurieren. Damit können Sie Verbindungen auf einer „pro Anwendung“-Basis anstatt einer „per Port“-Basis steuern. Dies erleichtert es Ihnen, die Vorteile des Firewall-Schutzes zu nutzen und zu verhindern, dass unerwünschte Apps die Kontrolle über für zulässige Apps offenen Netzwerk-Ports übernehmen.

Dieses Feature kann unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

Nachdem Sie die Firewall-Einstellung aktivieren, können Sie die Firewall mithilfe von zwei Strategien konfigurieren:

- Blockieren von allen eingehenden Verbindungen

   Sie können alle eingehenden Verbindungen für die Zielgeräte blockieren. Wenn Sie sich dazu entscheiden, werden eingehende Verbindungen für alle Apps blockiert.

- Zulassen oder Blockieren von bestimmten Apps

   Sie können den Empfang von eingehenden Verbindungen für bestimmte Apps zulassen oder blockieren. Sie können auch den geschützten Modus aktivieren, um zu verhindern, dass der Computer auf Suchanforderungen reagiert.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Detaillierte Fehlercodes und Meldungen <!-- 1376342 -->

In Ihrer Gerätekonfiguration können jetzt ausführlichere Fehlercodes und Fehlermeldungen angezeigt werden. Diese verbesserte Berichterstellung zeigt die Einstellungen, den Status dieser Einstellungen und Details zur Problembehandlung an.

##### <a name="more-information"></a>Weitere Informationen

- Blockieren von allen eingehenden Verbindungen

   Dadurch wird verhindert, dass alle Freigabedienste (z.B. Dateifreigabe und Bildschirmfreigabe) eingehende Verbindungen empfangen. Die folgenden Systemdienste sind noch zum Empfangen von eingehenden Verbindungen zugelassen:
  - configd - implementiert DHCP und andere Netzwerkkonfigurationsservices
  - mDNSResponder - implementiert Bonjour
  - racoon -  implementiert IPSec

    Stellen Sie sicher, dass **Eingehende Verbindungen** auf **Nicht konfiguriert** (und nicht auf **Block** (Blockieren)) festgelegt ist, um Freigabedienste zu verwenden.

- Geschützter Modus

   Aktivieren Sie diese Option, um den Computer daran zu hindern, auf Suchanforderungen zu reagieren. Der Computer antwortet weiterhin auf eingehende Anforderungen von autorisierten Apps. Unerwartete Anforderungen, wie z.B. ICMP (Ping), werden ignoriert.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Deaktivieren von Prüfungen bei Geräteneustart <!--1805490 -->
Mit Intune können Sie die [Verwaltung von Softwareupdates]](windows-update-for-business-configure.md) steuern. Seit diesem Update ist die Eigenschaft <strong>Neustartüberprüfungen</strong> verfügbar und standardmäßig aktiviert. Wählen Sie <strong>Überspringen</strong> aus, um die üblichen Überprüfungen zu überspringen, wenn Sie ein Gerät neu starten (z.B. aktive Benutzer, Akkustand usw.).

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Neue Windows 10 Insider Preview-Kanäle für Bereitstellungsringe verfügbar <!-- 1746293 -->
Sie haben von nun an die Möglichkeit, zwischen den folgenden Windows 10 Insider Preview-Wartungskanälen zu wählen, wenn Sie einen Windows 10-Bereitstellungsring erstellen:
- Windows-Insider-Build: schnell
- Windows-Insider-Build: langsam
- Windows-Insider-Build veröffentlichen 

Weitere Informationen zu diesen Kanälen finden Sie unter [Verwalten von Insider Preview-Builds](https://insider.windows.com/en-us/for-business-organization-admin/).   
Weitere Informationen zum Erstellen von Bereitstellungskanälen in Intune finden Sie unter [Verwalten von Softwareupdates](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Intune-Apps

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Verbesserte Unternehmensportal-Registrierung <!-- 1874230 eeready-->
Benutzer, die ein Gerät mithilfe des Unternehmensportals unter Windows 10-Version 1703 oder höher registrieren, können den ersten Registrierungsschritt jetzt innerhalb der App ausführen.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens und Surface Hub erscheinen nun in Gerätelisten <!--1725868 -->
Die Anzeige von über Intune registrierten HoloLens- und Surface Hub-Geräten in der Unternehmensportal-App wird jetzt unter Android unterstützt.

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>Benutzerdefinierte Buchkategorien für per Volumenlizenz erworbene eBooks <!-- 1488911 -->
Sie können benutzerdefinierte eBook-Kategorien erstellen und diesen dann per Volumenlizenz erworbene eBooks zuweisen. Endbenutzer können dann die neu erstellten eBook-Kategorien und den Kategorien zugewiesene Bücher sehen. Weitere Informationen finden Sie unter [Verwalten von per Volumenlizenz erworbenen Apps und Büchern mit Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Änderungen der Unterstützung der Option „Feedback senden“ in der Unternehmensportal-App für Windows <!-- 2070166 -->
Ab dem 30. April 2018 funktioniert die Option **Feedback senden** in der Unternehmensportal-App für Windows nur noch auf Geräten, auf denen das Windows 10 Anniversary Update (1607) und höher ausgeführt wird. Die Option zum Senden von Feedback wird bei Verwendung der Unternehmensportal-App für Windows unter folgenden Versionen nicht mehr unterstützt:  
- Windows 10, Version 1507  
- Windows 10, Version 1511  
- Windows Phone 8.1 

Wenn Ihr Gerät unter Windows 10 RS1 oder höher ausgeführt wird, können Sie die neueste Version der Windows-Unternehmensportal-App aus dem Store herunterladen. Bei Ausführung einer nicht unterstützten Version können Sie uns über die folgenden Kanäle weiterhin Feedback senden: 
- Die Feedback-Hub-App unter Windows 10
- E-Mail an WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Neue Einstellungen für Windows Defender Application Guard <!-- 1631890 -->

- **Enable graphics acceleration** (Grafikbeschleunigung aktivieren): Administratoren können einen virtuellen Grafikprozessor für Windows Defender Application Guard aktivieren. Über diese Einstellung kann die CPU Grafiken auslagern, die an die vGPU rendern. Dadurch kann die Leistung verbessert werden, wenn Sie mit grafikintensiven Websites arbeiten oder ein Video im Container ansehen.

- **SaveFilestoHost**: Administratoren können konfigurieren, dass Dateien des Browsers „Microsoft Edge“, der im Container ausgeführt wird, an das Hostdateisystem übergeben werden. Wenn Sie diese Einstellung aktivieren, können Benutzer Dateien von Microsoft Edge im Container auf das Hostdateisystem herunterladen.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Anwenden von MAM-Richtlinien je nach Verwaltungsstatus <!-- 1665993 -->
Sie können MAM-Richtlinien je nach Verwaltungsstatus des Geräts anwenden:
- **Android-Geräte:** Sie können Richtlinien auf nicht verwaltete Geräte, mit Intune verwaltete Geräte und mit Intune verwaltete Android Enterprise-Profile (früher Android for Work) anwenden.
- **iOS-Geräte:** Sie können Richtlinien auf nicht verwaltete Geräte (nur MAM) oder von Intune verwaltete Geräte anwenden.

    > [!NOTE]
    > - iOS-Unterstützung für diese Funktion wird im April 2018 eingeführt.

Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Sprachverbesserungen in der Unternehmensportal-App für Windows <!-- 1683758 -->
Die Sprache im Unternehmensportal für Windows 10 wurde verbessert und ist nun benutzerfreundlicher und unternehmensspezifischer. Unter [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md) finden Sie einige Beispielabbildungen der Neuerungen.

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Neue Datenschutzfunktionen in Dokumenten für Benutzer <!-- 1440709 -->
Wir arbeiten daran, Benutzern mehr Kontrolle über ihre Daten und den Datenschutz zu geben. Daher haben wir Updates für unsere Dokumente veröffentlicht, in denen erklärt wird, wie Sie von den Unternehmensportal-Apps lokal gespeicherte Daten anzeigen und entfernen. Sie finden diese Updates in den folgenden Quellen:

- **Android:** [Entfernen der Registrierung Ihres Android-Geräts bei Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, wenn der Benutzer die Nutzungsbedingungen abgelehnt hat:** [Remove your device management if you declined „Terms of Use“ (Entfernen der Geräteverwaltung, wenn die Nutzungsbedingungen abgelehnt wurden)](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS:** [Entfernen Ihres iOS-Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows:** [Entfernen Ihres Windows-Geräts aus Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Woche vom 19. März 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exportieren aller Geräte in CSV-Dateien in Internet Explorer, Edge oder Chrome <!-- 2258071 -->
Unter **Geräte** > **Alle Geräte** können Sie die Geräte mithilfe der Option **Exportieren** in eine CSV-formatierte Liste exportieren. Internet Explorer-Benutzer mit mehr als 10.000 Geräten können ihre Geräte in mehrere Dateien exportieren. Jede Datei verfügt über bis zu 10.000 Geräte.

Edge- und Chrome-Benutzer mit mehr als 30.000 Geräten können ihre Geräte ebenfalls in mehrere Dateien exportieren. Jede Datei verfügt dann über bis zu 30.000 Geräte.

Über die Option [Geräte verwalten](device-management.md) erhalten Sie weitere Informationen dazu, wie Sie die verwalteten Geräte verwenden können.

## <a name="week-of-march-12-2018"></a>Woche vom 12. März 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen das einmalige Anmelden dafür (Public Preview) <!-- 710595 -->

Mithilfe von Azure Active Directory (Azure AD) können Sie jetzt den Zugriff auf Websites auf mobilen Geräten auf die Intune Managed Browser-App beschränken. In Managed Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird. Weitere Informationen finden Sie unter [Access controls in Azure Active Directory conditional access (Zugriffsteuerung über den bedingten Zugriff für Azure Active Directory)](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Unternehmensportal-App für visuelle Android-Updates <!--976944 -->

Die Unternehmensportal-App wird für Android aktualisiert, um den [Material Design](https://material.io/)-Richtlinien von Android zu entsprechen. Bilder der neuen Symbole finden Sie im Artikel zu den [Neuerungen der App-Benutzeroberfläche](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Neue Einstellungen für Windows Defender Exploit Guard <!-- 1631893 -->

Es sind jetzt sechs neue Einstellungen zur <strong>Verringerung der Angriffsfläche</strong> und erweiterte Funktionen zum <strong>Überwachten Ordnerzugriff: Ordnerschutz</strong> verfügbar. Diese Einstellungen finden Sie unter: Gerätekonfiguration\Profiles\
Erstellen Sie profile\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche

|Name der Einstellung  |Einstellungsoptionen  |Beschreibung  |
|---------|---------|---------|
|Erweiterter Schutz vor Ransomware|Enabled, Audit, Not configured (Aktiviert, Überwachung, Nicht konfiguriert)|Verwendung eines offensiven Schutzes vor Ransomware.|
|Flag credential stealing from the Windows local security authority subsystem (Abgreifen von Anmeldeinformationen über das Subsystem der lokalen Sicherheitsautorität von Windows kennzeichnen)|Aktiviert, Überwachung, Nicht konfiguriert|Flag credential stealing from the Windows local security authority subsystem (lsass.exe) (Abgreifen von Anmeldeinformationen über das Subsystem zur lokalen Sicherheitsautorität von Windows kennzeichnen (lsass.exe)).|
|Process creation from PSExec and WMI commands (Prozesserstellung über die Befehle „PSExec“ und „WMI“)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert Prozesserstellungen über die Befehle „PSExec“ und „WMI“.|
|Untrusted and unsigned processes that run from USB (Nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden.|
|Executables that don’t meet a prevalence, age, or trusted list criteria (Ausführbare Dateien, die keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert das Ausführen ausführbarer Dateien, wenn sie keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen.|

#### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff

|              Name der Einstellung               |                                                              Einstellungsoptionen                                                              | Beschreibung |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Ordnerschutz (bereits implementiert) | Nicht konfiguriert, Aktivieren, Nur Überwachung (bereits implementiert)<br><br> <strong>Neu</strong><br>Blockieren der Änderung des Datenträgers, Überwachung der Änderung des Datenträgers |             |

Hiermit schützen Sie Dateien und Ordner vor unbefugten Änderungen durch bösartige Apps.<br><br>**Aktivieren:** Vermeiden Sie, dass nicht vertrauenswürdige Apps Dateien in geschützten Ordnern verändern oder löschen und in Datenträgersektoren schreiben.<br><br>
**Nur die Änderung des Datenträgers blockieren**:<br>Blockiert, dass nicht vertrauenswürdige Apps in Datenträgersektoren schreiben. Nicht vertrauenswürdige Apps können weiterhin Dateien in geschützten Ordnern verändern oder löschen.

## <a name="week-of-february-19-2018"></a>Woche vom 19. Februar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten <!-- 747685 -->

Intune unterstützt jetzt die Registrierung von Geräten mit bis zu 100 verschiedenen [Apple DEP-Konten](device-enrollment-program-enroll-ios.md) (Device Enrollment Program = Programm zur Geräteregistrierung) oder [Apple School Manager](apple-school-manager-set-up-ios.md)-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Anzeigen von Registrierungseinschränkungen pro Benutzer <!-- 1634444 eeready wnready -->
Auf dem Blatt **Problembehandlung** sehen Sie nun die [Registrierungseinschränkungen](enrollment-restrictions-set.md), die für jeden Benutzer gelten, wenn Sie in der Liste **Zuweisungen** auf **Registrierungseinschränkungen** klicken.

### <a name="device-management"></a>Geräteverwaltung
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Berichte zum Integritäts- und Bedrohungsstatus von Windows Defender <!--854704 -->

Ein grundlegendes Verständnis zur Integrität und zum Status von Windows Defender ist wichtig, damit Sie Windows-Computer verwalten können.  Mit diesem Update fügt Intune dem Status und der Integrität des Windows Defender-Agents neue Berichte und Aktionen hinzu. Wenn Sie einen Bericht zum Status des Rollups in der [Workload „Gerätekonformität“](compliance-policy-monitor.md) verwenden, werden Ihnen Geräte angezeigt, für die einer der folgenden Vorgänge erforderlich ist:
- Signaturupdate
- Neu starten
- Benutzereingriff
- vollständige Überprüfung
- andere Agent-Status, die einen Eingriff erfordern

In einem Drillthroughbericht für sämtliche Statuskategorien werden sowohl die einzelnen Computer aufgeführt, die überprüft werden sollten, als auch die, die als **Clean** (Bereinigt) eingestuft werden.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Neue Datenschutzeinstellungen für Gerätebeschränkungen <!--1308926 -->
Es sind jetzt [zwei neue Datenschutzeinstellungen](device-restrictions-windows-10.md#privacy) für Geräte verfügbar:
- **Benutzeraktivitäten veröffentlichen:** Legen Sie diese Einstellung auf **Blockieren** fest, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen in der Programmumschaltung zu vermeiden.
- **Nur lokale Aktivitäten:** Legen Sie diese Einstellungen auf **Blockieren** fest, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Neue Einstellungen für den Browser Microsoft Edge <!--1469166 -->
Für Geräte, auf denen Microsoft Edge installiert ist, sind [zwei neue Einstellungen](device-restrictions-windows-10.md#edge-browser) verfügbar: **Path to favorites file** (Pfad zu häufig verwendeten Dateien) und **Changes to Favorites** (Änderungen an Favoriten).

### <a name="app-management"></a>App-Verwaltung
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Protokollausnahmen für Anwendungen <!--1035509 -->

Sie können Ausnahmen für die Richtlinie zur Datenübertragung über die Verwaltung mobiler Anwendungen (MAM) mit Intune erstellen, um bestimmte nicht verwaltete Anwendungen zu öffnen. Diese Anwendungen müssen von der IT-Abteilung als vertrauenswürdig eingestuft werden. Entgegen der von Ihnen erstellten Ausnahmen ist die Datenübertragung immer noch auf Anwendungen beschränkt, die von Intune verwaltet werden, wenn Ihre Richtlinie zur Datenübertragung immer noch auf **managed apps only** (nur verwaltete Apps) festgelegt ist. Sie können die Einschränkungen mithilfe von Protokollen (unter iOS) oder Paketen (unter Android) erstellen.

Sie können beispielsweise das Webex-Paket als Ausnahme für die Richtlinie zur MAM-Datenübertragung hinzufügen. Dann ist es erlaubt, Webex-Links in einer verwalteten Outlook-E-Mail direkt über die Webex-Anwendung zu öffnen. In anderen nicht verwalteten Anwendungen ist die Datenübertragung dann aber immer noch eingeschränkt. Weitere Informationen finden Sie unter [Ausnahmen von der Datenübertragungsrichtlinie für Apps](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Mit Windows Information Protection (WIP) verschlüsselte Daten in Windows-Suchergebnissen <!-- 1469193 -->
Mit einer neuen Einstellung in der WIP-Richtlinie (Windows Information Protection) können Sie nun steuern, ob mit WIP verschlüsselte Daten in den Windows-Suchergebnissen enthalten sind. Legen Sie diese App-Schutzrichtlinienoption auf **Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten** in den **Erweiterten Einstellungen** der Windows Information Protection-Richtlinie fest. Die App-Schutzrichtlinie muss auf die *Windows 10*-Plattform und die App-Richtlinie **Registrierungsstatus** auf **Mit Registrierung** festgelegt werden. Weitere Informationen finden Sie unter [Der Windows Search-Indexerstellung die Suche nach verschlüsselten Elementen gestatten](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Konfigurieren einer mobilen MSI-App, die sich selbst aktualisiert <!-- 1740840 -->
Sie können eine bekannte mobile MSI-App konfigurieren, die sich selbst aktualisiert, um den Prozess der Versionsüberprüfung zu ignorieren. Diese Einstellung ist nützlich, um Racebedingungen zu vermeiden. Diese Art von Racebedingungen kann z.B. auftreten, wenn die App vom Entwickler automatisch aktualisiert wird, gleichzeitig aber auch von Intune ein Update ausgeführt wird. Beide könnten dann eine Version der App auf dem Windows-Client erzwingen, was einen Konflikt auslösen kann. Für diese automatisch aktualisierten MSI-Apps können Sie die Einstellung **App-Version ignorieren** auf dem Blatt **App-Informationen** konfigurieren. Wenn diese Einstellung auf **Ja** festgelegt wird, ignoriert Microsoft Intune die App-Version, die auf dem Windows-Client installiert ist.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Verwandte App-Lizenzen, die in Intune unterstützt werden <!-- 1864117 -->
Intune im App-Portal unterstützt nun verwandte App-Lizenzen als einzelne App-Elemente auf der Benutzeroberfläche. Außerdem werden alle offline lizenzierten Apps, die aus dem Microsoft Store für Unternehmen synchronisiert werden, in einem einzelnen App-Eintrag konsolidiert, und jegliche Bereitstellungsdetails aus den einzelnen Paketen werden in einen einzelnen Eintrag migriert. Wenn Sie verwandte App-Lizenzen im Azure-Portal abrufen möchten, klicken Sie im Azure-Portal auf der Seite **Mobile Apps** auf **App-Lizenzen**.

### <a name="device-configuration"></a>Gerätekonfiguration
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Dateierweiterungen für die automatische Verschlüsselung in Windows Informationen Protection (WIP) <!-- 1463582 -->
Mit einer Einstellung in Windows Informationen Protection (WIP) können Sie nun angeben, welche Dateierweiterungen automatisch verschlüsselt werden, wenn aus einer Server Message Block-Freigabe (SMB) innerhalb der Begrenzung des Unternehmens, wie in der WIP-Richtlinie definiert, kopiert wird.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Konfiguration der Einstellungen des Ressourcenkontos für Surface Hubs

Sie können nun Einstellungen des Ressourcenkontos für Surface Hubs über eine Remoteverbindung konfigurieren.

Das Ressourcenkonto wird von einem Surface Hub für die Authentifizierung bei Skype bzw. Exchange verwendet, um dessen Teilnahme an einer Besprechung zu ermöglichen.
Sie können ein eindeutiges Ressourcenkonto erstellen, damit der Surface Hub in der Besprechung als Konferenzraum angezeigt werden kann.
Dieses Ressourcenkonto können Sie dann beispielsweise **Konferenzraum B41/6233** nennen.

> [!NOTE]
> - Wenn Sie Felder leer lassen, setzen Sie bereits auf dem Gerät konfigurierte Attribute außer Kraft.
>
> - Die Eigenschaften des Ressourcenkontos auf dem Surface Hub können sich dynamisch verändern. Dies passiert z.B., wenn die Kennwortrotation aktiviert ist. Das bedeutet, dass es einige Zeit dauert, bis die Werte in der Azure-Konsole die aktuellen Gegebenheiten auf dem Gerät widerspiegeln.
>
>   Um ein grundlegendes Verständnis darüber zu erlangen, welche Optionen derzeit auf dem Surface Hub konfiguriert sind, können die Informationen zum Ressourcenkonto in der Hardwareinventur (die bereits alle sieben Tage durchgeführt wird) oder als schreibgeschützte Eigenschaften enthalten sein. Wenn Sie nach der Durchführung der Remoteaktion die Genauigkeit vergrößern möchten, können Sie den Status der Parameter unmittelbar nach der Ausführung dieser Aktion abrufen, um ein Update für das Konto bzw. die Parameter auf dem Surface Hub auszuführen.


##### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche


|Name der Einstellung  |Einstellungsoptionen  |Beschreibung  |
|---------|---------|---------|
|Execution of password-protected executable content from email (Ausführung der kennwortgeschützten ausführbaren Inhalte aus der E-Mail)|Blockieren, Überwachung, Nicht konfiguriert|Prevent password-protected executable files downloaded over email from running (Ausführung der von der E-Mail heruntergeladenen, kennwortgeschützten ausführbaren Inhalte verhindern).|
|Erweiterter Schutz vor Ransomware|Enabled, Audit, Not configured (Aktiviert, Überwachung, Nicht konfiguriert)|Verwendung eines offensiven Schutzes vor Ransomware.|
|Flag credential stealing from the Windows local security authority subsystem (Abgreifen von Anmeldeinformationen über das Subsystem der lokalen Sicherheitsautorität von Windows kennzeichnen)|Aktiviert, Überwachung, Nicht konfiguriert|Flag credential stealing from the Windows local security authority subsystem (lsass.exe) (Abgreifen von Anmeldeinformationen über das Subsystem zur lokalen Sicherheitsautorität von Windows kennzeichnen (lsass.exe)).|
|Process creation from PSExec and WMI commands (Prozesserstellung über die Befehle „PSExec“ und „WMI“)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert Prozesserstellungen über die Befehle „PSExec“ und „WMI“.|
|Untrusted and unsigned processes that run from USB (Nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden.|
|Executables that don’t meet a prevalence, age, or trusted list criteria (Ausführbare Dateien, die keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen)|Blockieren, Überwachung, Nicht konfiguriert|Blockiert das Ausführen ausführbarer Dateien, wenn sie keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen.|

##### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff

|              Name der Einstellung               |                                                              Einstellungsoptionen                                                              | Beschreibung |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Ordnerschutz (bereits implementiert) | Nicht konfiguriert, Aktivieren, Nur Überwachung (bereits implementiert)<br><br> <strong>Neu</strong><br>Blockieren der Änderung des Datenträgers, Überwachung der Änderung des Datenträgers |             |

Hiermit schützen Sie Dateien und Ordner vor unbefugten Änderungen durch bösartige Apps.<br><br>**Aktivieren:** Vermeiden Sie, dass nicht vertrauenswürdige Apps Dateien in geschützten Ordnern verändern oder löschen und in Datenträgersektoren schreiben.<br><br>
**Nur die Änderung des Datenträgers blockieren**:<br>Blockiert, dass nicht vertrauenswürdige Apps in Datenträgersektoren schreiben. Nicht vertrauenswürdige Apps können weiterhin Dateien in geschützten Ordnern verändern oder löschen.

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Ergänzungen zu den Konformitätsrichtlinien für die Systemsicherheitseinstellungen für Windows 10 und höher <!--1704133-->

Es sind nun Ergänzungen zu den Konformitätsrichtlinien für Windows 10 verfügbar. Z.B. sind eine Firewall und Windows Defender Antivirus erforderlich.


### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung
### <a name="intune-apps"></a>Intune-Apps
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Unterstützung für Offline-Apps aus dem Microsoft Store für Unternehmen <!--1222672-->
Offline-Apps, die Sie über den Microsoft Store für Unternehmen erworben haben, werden nun mit dem Azure-Portal synchronisiert. Sie können diese Apps für Geräte- oder Benutzergruppen bereitstellen. Offline-Apps werden durch Intune und nicht durch den Store installiert.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Verhindern, dass Benutzer Konten im Arbeitsprofil hinzufügen oder daraus entfernen <!-- 1728700 -->

Wenn Sie die Gmail-App in einem Android for Work-Profil bereitstellen, können Sie mit der Einstellung **Konten hinzufügen und entfernen** im Android for Work-Geräteeinschränkungsprofil verhindern, dass Benutzer Konten im Arbeitsprofil manuell hinzufügen oder daraus entfernen.

## <a name="week-of-february-5-2018"></a>Woche vom 5. Februar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Neue Option zur Benutzerauthentifizierung für die Apple-Massenregistrierung<!-- 747625 eeready -->

> [!NOTE]
> Neue Mandanten erkennen diese neue Option sofort. Für bereits vorhandene Mandanten wird dieses Feature im April eingeführt. Bis zur vollständigen Durchführung der Bereitstellung kann es sein, dass Sie noch keinen Zugriff auf diese neuen Features haben.

Mit Intune können Sie jetzt Geräte über folgende Registrierungsmethoden mit der Unternehmensportal-App authentifizieren:

- Apple-Programm zur Geräteregistrierung
- Apple School Manager
- Apple Configurator-Registrierung

Wenn Sie die Unternehmensportaloption verwenden, kann die mehrstufige Authentifizierung von Azure Active Directory erzwungen werden, ohne dass hierdurch diese Registrierungsmethoden blockiert werden.

Bei Verwendung der Unternehmensportaloption überspringt Intune die Benutzerauthentifizierung im iOS-Einrichtungsassistenten für die Registrierung mit der Benutzeraffinität. Das bedeutet, dass das Gerät zunächst als Gerät ohne Benutzer registriert wird und somit keine Konfigurationen oder Richtlinien von Benutzergruppen erhält. Es erhält nur Konfigurationen und Richtlinien für Gerätegruppen. Allerdings installiert Intune automatisch die Unternehmensportal-App auf dem Gerät. Der erste Benutzer, der die Unternehmensportal-App startet und sich bei dieser anmeldet, wird mit dem Gerät in Intune verbunden. An dieser Stelle erhält der Benutzer Konfigurationen und Richtlinien seiner Benutzergruppen. Die Benutzerzuordnung kann nur durch erneute Registrierung geändert werden.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune-Unterstützung für mehrere Apple DEP-/Apple School Manager-Konten <!-- 747685 eeready -->

Intune unterstützt jetzt die Registrierung von Geräten mit bis zu 100 verschiedenen Apple DEP-Konten (Device Enrollment Program = Programm zur Geräteregistrierung) oder Apple School Manager-Konten. Jedes Token kann separat für Registrierungsprofile und Geräte hochgeladen und verwaltet werden. Jedem hochgeladenen DEP-/School Manager-Token kann automatisch ein separates Registrierungsprofil zugewiesen werden. Wenn mehrere School Manager-Token hochgeladen werden, kann mit der Microsoft-Synchronisierung von Schul-/Unidaten jeweils nur ein Token freigegeben werden.

Nach der Migration funktionieren die Betaversionen der Graph-APIs und veröffentlichten Skripts zur Verwaltung von Apple DEP oder ASM über Graph nicht mehr. Neue Betaversionen der Graph-APIs sind in der Entwicklung und werden nach der Migration veröffentlicht.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Remotedrucken über ein sicheres Netzwerk <!-- 1709994  -->
Mobile drahtlose PrinterOn-Drucklösungen ermöglichen es Benutzern, jederzeit von einem beliebigen Ort aus Druckvorgänge remote über ein sicheres Netzwerk durchzuführen. PrinterOn wird in das Intune APP SDK für iOS und Android integriert. Über das Intune-Blatt **App-Schutzrichtlinien** in der Administratorkonsole können Sie gezielt die App-Schutzrichtlinien für diese App steuern. Endbenutzer können die App „PrinterOn for Microsoft“ über den Play Store oder iTunes herunterladen, um sie innerhalb ihres Intune-Ökosystems zu nutzen.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Unterstützung von Registrierungen durch das macOS-Unternehmensportal über den Geräteregistrierungs-Manager <!-- 1352411 -->

Benutzer können jetzt den Geräteregistrierungs-Manager verwenden, wenn sie sich im macOS-Unternehmensportal registrieren.

## <a name="week-of-january-29-2018"></a>Woche vom 29. Januar 2018

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Warnungen für abgelaufene und in Kürze ablaufende Token <!-- 1639263 -->
Auf der Übersichtsseite werden jetzt Warnungen für abgelaufene und in Kürze ablaufende Token angezeigt. Wenn Sie auf eine Warnung für ein einzelnes Token klicken, navigieren Sie zur Detailseite des Tokens.  Wenn Sie auf eine Warnung mit mehreren Token klicken, werden Sie zu einer Liste aller Token mit dem jeweiligen Status weitergeleitet. Administratoren sollten ihre Token vor dem Ablaufdatum verlängern.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Remoteunterstützung für den Befehl „Löschen“ für macOS-Geräte<!-- 1438084 -->

Administratoren können remote den Befehl „Löschen“ für macOS-Geräte auslösen.

> [!IMPORTANT]
> Der Löschbefehl kann nicht zurückgesetzt werden und sollte mit Bedacht angewendet werden.

Der Löschbefehl entfernt alle Daten von einem Gerät, einschließlich des Betriebssystems. Zusätzlich wird dabei auch das Gerät aus der Intune-Verwaltung entfernt. Es erfolgt keine Warnung gegenüber dem Benutzer und die Löschung erfolgt unmittelbar nach Ausgabe des Befehls.

Sie müssen eine 6-stellige PIN für die Wiederherstellung konfigurieren. Mit dieser PIN kann das gelöschte Gerät entsperrt werden, woraufhin die erneute Installation des Betriebssystems beginnt. Nach dem Starten des Löschvorgangs wird die PIN in einer Statusleiste auf dem Übersichtsblatt des Geräts in Intune angezeigt. Die PIN bleibt für die Dauer der Löschung bestehen. Nach der Löschung verschwindet das Gerät vollständig aus der Intune-Verwaltung. Dokumentieren Sie die Wiederherstellungs-PIN, damit sie jedem, der das Gerät wiederherstellt, zur Verfügung steht.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Widerrufen von Lizenzen für ein iOS Volume Purchase Program-Token <!-- 820870 -->
Sie können die Lizenz für alle iOS VPP-Apps (Volume Purchase Program) für ein bestimmtes VPP-Token widerrufen.

### <a name="app-management"></a>App-Verwaltung

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Widerrufen von Apps aus dem iOS Volume Purchase Program <!-- 820863 -->
Für ein bestimmtes Gerät, das mindestens eine iOS VPP-App (Volume Purchase Program) enthält, können Sie die zugehörige gerätebasierte App-Lizenz für das Gerät widerrufen. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Weitere Informationen finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Zuweisen von mobilen Office 365-Apps an iOS- und Android-Geräte mithilfe des integrierten App-Typs <!-- 1332318 -->
Der **integrierte** App-Typ erleichtert, Office 365-Apps für die iOS- und Android-Geräte, die Sie verwalten, zu erstellen und sie diesen zuzuweisen. Zu diesen Apps gehören Office 365-Apps wie Word, Excel, PowerPoint und OneDrive. Sie können bestimmte Apps dem App-Typen zuweisen und die Konfiguration der App-Informationen bearbeiten.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen<!-- 1406920 -->

Bei der App-Zuweisung und nach der Auswahl eines Zuweisungstyps können Sie die ein- und auszuschließenden Gruppen auswählen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Sie können eine Anwendungskonfigurationsrichtlinie Gruppen zuweisen, indem Sie Zuweisungen ein- und ausschließen  <!-- 1480316 -->

Sie können einer Gruppe von Benutzern und Geräten mithilfe einer Kombination von Ein- und Ausschlusszuweisungen eine Anwendungskonfigurationsrichtlinie zuweisen. Zuweisungen können entweder als eine benutzerdefinierte Auswahl von Gruppen oder virtuelle Gruppe ausgewählt werden. Eine virtuelle Gruppe kann entweder **Alle Benutzer**, **Alle Geräte** oder **Alle Benutzer und alle Geräte** einschließen.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Unterstützung für die Windows 10-Editionsupgraderichtlinie <!-- 903672(archived), 1119689 -->  
Durch das Erstellen einer Windows 10-Editionsupgraderichtlinie können Sie für Windows 10-Geräte ein Upgrade auf folgende Betriebssysteme durchführen: Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education und Windows 10 Professional Education N. Weitere Informationen zu Windows 10-Editionsupgrades finden Sie unter [Konfigurieren von Windows 10-Editionsupgrades](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Ausschließliche Verfügbarkeit von Richtlinien für den bedingten Zugriff für Intune über das Azure-Portal  <!-- 1737088 1634311 -->

Ab diesem Release müssen Sie Ihre Richtlinien für den bedingten Zugriff über das [Azure-Portal](https://portal.azure.com) unter **Azure Active Directory** > **Bedingter Zugriff** konfigurieren und verwalten. Der Einfachheit halber können Sie dieses Blatt auch über **Intune** > **Bedingter Zugriff** im Azure-Portal aufrufen.

#### <a name="updates-to-compliance-emails---1637547---"></a>Updates für Konformitäts-E-Mails<!--1637547 -->

Wenn eine E-Mail zur Meldung eines nicht konformen Geräts gesendet wird, werden Details über das nicht konforme Gerät einbezogen.


## <a name="week-of-january-22-2018"></a>Woche vom 22. Januar 2018

### <a name="intune-apps"></a>Intune-Apps

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Neue Funktionen für die Aktion „Lösung“ für Android-Geräte <!--1583480-->

Die Unternehmensportal-App für Android erweitert die Aktion „Lösung“ für **Geräteeinstellungen aktualisieren**, um [Verschlüsselungsprobleme bei Geräten](/intune-user-help/encrypt-your-device-android) zu lösen.

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Remote-Sperre in der Unternehmensportal-App für Windows 10 verfügbar <!--676506-->
Endbenutzer können Ihre Geräte jetzt über die Unternehmensportal-App für Windows 10 über eine Remoteverbindung sperren. Dies wird nicht für das lokale Gerät angezeigt, dass sie aktiv verwenden.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Einfachere Lösung von Konformitätsfehlern für die Unternehmensportal-App für Windows 10 <!--676546-->
Endbenutzer mit Windows-Geräten können in der Unternehmensportal-App auf den Grund der Nichtkonformität tippen. Wenn möglich werden sie direkt an den korrekten Ort in der Einstellungs-App geleitet, um das Problem zu beheben.

## <a name="week-of-december-11-2017"></a>Woche des 11. Dezember 2017

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Neue Einstellung für die automatische erneute Bereitstellung <!-- 1469168 -->
Die Einstellung **Automatische erneute Bereitstellung** ermöglicht es Benutzern mit Administratorrechten, alle Benutzerdaten und -einstellungen über **STRG+Windows+R** vom Sperrbildschirm des Geräts aus zu löschen. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung neu registriert. Diese Einstellung finden Sie unter „Windows 10“ > „Geräteeinschränkungen“ > „Allgemein“ > „Automatische erneute Bereitstellung“. Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10 in Intune](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Unterstützung für zusätzliche Quelleditionen in der Windows 10-Editionsupgraderichtlinie<!-- 903672,  1119689 -->
Sie können jetzt die Windows 10-Editionsupgraderichtlinie verwenden, um ein Upgrade von zusätzlichen Windows 10-Editionen (Windows 10 Pro, Windows 10 Pro for Education, Windows 10 Cloud, usw.) durchzuführen. Vor dieser Version waren die Upgradepfade für die unterstützten Editionen stärker eingeschränkt. Einzelheiten finden Sie unter [Konfigurieren von Windows 10-Editionsupgrades in Microsoft Intune](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Neue Einstellungen des WDSC-Gerätekonfigurationsprofils (Windows Defender Security Center) <!-- 1335507 -->

Unter dem Endpunktschutz namens **Windows Defender Security Center** fügt Intune einen neuen Abschnitt mit Einstellungen des Gerätekonfigurationsprofils hinzu. IT-Administratoren können konfigurieren, welche ///Komponenten der Windows Defender Security Center-App für Endbenutzer zugänglich sind. Wenn ein IT-Administrator eine Komponente in der Windows Defender Security Center-App ausblendet, werden Benachrichtigungen in Zusammenhang mit der ausgeblendeten Komponente nicht auf dem Gerät des Benutzers angezeigt.

Folgende Komponenten können von Administratoren aus den Einstellungen des Gerätekonfigurationsprofils von Windows Defender Security Center ausgeblendet werden:
- Viren- und Bedrohungsschutz
- Geräteleistung und -integrität
- Firewall- und Netzwerkschutz
- App- und Browsersteuerung
- Familienoptionen

IT-Administratoren können auch anpassen, welche Benutzer Benachrichtigungen empfangen können. Beispielsweise können Sie konfigurieren, ob Benutzer alle von sichtbaren Komponenten in WDSC generierten Benachrichtigungen oder nur kritische Benachrichtigungen erhalten. Zu nicht kritischen Benachrichtigungen gehören regelmäßige Zusammenfassungen von Windows Defender Antivirus-Aktivitäten und Benachrichtigungen bei Abschluss von Überprüfungen. Alle übrigen Benachrichtigungen gelten als kritisch. Darüber hinaus können Sie auch den Inhalt der Benachrichtigung anpassen. Beispielsweise können Sie die IT-Kontaktinformationen angeben, um sie in die Benachrichtigungen einzubetten, die auf den Geräten der Benutzer angezeigt werden.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Unterstützung für mehrere Connectors für die Behandlung von SCEP- und PFX-Zertifikaten <!-- 1361755 -->

Kunden, die den lokalen NDES-Connector zum Übermitteln von Zertifikaten an Geräte verwenden, können ab sofort mehrere Connectors in einem einzelnen Mandanten konfigurieren.

Diese neue Funktion unterstützt das folgende Szenario:

- **Hochverfügbarkeit**

Jeder NDES-Connector bezieht Zertifikatanforderungen mithilfe von Pull von Intune.  Wenn ein NDES-Connector offline geschaltet wird, kann der andere Connector weiterhin Anforderungen verarbeiten.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Möglichkeit zur Verwendung der Variable AAD_DEVICE_ID im benutzerdefinierten Antragstellernamen <!-- 1468599 -->

Wenn Sie ein SCEP-Zertifikatprofil in Intune erstellen, können Sie beim Erstellen des benutzerdefinierten Antragstellernamens ab sofort die Variable AAD_DEVICE_ID verwenden.   Wenn das Zertifikat mithilfe dieses SCEP-Profils angefordert wird, wird die Variable durch die AAD-Geräte-ID des Geräts ersetzt, das die Zertifikatsanforderung ausführt.


### <a name="device-management"></a>Geräteverwaltung

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Verwalten von über Jamf registrierten macOS-Geräten mit der Gerätekonformitäts-Engine von Intune <!-- 1592747 -->
Ab sofort können Sie mit Jamf Informationen über den macOS-Gerätezustand an Intune senden. Dort werden sie im Hinblick auf Konformität mit den Richtlinien ausgewertet, die in der Intune-Konsole definiert sind. Basierend auf dem Konformitätszustand des Geräts und anderen Bedingungen (z.B. Standort, Benutzerrisiko usw.) wird die Konformität für macOS-Geräte, die auf mit Azure AD verbundene Cloud- und lokale Anwendungen zugreifen (einschließlich Office 365) mithilfe des bedingten Zugriffs erzwungen. Erfahren Sie mehr über die [Einrichtung der Jamf-Integration](conditional-access-integrate-jamf.md) und [Erzwingung der Konformität für Jamf-verwaltete Geräte](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Neue iOS-Geräteaktion <!-- 1424701 -->

Sie können nun überwachte iOS 10.3-Geräte herunterfahren. Diese Aktion fährt das Gerät sofort und ohne Warnung für den Endbenutzer herunter. Die Aktion **Herunterfahren (nur überwacht)** finden Sie in den Geräteeigenschaften bei der Auswahl eines Geräts in der Workload **Gerät**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Verhindern von Änderungen an Datum/Uhrzeit bei Samsung KNOX-Geräten <!-- 1468103 -->

Wir haben ein neues Feature hinzugefügt, mit dem Sie Datums- und Zeitänderungen auf Samsung KNOX-Geräten blockieren können. Sie finden dieses unter **Gerätekonfigurationsprofile** > **Geräteeinschränkungen (Android)** > **Allgemein**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Unterstützung für Surface Hub-Ressourcenkonto <!-- 1566442  -->

Eine neue Geräteaktion wurde hinzugefügt, damit Administratoren das einem Surface Hub zugeordnete Ressourcenkonto definieren und aktualisieren können.

Das Ressourcenkonto wird von einem Surface Hub für die Authentifizierung bei Skype/Exchange verwendet, um seine Teilnahme an einer Besprechung zu ermöglichen. Sie können ein eindeutiges Ressourcenkonto erstellen, damit der Surface Hub in der Besprechung als Konferenzraum angezeigt wird. Beispielsweise kann das Ressourcenkonto als *Konferenzraum B41/6233* angezeigt werden. Das Ressourcenkonto (auch als Gerätekonto bezeichnet) für den Surface Hub muss in der Regel für den Standort des Konferenzraums konfiguriert werden, wenn andere Parameter des Ressourcenkontos geändert werden müssen.

Wenn Administratoren das Ressourcenkonto auf einem Gerät aktualisieren möchten, müssen sie die aktuellen Active Directory-/Azure Active Directory-Anmeldeinformationen angeben, die dem Gerät zugeordnet sind. Wenn die Kennwortrotation für das Gerät aktiviert ist, müssen Administratoren zu Azure Active Directory wechseln, um das Kennwort zu finden.

> [!NOTE]
> Alle Felder werden im Paket nach unten gesendet und überschreiben alle Felder, die zuvor konfiguriert wurden. Leere Felder überschreiben auch vorhandene Felder.

Administratoren können folgende Einstellungen konfigurieren:

- **Ressourcenkonto**
   - **Active Directory-Benutzer**

      Domänenname\Benutzername oder Benutzerprinzipalname (UPN): user@domainname.com

   - **Passwort**

- **Optionaler Ressourcenkontoparameter** (muss über das angegebene Ressourcenkonto festgelegt werden)

   - **Zeitraum für Kennwortrotation**

     Stellt sicher, dass das Kontokennwort aus Sicherheitsgründen jede Woche automatisch durch den Surface Hub aktualisiert wird. Um nach dem Aktivieren dieser Option Parameter zu konfigurieren, muss das Kennwort für das Konto in Azure Active Directory zuerst zurückgesetzt werden.

   - **SIP-Adresse (Session Initiation-Protokoll)**

     Wird nur verwendet, wenn die AutoErmittlung nicht möglich ist.

   - **E-Mail**

     E-Mail-Adresse des Geräte-/Ressourcenkontos.

   - **Exchange-Server**

     Nur erforderlich, wenn die AutoErmittlung nicht möglich ist.

   - **Kalendersynchronisierung**

     Gibt an, ob die Kalendersynchronisierung und andere Exchange-Serverdienste aktiviert sind. Beispiel: die Besprechungssynchronisierung.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installieren von Office-Apps auf macOS-Geräten <!-- 1494311 -->
Sie können nun Office-Apps auf macOS-Geräten installieren. Dieser neue App-Typ ermöglicht Ihnen die Installation von Word, Excel, PowerPoint, Outlook und OneNote. Diese Apps sind auch im Lieferumfang von Microsoft AutoUpdate (MAU) enthalten, um Ihre Apps sicher und auf dem neuesten Stand zu halten.

### <a name="app-management"></a>App-Verwaltung

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Löschen eines iOS Volume Purchase Program-Tokens <!-- 820879 -->
Sie können das iOS-VPP-Token (Volume Purchase Program) über die Konsole löschen. Dies kann erforderlich sein, wenn doppelte Instanzen eines VPP-Tokens vorliegen.

### <a name="intune-apps"></a>Intune-Apps


### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Eine neue Entitätssammlung namens „Aktueller Benutzer“ ist auf die Daten der momentan aktiven Benutzer beschränkt.<!-- 1667026 -->

Die Entitätssammlung **Benutzer** listet alle Benutzer von Azure Active Directory (Azure AD) mit zugewiesenen Lizenzen in Ihrem Unternehmen auf. Beispielsweise kann ein Benutzer in Intune hinzugefügt und dann im Verlauf des letzten Monats entfernt worden sein. Auch wenn dieser Benutzer zum Zeitpunkt der Berichterstellung nicht vorhanden ist, liegen Angaben zu Benutzer und Zustand in den Daten vor. Sie können einen Bericht erstellen, der die Dauer der Präsenz des Benutzers in Ihren Daten zeigt.

Im Gegensatz dazu enthält die neue Entitätssammlung **Aktueller Benutzer** nur Benutzer, die nicht entfernt wurden. Die Entitätssammlung **Aktueller Benutzer** enthält nur die derzeit aktiven Benutzer. Informationen zur Entitätssammlung **Aktueller Benutzer** finden Sie unter [Referenz für die Entität „Aktueller Benutzer“](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>Aktualisierte Graph-APIs<!-- 1736360 -->

In diesem Release haben wir einige der Graph-APIs für Intune aktualisiert, die sich in der Betaphase befinden. Weitere Informationen finden Sie im monatlichen [Graph-API-Änderungsprotokoll](https://developer.microsoft.com/graph/docs/concepts/changelog).

## <a name="week-of-december-4-2017"></a>Woche des 4. Dezember 2017

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune unterstützt WIP-abgelehnte Apps (Windows Information Protection) <!-- 1479103 -->
Sie können abgelehnte Apps in Intune festlegen. Wenn eine App abgelehnt wird, wird ihr der Zugriff auf Unternehmensinformationen verweigert. Sie ist also genau das Gegenteil einer zugelassenen App. Weitere Informationen finden Sie unter [AppLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection).


## <a name="week-of-november-27-2017"></a>Woche vom 27. November 2017

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Behandlung von Problemen bei der Registrierung <!-- 746324 -->

Im Arbeitsbereich **Problembehandlung** werden nun Probleme der Benutzer bei der Registrierung angezeigt. Die Details zum Problem und die vorgeschlagenen Abhilfemaßnahmen können Administratoren und Helpdeskmitarbeiter bei der Behandlung von Problemen unterstützen. Bestimmte Probleme bei der Registrierung werden nicht erfasst, und für einige Fehler liegen möglicherweise keine Wiederherstellungsvorschläge vor.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Gruppen zugeordnete Registrierungseinschränkungen <!-- 747598 -->

Als Intune-Administrator können Sie nun [benutzerdefinierte Registrierungsbeschränkungen für Gerätetypen und -limits für Benutzergruppen erstellen](enrollment-restrictions-set.md).

Im Intune Azure-Portal können Sie bis zu 25 Instanzen für jeden Beschränkungstyp erstellen, die Sie anschließend Benutzergruppen zuordnen können. Gruppen zugeordnete Beschränkungen setzen die Standardbeschränkungen außer Kraft.

Sämtliche Instanzen eines Beschränkungstypen werden in einer Liste mit einer strengen Reihenfolge verwaltet. Diese Reihenfolge definiert einen Prioritätswert für die Lösung von Konflikten. Ein Benutzer, der von mehr als einer Beschränkungsinstanz betroffen ist, wird nur von der Instanz mit dem höchsten Prioritätswert eingeschränkt. Sie können die Priorität einer vorhandenen Instanz ändern, indem Sie sie an eine andere Stelle in der Liste ziehen.

Diese Funktion wird mit der Migration von Android for Work-Einstellungen aus dem Android for Work-Registrierungsmenü in das Registrierungsmenü freigegeben. Da diese Migration einige Tage in Anspruch nehmen kann, wird Ihr Konto möglicherweise auf andere Teile des Releases im November aktualisiert, bevor die Gruppenzuweisung für Registrierungsbeschränkungen aktiviert ist.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Unterstützung von mehreren Konnektoren für den Registrierungsdienst für Netzwerkgeräte <!-- 1528104 -->

Über den Registrierungsdienst für Netzwerkgeräte (Network Device Enrollment Service NDES) können Mobilgeräte, die ohne Domänen-Anmeldeinformationen ausgeführt werden, Zertifikate auf Basis des Simple Certificate Enrollment-Protokolls (SCEP) abrufen.
Mit diesem Update werden mehrere NDES-Connectors unterstützt.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Verwalten von Android for Work-Geräten unabhängig von Android-Geräten <!-- 1490731 EEready-->

Intune unterstützt das Verwalten von Registrierungen von Android for Work-Geräten unabhängig von der Android-Plattform. Diese Einstellungen werden unter **Geräteregistrierung** > **Registrierungsbeschränkungen** > **Gerätetypbeschränkungen** verwaltet. (Zuvor waren sie unter **Geräteregistrierung** > **Android for Work-Registrierung** > **Android for Work-Registrierungseinstellungen** zu finden.)

Standardmäßig ändern sich die Android for Work-Geräteeinstellungen gegenüber Ihren Android-Geräteeinstellungen nicht. Dies ändert sich allerdings, nachdem Sie ihre Android for Work-Einstellungen geändert haben.

Wenn Sie die private Android for Work-Registrierung blockieren, können sich nur unternehmenseigene Android-Geräte als Android for Work-Geräte registrieren.

Ziehen Sie Folgendes in Betracht, wenn Sie mit den neuen Einstellungen arbeiten:

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Wenn Sie die Android for Work-Registrierung zuvor noch nie integriert haben

Die neue Android for Work Plattform wird in den Standardgerätetypbeschränkungen blockiert. Nachdem Sie die Funktion integriert haben, können Sie zulassen, dass sich Geräte mit Android for Work registrieren. Ändern Sie dafür die Standardeinstellungen, oder erstellen Sie eine neue Gerätetypbeschränkung, um die Standardgerätetypbeschränkungen zu ersetzen.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Wenn Sie die Android for Work-Registrierung bereits integriert haben

Wenn Sie zuvor bereits eine Integration vorgenommen haben, hängt Ihre Situation von den von Ihnen ausgewählten Einstellungen ab:

| Einstellung | Android for Work-Status in den Standardgerätetypbeschränkungen | Hinweise |
| --- | --- | --- |
| **Alle Geräte als Android-Geräte verwalten** | Gesperrt | Alle Android-Geräte müssen sich ohne Android for Work registrieren. |
| **Unterstützte Geräte als Android for Work-Geräte verwalten** | Zugelassen | Alle Android-Geräte, die Android for Work unterstützen, müssen sich mit Android for Work registrieren. |
| **Nur unterstützte Geräte für Benutzer in diesen Gruppen als Android for Work-Geräte verwalten** | Gesperrt | Eine separate Richtlinie für Gerätetypbeschränkungen wurde erstellt, um die Standareinstellungen außer Kraft zu setzen. Diese Richtlinie definiert die Gruppen, für die Sie zuvor die Android for Work-Registrierung zugelassen haben. Benutzer der ausgewählten Gruppen dürfen ihre Android for Work-Geräte weiterhin registrieren. Alle anderen Benutzer können sich nicht mit Android for Work registrieren. |

In beiden Fällen wird die von Ihnen vorgesehene Regulierung beibehalten. Von Ihrer Seite ist kein weiterer Vorgang erforderlich, um die globalen oder gruppenbedingten Zulassungen von Android for Work in Ihrer Umgebung zu verwalten.

### <a name="app-management"></a>App-Verwaltung

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>App-Installationsbericht mit dem Status „Installation steht aus“ aktualisiert <!-- 1249446 -->  

Der Bericht über den **Installationsstatus der App**, der in jeder App über die **App**-Liste in der Workload **Mobile Apps** verfügbar ist, enthält nun für Benutzer und Geräte die Angabe **Installation steht aus** samt Anzahl.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>App-Bestand-API zur Bedrohungserkennung auf Mobilgeräten unter iOS 11 <!-- 1391759 -->

Intune erfasst sowohl von privaten als auch von unternehmenseigenen Geräten Informationen zum App-Bestand und stellt diese für Anbieter von Bedrohungserkennung auf Mobilgeräten (Mobile Thread Detection, MTD) wie Lookout for Work zur Verfügung. Sie können Informationen zum App-Bestand auf iOS 11-Geräten (oder höher) erfassen.

**App-Bestand**  
Die Bestände von sowohl unternehmenseigenen als auch privaten iOS 11-Geräten (oder höher) werden an Ihren MTD-Dienstanbieter übermittelt. Die Daten in den App-Beständen umfassen:

 - App-ID
 - App-Version
 - Kurzversion der App
 - App-Name
 - Größe des App-Pakets
 - Dynamische Größe der App
 - App wird geprüft oder nicht
 - App wird verwaltet oder nicht


### <a name="device-management"></a>Geräteverwaltung

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Migrieren von Benutzern und Geräten in eigenständiges Intune <!-- 1463747 wnready -->
Der Prozess und die Tools zum Verschieben von Benutzern und deren zugehörigen Geräten aus hybridem MDM nach Intune im Azure-Portal sind jetzt verfügbar. Sie können daher jetzt folgende Aufgaben durchführen:
- Sie können Richtlinien und Profile aus der Configuration Manager-Konsole nach Intune im Azure-Portal verschieben.
- Sie können einen Teil der Benutzer nach Intune im Azure-Portal verschieben und den anderen Teil im hybriden MDM belassen.
- Sie können Geräte zu Intune im Azure-Portal migrieren, ohne erneut eine Registrierung durchführen zu müssen.

Ausführlichere Angaben finden Sie unter [Migrieren von Benutzern und Geräten in einer MDM-Hybridlösung zu eigenständigem Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Hochverfügbarkeit der Unterstützung von lokalem Exchange-Connector <!-- 676614 -->
Nachdem der Exchange-Connector mit dem angegebenen CAS eine Verbindung mit Exchange hergestellt hat, weist der Connector nun die Möglichkeit zur Ermittlung anderer CAS auf. Wenn der primäre CAS nicht mehr verfügbar ist, wird für den Connector ggf. ein Failover auf einen anderen CAS durchgeführt, bis der primäre CAS verfügbar wird. Einzelheiten finden Sie unter [Hochverfügbarkeitsunterstützung für lokalen Exchange Connector](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Remote-Neustart von iOS-Geräten (nur überwacht) <!-- 1424595 -->

Sie können nun bei einem überwachten iOS 10.3-Gerät (und höher) über eine Geräteaktion einen Neustart auslösen. Weitere Informationen zum Geräteneustart finden Sie unter [Remotely restart devices with Intune (Remote-Neustart von Geräten mit Intune)](device-restart.md).

> [!Note]
> Für diesen Befehl wird ein überwachtes Gerät und das Zugriffsrecht **Gerätesperre** benötigt. Das Gerät wird sofort neu gestartet. Kennungsgeschützte iOS-Geräte verbinden Sie nach dem Neustart nicht wieder mit dem WLAN-Netzwerk und können unter Umständen nicht mehr mit dem Server kommunizieren.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>Unterstützen des einmaligen Anmeldens (Single Sign-On, SSO) für iOS <!-- 1333645 -->  

Sie können SSO für iOS-Benutzer verwenden. Die iOS-Apps, die so programmiert wurden, dass sie nach Benutzeranmeldeinformationen in der Payload für einmaliges Anmelden suchen, sind mit diesem Payload-Konfigurationsupdate weiterhin funktionsfähig. Sie können auch den UPN und die Intune-Geräte-ID verwenden, um den Prinzipalnamen und den Bereich zu identifizieren. Ausführlichere Angaben finden Sie unter [Configure Intune for iOS device single sign-on (Konfigurieren von Intune für SSO von iOS-Geräten)](sso-ios.md).

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Hinzufügen der Funktion „Find my iPhone“ („Mein iPhone finden“) für private Geräte <!--1427287-->
Ihnen wird jetzt angezeigt, ob für iOS-Geräte eine Aktivierungssperre aktiviert ist. Diese Funktion konnten Sie zuvor im klassischen Intune-Portal finden.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Remote-Sperren von verwalteten macOS-Geräten durch Intune <!-- 1437691 -->

Sie können ein verlorenes macOS-Gerät sperren und eine sechsstellige Wiederherstellungs-PIN festlegen. Wenn das Gerät gesperrt ist, wird im Blatt **Device overview** (Geräteübersicht) die PIN solange angezeigt, bis eine andere Geräteaktion gesendet wurde.

Weitere Informationen finden Sie unter [Remotely lock managed devices with Intune (Remote-Sperren von verwalteten Geräten durch Intune)](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Unterstützen von neuen SCEP-Profildetails <!-- 1559808 -->

Administratoren können nun zusätzliche Einstellungen festlegen, wenn sie ein SCEP-Profil auf Windows-, iOS-, macOS- und Android-Plattformen erstellen.  Administratoren können die IMEI, die Seriennummer oder allgemeine Namen, einschließlich der E-Mail-Adresse im Format des Antragstellernamens, festlegen.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Beibehalten von Daten während einer Zurücksetzung auf Werkseinstellungen <!--1588489 -->
Beim Zurücksetzen der Windows 10-Version 1709 und höher auf die Werkseinstellungen steht eine neue Funktion zur Verfügung. Administratoren können angeben, ob die Geräteregistrierung und andere bereitgestellte Daten während einer Zurücksetzung auf Werkseinstellungen auf einem Gerät erhalten bleiben sollen.

Die folgenden Daten bleiben während der Zurücksetzung auf Werkseinstellungen erhalten:
- Dem Gerät zugeordnete Benutzerkonten
- Status des Computers (Domänenbeitritt, mit Azure Active Directory verknüpft)
- MDM-Registrierung
- Über OEM installierte Apps (Store- und Win32-Apps)
- Benutzerprofil
- Benutzerdaten außerhalb des Benutzerprofils
- Automatische Anmeldung des Benutzers

Die folgenden Daten bleiben nicht erhalten:
- Benutzerdateien
- Vom Benutzer installierte Apps (Store- und Win32-Apps)
- Geräteeinstellungen, die nicht dem Standard entsprechen

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Zuweisungen des Windows 10-Updaterings werden angezeigt <!-- 1621837 -->
Wenn Sie für den angezeigten Benutzer **Probleme behandeln**, werden Ihnen sämtliche Zuweisungen des Windows 10-Updaterings angezeigt.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Häufigkeitseinstellungen von Windows Defender Advanced Threat Protection-Berichten <!-- 1455974  -->
Der Dienst Windows Defender Advanced Threat Protection (WDETP) ermöglicht es Administratoren, zu verwalten, wie häufig für verwaltete Geräte Berichte erstellt werden sollen. Mit der neuen Option **Häufigkeit von Telemetrieberichten erhöhen** erfasst WDETP häufiger Daten und prüft Risiken. Die Standardeinstellung für die Berichterstellung optimiert Geschwindigkeit und Leistung. Für Geräte, die ein hohes Risiko darstellen,kann es sehr nützlich sein, häufiger Berichte zu erstellen. Diese Einstellung finden Sie in den **Gerätekonfigurationen** in dem Profil **Windows Defender ATP**.

#### <a name="audit-updates----1412961---"></a>Überwachungsupdates <!-- 1412961 -->  
Die Intune-Überwachung stellt einen Datensatz mit Änderungsvorgängen im Zusammenhang mit Intune zur Verfügung.  Alle Vorgänge zum Erstellen, Aktualisieren und Löschen sowie Remoteaufgaben werden erfasst und für ein Jahr gespeichert.  Im Azure-Portal werden die Überwachungsdaten der letzten 30 Tage filterbar in sämtlichen Workloads dargestellt.  Eine dazugehörige Graph-API ermöglicht den Abruf von Überwachungsdaten, die über ein Jahr hinweg gespeichert wurden.

Die Überwachungsfunktion finden Sie unter der Gruppe **MONITOR**. Für jede Workload gibt es das Menüelement **Überwachungsprotokolle**.




## <a name="week-of-november-20-2017"></a>Woche vom 20. November 2017

### <a name="app-management"></a>App-Verwaltung

#### <a name="google-play-protect-support-on-android----908720---"></a>Unterstützung für Google Play Protect unter Android <!-- 908720 -->

Mit der Version Android Oreo führt Google eine Suite von Sicherheitsfunktionen namens „Google Play Protect“ ein, mit denen Benutzer und Organisationen Apps und Android-Images sicher ausführen können. Intune unterstützt jetzt Google Play Protect-Features, einschließlich des SafetyNet-Remotenachweises. Administratoren können Konformitätsrichtlinienanforderungen festlegen, für die Google Play Protect konfiguriert sein und sich in einem fehlerfreien Zustand befinden muss.
Für die Verwendung der Einstellung **SafetyNet-Gerätenachweis** muss das Gerät eine Verbindung mit einem Google-Dienst herstellen, damit sichergestellt ist, dass sich das Gerät in einem fehlerfreien Zustand befindet und es nicht beeinträchtigt ist. Administratoren können zudem eine Konfigurationsprofileinstellung für Android for Work festlegen, um zu erfordern, dass installierte Apps von Google Play-Diensten überprüft werden. Wenn ein Gerät nicht mit den Google Play Protect-Anforderungen konform ist, können Benutzer durch den bedingten Zugriff daran gehindert werden, auf Unternehmensressourcen zuzugreifen.

- Siehe [Informationen zum Erstellen einer Gerätekonformitätsrichtlinie zum Aktivieren von Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Zulässige Textprotokolle verwalteter Apps <!-- 1414050  -->

Apps, die über das Intune App SDK verwaltet werden, können SMS-Nachrichten versenden.

## <a name="week-of-november-13-2017"></a>Woche vom 13. November 2017

### <a name="intune-apps"></a>Intune-Apps
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>Die Unternehmensportal-App für macOS ist verfügbar <!--1541700-->
Das Intune-Unternehmensportal unter macOS besitzt eine aktualisierte Benutzeroberfläche, die für die saubere Darstellung aller Informationen und Konformitätsbenachrichtigungen optimiert wurde, die Ihre Benutzer für alle registrierten Geräte benötigen. Nachdem das Intune-Unternehmensportal auf einem Gerät bereitgestellt wurde, stellt Microsoft AutoUpdate für macOS Updates für sie bereit. Sie können das neue Intune-Unternehmensportal für macOS herunterladen, indem Sie sich von einem macOS-Gerät aus bei der Website des Intune-Unternehmensportals anmelden.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner ist jetzt Bestandteil der MAM-Liste (Mobile App-Verwaltung) genehmigter Apps <!-- 1248473 -->
Die Microsoft Planner-App für iOS und Android gehört jetzt zu den genehmigten Apps für die mobile App-Verwaltung (MAM). Im Azure-Portal kann die App über das Blatt „Intune-App-Schutz“ für alle Mandanten konfiguriert werden.
- Weitere Informationen zur [MAM-Liste genehmigter Apps](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Aktualisierungshäufigkeit der Pro-App-VPN-Anforderung auf iOS-Geräten <!-- 1547061 -->  
Administratoren können jetzt Pro-App-VPN-Anforderungen für Apps auf iOS-Geräten entfernen. Betroffene Geräte werden nach ihrem nächsten Intune-Check-In aktualisiert, das in der Regel innerhalb von 15 Minuten erfolgt.  

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Unterstützung für das System Center Operations Manager-Management Pack für den Exchange-Connector <!-- 885457 -->
Mit dem SCOM-Management Pack (System Center Operations Manager) für den Exchange-Connector können Sie jetzt die Exchange-Connector-Protokolle analysieren. Dieses Feature bietet Ihnen verschiedene Möglichkeiten zur Überwachung des Diensts bei der Problembehandlung.

## <a name="week-of-november-6-2017"></a>Woche vom 6. November 2017

### <a name="device-enrollment"></a>Geräteregistrierung
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Co-Verwaltung für Windows 10-Geräte <!-- 1243445 -->
Bei der Co-Verwaltung handelt es sich um eine Lösung, die eine Brücke von der herkömmlichen zur modernen Verwaltung schlägt und Ihnen die Möglichkeit bietet, die Umstellung schrittweise durchzuführen. Bei der Co-Verwaltung handelt es sich im Grunde um eine Lösung, mit der Windows 10-Geräte gleichzeitig mit Configuration Manager und Intune verwaltet werden können. Außerdem können sie in Active Directory (AD) und Azure Active Directory (Azure AD) eingebunden werden.  Diese Konfiguration bietet Ihnen eine Möglichkeit, um nach und nach den Bedürfnissen Ihrer Organisation entsprechend eine Modernisierung durchzuführen, wenn Sie nicht alles auf einmal durchführen können.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Einschränkung der Windows-Registrierung nach Betriebssystemversion <!-- 245498 -->
Als Intune-Administrator können Sie jetzt eine Mindest- und eine Höchstversion von Windows 10 für Geräteregistrierungen angeben. Sie können diese Einschränkungen auf dem Blatt **Plattformkonfigurationen** festlegen.

Intune unterstützt auch weiterhin die Registrierung von Windows 8.1-PCs und Smartphones. Allerdings können nur für Windows 10-Versionen Grenzwerte für die Mindest- und Höchstversion festgelegt werden. Um die Registrierung von 8.1-Geräten zu erlauben, lassen Sie die Angabe für die Mindestversion leer.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Warnungen für nicht zugewiesene Windows AutoPilot-Geräte <!-- 1631236 -->
Auf der Seite **Microsoft Intune** > **Geräteregistrierung** > **Übersicht** steht eine neue Warnung für nicht zugewiesene Windows AutoPilot-Geräte zur Verfügung. Diese Warnung zeigt, wie vielen Geräten aus dem AutoPilot-Programm keine AutoPilot-Bereitstellungsprofile zugewiesen wurden. Verwenden Sie die Informationen aus der Warnung, um Profile zu erstellen und sie den nicht zugeordneten Geräten zuzuweisen. Wenn Sie auf die Warnung klicken, sehen Sie die vollständige Liste der Windows AutoPilot-Geräte zusammen mit detaillierten Informationen. Weitere Informationen finden Sie unter [Enroll Windows devices using Windows AutoPilot Deployment Program (Registrieren von Windows-Geräten mithilfe des Windows AutoPilot Deployment-Programms)](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Geräteverwaltung

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Schaltfläche „Aktualisieren“ für Geräteliste    <!-- 1333581 -->
Da die Geräteliste nicht automatisch aktualisiert wird, können Sie die neue Schaltfläche „Aktualisieren“ verwenden, um die in der Liste angezeigten Geräte zu aktualisieren.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Unterstützung für die Symantec-Cloudzertifizierungsstelle (ZS) <!-- 1333638 -->    
Intune unterstützt nun die Symantec-Cloud-ZS, die es dem Intune Certificate Connector ermöglicht, PKCS-Zertifikate von der Symantec-Cloud-ZS für von Intune verwaltete Geräte auszustellen. Wenn Sie den Intune Certificate Connector bereits mit der Microsoft-Zertifizierungsstelle (ZS) verwenden, können Sie das vorhandene Intune Certificate Connector-Setup nutzen, um die Unterstützung für die Symantec-ZS hinzuzufügen.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Neue Elemente im Geräteinventar   <!--1404455 -->
Die folgenden neuen Elemente sind jetzt im [Inventar der registrierten Geräte](device-inventory.md) enthalten:

- WLAN-MAC-Adresse
- Gesamtmenge des Speicherplatzes
- Gesamtmenge des freien Speicherplatzes
- MEID
- Netzbetreiber des Abonnenten


### <a name="app-management"></a>App-Verwaltung
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Festlegen des Zugriffs für Apps durch einen mindestens erforderlichen Android-Sicherheitspatch auf dem Gerät <!-- 1278463 -->   
Ein Administrator kann den mindestens erforderlichen Android-Sicherheitspatch definieren, der auf dem Gerät installiert sein muss, um Zugriff auf eine verwaltete Anwendung mit einem verwalteten Konto zu erhalten.

> [!Note]  
> Dieses Feature schränkt nur Sicherheitspatches ein, die von Google für Android 6.0+-Geräte veröffentlicht wurden.

#### <a name="app-conditional-launch-support----1193313---"></a>App-bedingte Startunterstützung <!-- 1193313 -->
IT-Administratoren können nun eine Anforderung über das Azure-Verwaltungsportal festlegen, um eine Kennung statt einer numerischen PIN über die mobile App-Verwaltung (Mobile App Management, MAM) zu erzwingen, wenn die Anwendung gestartet wird. Wenn dies konfiguriert ist, muss der Benutzer eine Kennung festlegen und verwenden, wenn er dazu aufgefordert wird, bevor der Zugriff auf MAM-aktivierte Apps gewährt wird. Eine Kennung ist als numerische PIN mit mindestens einem Sonderzeichen oder einem Groß-/Kleinbuchstaben definiert. In dieser Version von Intune wird dieses Feature **nur unter iOS** aktiviert. Intune unterstützt Kennungen auf ähnliche Weise wie numerische PINs, nämlich indem eine Mindestlänge festgelegt wird, sodass wiederholte Zeichen und Sequenzen möglich sind. Für dieses Feature ist die Beteiligung von Anwendungen erforderlich (d.h. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK in den Code für dieses Feature anstelle der Kennungseinstellungen zu integrieren und für die Zielanwendungen zu erzwingen.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>App-Versionsnummer für branchenspezifische Apps im Statusbericht der Geräteinstallation <!-- 1233999 -->
Ab dieser Version zeigt der Statusbericht der Geräteinstallation die App-Versionsnummern der branchenspezifischen Apps für iOS und Android an. Sie können diese Informationen verwenden, um Probleme mit Ihren Apps zu beheben oder um Geräte zu suchen, auf denen veraltete App-Versionen ausgeführt werden.


### <a name="device-configuration"></a>Gerätekonfiguration
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Administratoren können nun die Firewall-Einstellungen auf einem Gerät mithilfe eines Profils für die Gerätekonfiguration konfigurieren <!-- 951708 -->   
Administratoren können die Firewall für Geräte einschalten sowie verschiedene Protokolle für Domänen sowie private und öffentliche Netzwerke konfigurieren.  Diese Firewall-Einstellungen können im Profil „Endpoint Protection“ gefunden werden.

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard unterstützt den Schutz von Geräten vor nicht vertrauenswürdigen Websites gemäß den Definitionen Ihrer Organisation <!-- 958257 -->   
Administratoren können Websites mithilfe eines Windows Information Protection-Workflows oder des neuen Profils „Netzwerkgrenze“ in den Gerätekonfigurationen als „trusted“ (vertrauenswürdig) oder „corporate“ (geschäftlich) definieren. Alle Websites, die mit Microsoft Edge angezeigt werden und nicht in der vertrauenswürdigen Netzwerkgrenze eines Windows 10-Geräts (64 Bit) aufgelistet werden, werden stattdessen in einem Browser innerhalb eines virtuellen Hyper-V-Computers geöffnet.

Application Guard kann unter den Profilen für die Gerätekonfiguration im Profil „Endpoint Protection“ gefunden werden. Von dort aus können Administratoren die Interaktionen zwischen dem virtualisierten Browser und dem Hostcomputer, vertrauenswürdigen und nicht vertrauenswürdigen Websites sowie das Speichern von Daten konfigurieren, die im virtualisierten Browser generiert werden. Es muss zunächst eine Netzwerkgrenze konfiguriert werden, um Application Guard auf einem Gerät zu verwenden. Es ist wichtig, nur eine Netzwerkgrenze für ein Gerät zu definieren.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Control unter Windows 10 Enterprise bietet einen Modus, um nur autorisierten Apps zu vertrauen <!-- 1031096 -->    
Durch Tausende von neuen, schädlichen Dateien, die jeden Tag erstellt werden, bietet das Verwenden von signaturbasierten Antivirenerkennungen zum Bekämpfen von Schadsoftware keine angemessene Verteidigung mehr gegen neue Angriffe. Indem Sie Windows Defender Application Control unter Windows 10 Enterprise verwenden, können Sie die Gerätekonfiguration von einem Modus, in dem Apps als vertrauenswürdig gelten, wenn Sie nicht von einem Antivirenprogramm oder einer anderen Sicherheitslösung blockiert werden, zu einem Modus ändern, in dem das Betriebssystem nur Apps vertraut, die von Ihrem Unternehmen autorisiert wurden. Sie weisen den Apps die Vertrauensstellung in Windows Defender Application Control zu.

Mithilfe von Intune können Sie die Anwendungssteuerungsrichtlinien entweder für den Modus „Nur überwachen“ oder „Erzwingen“ konfigurieren. Apps werden nicht blockiert, wenn diese im Modus „audit only“ (Nur überwachen) ausgeführt werden. Der Modus „Nur überwachen“ protokolliert alle Ereignisse in lokalen Clientprotokollen. Sie können ebenfalls konfigurieren, ob nur Windows-Komponenten und Microsoft Store-Apps ausgeführt werden können, oder ob zusätzliche Apps mit gutem Ruf gemäß der Definition von Intelligent Security Graph ausgeführt werden können.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender Exploit Guard stellt eine neue Reihe von Funktionen zur Abwendung von Eingriffen für Windows 10 dar <!-- 1063615 -->   
Window Defender Exploit Guard enthält benutzerdefinierte Regeln, um die Angreifbarkeit von Anwendungen zu reduzieren, verhindert Bedrohungen durch Makros und Skripts, blockiert automatisch Netzwerkverbindungen zu IP-Adressen mit schlechtem Ruf und kann Daten vor Ransomware und unbekannten Bedrohungen schützen. Windows Defender Exploit Guard besteht aus folgenden Komponenten:

- Die **Verringerung der Angriffsfläche (Attack Surface Reduction, ASR)** stellt Regeln bereit, die es Ihnen ermöglichen, Bedrohungen durch Makros, Skripts und E-Mails zu verhindern.
- Der **gesteuerte Ordnerzugriff** blockiert automatisch den Zugriff auf Inhalte in geschützten Ordnern.
- Der **Netzwerkfilter** blockiert ausgehende Verbindungen von jeder App mit IPs/Domänen mit schlechtem Ruf.
- Der **Exploit-Schutz** stellt Einschränkungen für den Arbeitsspeicher, die Ablaufsteuerung und Richtlinien bereit, die für den Schutz einer Anwendung vor Exploits verwendet werden können.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte <!-- 790537 -->

Durch die Verwaltungserweiterung von Intune können Sie PowerShell-Skripts in Intune für die Ausführung auf Windows 10-Geräten hochladen. Die Erweiterungen ergänzen Funktionen für die mobile Geräteverwaltung (mobile device management, MDM) von Windows 10 und erleichtern Ihnen die Umstellung auf eine moderne Verwaltung. Details finden Sie unter [Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Neue Einstellungen für Geräteeinschränkungen für Windows 10 <!-- 1308850 -->
-    Messaging (nur mobil): Deaktivieren von Test- oder MMS-Nachrichten
-    Kennwort: Einstellungen zum Aktivieren von FIPS und der Verwendung von sekundären Windows Hello-Geräten für die Authentifizierung 
-    Anzeige: Einstellungen zum Aktivieren oder Deaktivieren der GDI-Skalierung für ältere Apps

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Geräteeinschränkungen beim Windows 10-Kioskmodus <!-- 1308872 -->   
Sie können die Benutzer von Windows 10-Geräten auf den Kioskmodus beschränken, der diese auf eine Reihe von vordefinierten Apps einschränkt.  Erstellen Sie dazu ein Einschränkungsprofil für Windows 10-Geräte und legen Sie die Kioskeinstellung fest.

Der Kioskmodus unterstützt zwei Modi: **einzelne App** (ermöglicht dem Benutzer nur das Ausführen einer einzigen App) oder **mehrere Apps** (ermöglicht den Zugriff auf verschiedene Apps).  Sie definieren das Benutzerkonto und den Gerätenamen, der die unterstützten Apps definiert.  Wenn der Benutzer angemeldet ist, ist dieser auf die definierten Apps beschränkt.  Weitere Informationen finden Sie unter [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Der Kioskmodus erfordert Folgendes:

- Intune muss die MDM-Autorität sein.
- Die Apps müssen bereits auf dem Zielgerät installiert sein.
- Das Gerät muss [ordnungsgemäß bereitgestellt](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) sein.

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Neues Gerätekonfigurationsprofil für das Erstellen von Netzwerkgrenzen <!-- 1311967 -->   
Ein neues Gerätekonfigurationsprofil namens **Netzwerkgrenze** ist jetzt neben Ihren anderen Gerätekonfigurationsprofilen verfügbar. Verwenden Sie dieses Profile, um Onlineressourcen zu definieren, die als „geschäftlich“ oder „vertrauenswürdig“ angesehen werden sollen. Sie müssen eine Netzwerkgrenze für ein Gerät definieren, *bevor* Features wie Windows Defender Application Guard und Windows Information Protection auf dem Gerät verwendet werden können. Es ist wichtig, nur eine Netzwerkgrenze für jedes Gerät zu definieren.

Sie können Unternehmenscloudressourcen, IP-Adressbereiche und interne Proxyserver definieren, die als vertrauenswürdig angesehen werden sollen. Sobald diese definiert sind, kann die Netzwerkgrenze von anderen Features wie Windows Defender Application Guard und Windows Information Protection verwendet werden.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Zwei zusätzliche Einstellungen für Windows Defender Antivirus <!-- 1338409 -->  
**Ebene der Dateiblockierung**

| | |
|---|---|
| Nicht konfiguriert | **Nicht konfiguriert** verwendet die Standardblockierungsebene von Windows Defender Antivirus und bietet eine starke Erkennung ohne das Risiko zu erhöhen, zulässige Dateien zu erkennen. |
| Hoch | **Hoch** wendet eine starke Erkennungsebene an.
| Hoch +  | **Hoch +** bietet die Ebene „Hoch“ mit zusätzlichen Schutzmaßnahmen, die sich auf die Clientleistung auswirken können.
| Keine Toleranz  | **Keine Toleranz** blockiert alle unbekannten ausführbaren Dateien. |

Es ist zwar unwahrscheinlich, aber dennoch können bei der Einstellung auf **Hoch** einige zulässige Dateien erkannt werden.
Es wird empfohlen, die Ebene der Datenblockierung auf den Standardwert, **Nicht konfiguriert**, festzulegen.

**Timeouterweiterung für die Dateiüberprüfung durch die Cloud**  

| | |
|--|--|
| Anzahl von Sekunden (0–50) | Geben Sie den maximalen Zeitraum an, für den Windows Defender Antivirus eine Datei blockieren soll, während auf ein Ergebnis von der Cloud gewartet wird. Der Standardzeitraum beträgt 10 Sekunden. Jede zusätzliche Zeit, die hier angegeben wird (bis zu 50 Sekunden), wird zu diesen 10 Sekunden addiert. In den meisten Fällen nimmt der Scan wesentlich weniger als den Maximalwert in Anspruch. Das Erweitern des Zeitraums ermöglicht es der Cloud, verdächtige Dateien gründlich zu überprüfen. Es wird empfohlen, diese Einstellung zu aktivieren und mindestens 20 zusätzliche Sekunden anzugeben. |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Citrix-VPN wurde für Windows 10-Geräte hinzugefügt <!-- 1512457 -->  
Sie können Citrix-VPN für ihre Windows 10-Geräte konfigurieren. Sie können Citrix-VPN in der Liste *Verbindungstyp auswählen* im Blatt **Basis-VPN** auswählen, wenn Sie ein VPN für Windows 10 oder höher konfigurieren.

> [!Note]
> Die Citrix-Konfiguration ist bereits für iOS und Android vorhanden.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>WLAN-Verbindungen unterstützen vorinstallierte Schlüssel unter iOS <!-- 1550823 -->
Kunden können WLAN-Profile konfigurieren, um vordefinierte Schlüssel (pre-shared keys, PSK) für persönliche WPA/WPA2-Verbindungen auf iOS-Geräten zu verwenden. Diese Profile werden per Push an das Gerät des Benutzers übertragen, wenn das Gerät bei Intune registriert wird.

Wenn das Profil an das Gerät übertragen wurde, hängt der nächste Schritt von der Profilkonfiguration ab.  Wenn automatisches Herstellen einer Verbindung festgelegt ist, geschieht das bei der nächsten Gelegenheit, bei der das Netzwerk benötigt wird.  Wenn das Profil manuelles Herstellen der Verbindung festlegt, muss der Benutzer die Verbindung manuell aktivieren.  

### <a name="intune-apps"></a>Intune-Apps

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Zugriff auf Protokolle von verwalteten Geräten für iOS <!-- 1469920 -->
Endbenutzer, bei denen der Managed Browser installiert ist, können jetzt den Verwaltungsstatus aller von Microsoft veröffentlichten Apps anzeigen und Protokolle zur Problembehandlung ihrer verwalteten iOS-Apps senden.

Informationen zum Aktivieren des Problembehandlungsmodus im Managed Browser auf einem iOS-Gerät finden Sie unter [Zugreifen auf Protokolle von verwalteten Apps mithilfe des Managed Browsers unter iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Verbesserungen des Workflows für das Gerätesetup im Unternehmensportal für iOS in Version 2.9.0 <!-- 1417174 -->

Der Workflow für die Geräteinstallation in der Unternehmensportal-App unter iOS wurde verbessert. Die Sprache ist nun benutzerfreundlicher. Zudem haben wir Bildschirme nach Möglichkeit zusammengefasst. Die Sprache wurde speziell für Ihr Unternehmen angepasst, indem der Name Ihres Unternehmens im gesamten Setuptext verwendet wird. Dieser aktualisierte Workflow ist auf der Seite mit den  [Aktualisierungen für die Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md) zu sehen.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>Die Benutzerentität enthält die aktuellen Benutzerdaten im Data Warehouse-Datenmodell <!-- 1544273 -->
Die erste Version des Intune Data Warehouse-Datenmodells enthielt lediglich aktuelle Verlaufsdaten für Intune. Berichtersteller konnten den aktuellen Status eines Benutzers nicht erfassen. In diesem Update wird die **Benutzerentität** mit den aktuellen Benutzerdaten voraufgefüllt.


## <a name="notices"></a>Benachrichtigungen

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>Planen der Änderung: Neue Windows 10-Einstellung für die Kioskkonfiguration in Intune <!-- 1560072 -->
Es wurde geändert, wie und wo Sie Desktops von Windows 10-Version 1709 und höher (RS3 und höher) im Intune-Azure-Portal konfigurieren.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich? 
Unseren Informationen zufolge verwenden Sie die Einstellung „Windows 10 > Geräteeinschränkungen > Kiosk (Vorschau)“. Diese wird im Mai in der Benutzeroberfläche in „Windows 10 > Geräteeinschränkungen > Kiosk (obsolete)“ (Kiosk (Veraltet)) umbenannt, um deutlich zu machen, dass von der Verwendung abgeraten wird. Die Einstellung bleibt jedoch bis zum Juli-Update von Intune weiterhin funktionsfähig. Anschließend wird sie im Back-End deaktiviert und wird nicht mehr funktionieren. Alternativ wird im Mai ein neues Gerätekonfigurationsprofil veröffentlicht: „Windows 10 > Kiosk“. Dieses enthält die Einstellungen zum Konfigurieren der Kiosks unter Windows 10-Version RS4 und höher.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?  
Im Rahmen des Intune-Updates Ende Mai werden auch Anleitungen veröffentlicht, mit denen Sie testen und überprüfen können, ob Sie Ihre Kioskkonfiguration von Windows 10-Version RS3 auf die Version RS4 migrieren können. Konfigurieren Sie Ihre Geräte mithilfe dieser Anleitungen und mithilfe des neuen Gerätekonfigurationsprofils als Kiosks.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Sowohl eigenständige Intune-Kunden als auch hybride Kunden (die Intune mit Configuration Manager verwenden) sind von dieser Änderung betroffen. Diese Integration soll Ihre Cloudverwaltung vereinfachen. Es gibt jetzt nur noch ein Blatt (das Blatt „Intune“) in Azure, über das Sie Gruppen, Richtlinien, Apps und die Verwaltung mobiler Geräte verwalten.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Markieren Sie bitte Intune und nicht das Dienstblatt „Intune-App-Schutz“ als Favorit, und machen Sie sich mit dem Richtlinienworkflow für den App-Schutz auf der Seite „Mobile App“ in Intune vertraut. Es wird zwar für einen kurzen Zeitraum eine Umleitung eingerichtet, aber danach wird das Blatt „App-Schutz“ entfernt. Beachten Sie, dass alle Richtlinien zum App-Schutz bereits in Intune verschoben wurden. Sie können Ihre Richtlinien für den bedingten Zugriff verändern, indem Sie die in der folgenden Dokumentation beschriebenen Schritte ausführen: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Weitere Informationen**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Planen der Änderung: Änderung in der Unterstützung für das Microsoft Intune App SDK-Cordova-Plug-In
Intune beendet die Unterstützung des [Microsoft Intune App SDK-Cordova-Plug-Ins](app-sdk-cordova.md) am 1. Mai 2018. Sie sollten stattdessen das Intune App Wrapping Tool verwenden, um Ihre auf Cordova basierenden Apps auf die Verwaltbarkeit und Verfügbarkeit in Intune vorzubereiten. Wenn diese Änderung wirksam wird, wird das Microsoft Intune APP SDK-Cordova-Plug-In jedoch weder beibehalten, noch werden Updates empfangen. App-Entwickler werden dieses Plug-In nicht verwenden können. Intune plant, weiterhin mit Cordova erstellte Apps zu unterstützen. Allerdings wird die Funktionalität mit dem Microsoft Intune APP SDK-Cordova-Plug-In erstellter Apps in Intune eingeschränkt sein. Nach Wrapping mit dem Intune App Wrapping Tool können Apps Endbenutzern normal bereitgestellt werden. Für auf Cordova basierende Android-Apps, die im Google Play Store veröffentlicht werden, gilt:
- Endbenutzer werden beim ersten Start aufgefordert, Anmeldeinformationen zum Empfangen der Intune-Richtlinie einzugeben.
- Apps sollten im App-Store für Intune-Benutzer veröffentlicht werden, z.B. „Contoso App for Intune“.

Weitere Informationen zum App Wrapping Tool finden Sie unter [Vorbereiten von iOS-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool](app-wrapper-prepare-ios.md) und [Vorbereiten von Android-Apps für App-Schutzrichtlinien mit dem Intune App Wrapping Tool](app-wrapper-prepare-android.md). Sollten Probleme auftreten oder Sie Fragen haben, kontaktieren Sie [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Planen von Änderungen: Verwenden von Intune in Azure für die Verwaltung Ihrer mobilen Geräte jetzt möglich <!-- 1227338 -->
Vor über einem Jahr wurde eine [öffentlich zugängliche Vorschau von Intune in Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) angekündigt. Sechs Monate später wurde [die neue Benutzeroberfläche für Administratoren allgemein zugänglich gemacht](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/). Ab 31. August 2018 wird die Verwaltung mobiler Geräte (MDM) in der klassischen Silverlight-Konsole für Kunden deaktiviert, die eine eigenständige Intune-Version verwenden. Stattdessen können Sie [Intune in Azure](https://aka.ms/Intune_on_Azure) verwenden, wenn Sie Ihre Geräte mobil verwalten möchten. Wenn Sie immer noch die klassische Konsole für die Verwaltung mobiler Geräte verwenden, sollten Sie sich nun mit Intune in Azure vertraut machen. Diese Änderungen sollten keine Auswirkungen auf die Benutzer haben. Die klassische PC-Verwaltung bleibt in Silverlight erhalten. Erfahren Sie [hier](https://aka.ms/Intune_on_Azure_mdm) mehr über diese Änderungen und deren Folgen für Sie.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Direkter Zugriff auf Apple-Registrierungsszenarien <!--951869-->
Für Intune-Konten, die nach Januar 2017 erstellt wurden, hat Intune direkten Zugriff auf Apple-Registrierungsszenarien mithilfe der Workload „Geräte registrieren“ im Azure-Portal aktiviert. Bisher konnte nur über Links im klassischen Intune-Portal auf die Apple-Registrierungsvorschau zugegriffen werden. Vor Januar 2017 erstellte Intune-Konten erfordern eine einmalige Migration, bevor diese Features in Azure verfügbar sind. Der Zeitplan für die Migration wurde noch nicht angekündigt, aber Sie erfahren so bald wie möglich Näheres. Es wird dringend empfohlen, ein Testkonto zu erstellen, um die neue Oberfläche zu testen, wenn Sie mit Ihrem vorhandenen Konto nicht auf das Azure-Portal zugreifen können.

## <a name="whats-coming"></a>Was steht an?

### <a name="local-device-security-option-settings----1251887---"></a>Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1251887 -->
Mithilfe der neuen Einstellungen der Sicherheitsoptionen für lokale Geräte können Sie Sicherheitseinstellungen auf Windows 10-Geräten aktivieren. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968-->

Im April soll die Benutzerfreundlichkeit der Unternehmensportalwebsite verbessert werden. Dafür werden Updates für die Benutzeroberfläche ausgeführt, Workflows optimiert und die Barrierefreiheit verbessert. Diese Änderungen umfassen auf den Kunden ausgerichtete Verbesserungen wie das Freigeben von Apps. Außerdem wurde die Gesamtleistung verbessert, um die Servicequalität zu optimieren.
Es wurden auf der Grundlage von Feedback von Kunden wie Ihnen neue Features hinzugefügt, die die bereits vorhandenen Funktionen und die Benutzerfreundlichkeit um ein Vielfaches verbessern sollen:

-   Verbesserungen der Benutzeroberfläche auf der gesamten Website
-   Möglichkeit, direkte Links zu Apps zu teilen
- Verbesserte Leistung bei großen App-Katalogen

Sie müssen nichts tun, um sich auf diese Änderungen vorzubereiten. Sie werden informiert, sobald die aktualisierte Unternehmensportalwebsite für Sie verfügbar gemacht wird. Es kann jedoch sein, dass Sie danach die Dokumentation für die Endbenutzer aktualisieren und neue Screenshots hinzufügen müssen. Beachten Sie außerdem, dass Sie möglicherweise die Dokumentation für die Unternehmensportal-App unter iOS aktualisieren müssen, da die Website auf dem Abschnitt **Apps** der iOS-App basiert. Eine Beispielabbildung finden Sie auf der Seite zu den [Neuerungen der App-Benutzeroberfläche](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple erfordert Updates für die Transportsicherheit für Anwendungen <!--748318-->
Apple hat angekündigt, dass bestimmte Anforderungen für die Transportsicherheit für Anwendungen (Application Transport Security, ATS) erzwungen werden. ATS wird verwendet, um eine strengere Sicherheit in allen App-Kommunikationen über HTTPS zu erzwingen. Diese Änderung wirkt sich auf Intune-Kunden aus, die die iOS-Unternehmensportal-App verwenden. Die aktuellen Informationen finden Sie auf dem [Intune-Support-Blog](https://aka.ms/compportalats).



## <a name="see-also"></a>Siehe auch
* [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roadmap für die Cloudplattform](https://www.microsoft.com/cloud-platform/roadmap)
* [What‘s new in the Intune App UI (Neues auf der Intune-App-Benutzeroberfläche)](whats-new-app-ui.md)
* [Neuerungen in den vorherigen Monaten](whats-new-archive.md)
