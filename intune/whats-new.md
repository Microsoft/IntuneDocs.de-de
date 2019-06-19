---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c14568a0581220cf5941984645bd0b9044e00c1
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749951"
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Außerdem finden Sie hier Informationen zu [bevorstehenden Änderungen](in-development.md), [wichtigen Hinweisen](#notices) sowie Informationen zu [früheren Releases](whats-new-archive.md). 

> [!Note]
> Einige Features werden im Laufe mehrerer Wochen bereitgestellt und sind in der ersten Woche möglicherweise nicht für alle Kunden verfügbar.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-may-27-2019"></a>Woche vom 27. Mai 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Berichterstellung über potenziell schädlichen Apps auf Android-Geräten <!-- 4223162 -->
Intune stellt jetzt zusätzliche Berichterstellungsinformationen über potenziell schädliche Apps auf Android-Geräten bereit. 

## <a name="week-of-may-20-2019"></a>Woche vom 20. Mai 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="windows-company-portal-app----3316993---"></a>Windows-Unternehmensportal-App <!-- 3316993 -->
Die Windows-Unternehmensportal-App enthält jetzt die neue Seite **Geräte**. Auf der Seite **Geräte** werden den Endbenutzern alle ihre registrierten Geräte angezeigt. Benutzer sehen diese Änderung im Unternehmensportal, wenn sie Version 10.3.4291.0 und höher verwenden. Informationen zum Konfigurieren des Unternehmensportals finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot-Gerät – Attributname „OrderID“ in „Gruppentag“ geändert <!-- 4659453 -->

Um die Aussagekraft zu erhöhen, wurde der Attributname **OrderID** bei Autopilot-Geräten in **Gruppentag** geändert. Wenn Sie Autopilot-Geräteinformationen über freigegebene Clustervolumen (CSVs) hochladen, müssen Sie „Gruppentag“ (und nicht „OrderID“) als Spaltenüberschrift verwenden.  

## <a name="week-of-may-13-2019"></a>Woche vom 13. Mai 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App  <!-- 1927359 idready wnready-->
Bei Geräten, die bereits mithilfe des Setup-Assistenten über eine der Methoden von Apple für die Registrierung von Unternehmensgeräten registriert wurden, unterstützt Intune das Unternehmensportal nicht mehr, wenn es manuell von Endbenutzern aus dem App-Store installiert wurde. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Wenn Benutzer die Unternehmensportal-App aus dem App Store installieren und dann versuchen, diese Geräte darüber zu registrieren, erhalten sie eine Fehlermeldung. Es wird vorausgesetzt, dass diese Geräte die Unternehmensportal-App nur dann verwenden, wenn sie während der Registrierung von Intune mithilfe von Push automatisch übertragen wird. Registrierungsprofile in Intune im Azure-Portal werden aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Wenn Sie wünschen, dass Ihre DEP-Gerätebenutzer die Unternehmensportal-App verwenden, müssen Sie Ihre Einstellungen in einem Registrierungsprofil angeben. 

Darüber hinaus wird der Bildschirm **Gerät identifizieren** im iOS-Unternehmensportal entfernt. Deshalb müssen Administratoren, die den bedingten Zugriff aktivieren oder Unternehmens-Apps bereitstellen möchten, das DEP-Registrierungsprofil aktualisieren. Diese Anforderung gilt nur, wenn die DEP-Registrierung mit dem Setup-Assistenten authentifiziert wird. In diesem Fall müssen Sie die Unternehmensportal-App mithilfe von Push auf das Gerät übertragen. Wählen Sie dazu **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > anschließend ein Token > **Profile** > dann ein Profil und > **Eigenschaften** aus, und > legen Sie für **Unternehmensportal installieren** den Wert **Ja** fest.

Um die Unternehmensportal-App auf bereits registrierten DEP-Geräten zu installieren, müssen Sie zu „Intune“ > „Client-Apps“ wechseln und sie als verwaltete App mit App-Konfigurationsrichtlinien mithilfe von Push übertragen. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Konfigurieren, wie Endbenutzer eine LOB-App mithilfe einer App-Schutzrichtlinie aktualisieren können <!-- 3568384 -->
Sie können jetzt konfigurieren, wo Ihre Endbenutzer eine aktualisierte Version einer LOB-App (Line-of-Business-App, branchenspezifische App) erhalten können. Endbenutzer sehen diese Funktion im bedingten Startdialogfeld **App-Mindestversion**, in dem der Benutzer aufgefordert wird, auf eine Mindestversion der LOB-App zu aktualisieren. Sie müssen diese Updatedetails als Teil Ihrer LOB-App-Schutzrichtlinie (APP) angeben. Dieses Feature ist unter iOS und Android verfügbar. Unter iOS erfordert dieses Feature, dass die App integriert (oder mit dem Wrapping Tool umschlossen) und dafür das Intune SDK für iOS, V. 10.0.7 oder höher, verwendet wird. Unter Android wäre für dieses Feature die neueste Unternehmensportal-App erforderlich. Um zu konfigurieren, wie ein Endbenutzer eine LOB-App aktualisiert, muss eine verwaltete App-Konfigurationsrichtlinie mit dem Schlüssel `com.microsoft.intune.myappstore` an diese gesendet werden. Der gesendete Wert definiert, aus welchem Speicher der Endbenutzer die App herunterladen wird. Wenn die App über das Unternehmensportal bereitgestellt wird, muss der Wert `CompanyPortal` sein. Für alle anderen Speicher müssen Sie eine vollständige URL eingeben.

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>PowerShell-Skripts zur Erweiterung der Intune-Verwaltung  <!-- 3734186 idready -->
Sie können PowerShell-Skripts so konfigurieren, dass sie mit Administratorrechten des Benutzers auf dem Gerät ausgeführt werden. Weitere Informationen finden Sie unter [Verwenden von PowerShell-Skripts auf Windows 10-Geräten in Intune](intune-management-extension.md) und [Win32-App-Verwaltung](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Verwaltung von Android Enterprise-Apps <!-- 4459905 -->
Um IT-Administratoren die Konfiguration und Nutzung der Android Enterprise-Verwaltung zu erleichtern, fügt Intune der Intune-Verwaltungskonsole automatisch vier gängige Android Enterprise-bezogene Apps hinzu. Die vier Android Enterprise-Apps sind wie folgt:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : für vollständig verwaltete Android Enterprise-Szenarien.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : hilft bei der Anmeldung bei Ihren Konten, wenn Sie die zweistufige Überprüfung verwenden.
- **[Intune-Unternehmensportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : wird für App Protection Policies (APP) und Szenarien mit Android Enterprise-Arbeitsprofilen genutzt.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : wird für dedizierte/Kioskszenarien mit Android Enterprise verwendet.

Bisher mussten IT-Administratoren diese Apps im [verwalteten Google Play Store](https://play.google.com/store/apps) als Teil des Setups manuell auffinden und genehmigen. Durch diese Änderung entfallen diese bislang manuellen Schritte, sodass Kunden die Android Enterprise-Verwaltung einfacher und schneller nutzen können.

Administratoren werden feststellen, dass diese vier Apps automatisch zur Liste ihrer Intune-Apps hinzugefügt wurden, wenn sie ihren Intune-Mandanten zum ersten Mal mit dem verwaltetem Google Play Store verbinden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto](connect-intune-android-enterprise.md). Für Mandanten, die ihren Mandanten bereits verbunden haben oder Android Enterprise bereits nutzen, gibt es keinerlei Administrationsaufwand. Diese vier Apps werden automatisch binnen 7 Tagen nach Abschluss des Dienstrollouts vom Mai 2019 verfügbar sein.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>PFX-Zertifikatconnector für Microsoft Intune aktualisiert  <!-- 1533038 -->
Wir haben ein Update zum [PFX-Zertifikatconnector für Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht, das ein Problem behebt, bei dem vorhandene PFX-Zertifikate weiter erneut verarbeitet werden. Dies führt dazu, dass der Connector die Verarbeitung neuer Anforderungen beendet.

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Intune-Sicherheitsaufgaben für Defender ATP (in öffentlicher Vorschau)     <!-- 3208597 -->
In der öffentlichen Vorschau können Sie Intune verwenden, um [Sicherheitsaufgaben für Microsoft Defender Advanced Threat Protection (ATP)](atp-manage-vulnerabilities.md) zu verwalten. Diese Integration in ATP bietet einen risikobasierten Ansatz zur Erkennung, Priorisierung und Behebung von Schwachstellen und Fehlkonfigurationen an Endpunkten, wobei gleichzeitig die Zeitspanne zwischen Ermittlung und Risikominderung verkürzt wird.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie <!-- 3617671   idstaged-->
Viele Geräte unter Windows 10 und höher haben Chipsätze von Trusted Platform Module (TPM). Dieses Update enthält eine neue Konformitätseinstellung, die die Version des TPM-Chips auf dem Gerät überprüft. 

Unter [Richtlinieneinstellungen für Windows 10 und höher](compliance-policy-create-windows.md#device-security) wird diese Einstellung beschrieben.

Gilt für: Windows 10 und höher

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Hindern von Endbenutzern am Ändern ihres privaten Hotspots und Deaktivieren der Siri-Serverprotokollierung auf iOS-Geräten <!-- 4097904   -->  
Sie können auf einem iOS-Gerät ein Geräteeinschränkungsprofil einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). Dieses Update umfasst neue Einstellungen, die Sie konfigurieren können:

- **Integrierte Apps**: Serverseitige Protokollierung für Siri-Befehle
- **Drahtlos**: Benutzeränderung des persönlichen Hotspots (nur überwacht)

Zum Anzeigen dieser Einstellungen wechseln Sie zu [built-in app settings for iOS](device-restrictions-ios.md#built-in-apps) (Integrierte App-Einstellungen für iOS) und [wireless settings for iOS](device-restrictions-ios.md#wireless) (Drahtloseinstellungen für iOS).

Gilt für: iOS 12.2 und höher

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Neue Geräteeinschränkungseinstellungen für Classroom-App für macOS-Geräte <!-- 4097905   --> 
Sie können für macOS-Geräte Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). Dieses Update enthält neue Classroom-App-Einstellungen, die Option zum Sperren von Screenshots und die Option zum Deaktivieren der iCloud-Fotomediathek.

Die aktuellen Einstellungen finden Sie unter [macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-macos.md).

Gilt für: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Die iOS-Einstellung „Kennwort für Zugriff auf App Store“ wird umbenannt<!-- 4557891  -->
Die Einstellung **Kennwort für Zugriff auf App Store** wird umbenannt in **iTunes Store-Kennwort für alle Käufe erforderlich** (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für „Plattform“ > **Geräteeinschränkungen** für „Profiltyp“ > **App Store, Dokumentanzeige, Spiele**).

Zum Anzeigen der verfügbaren Einstellungen wechseln Sie zu [App Store, Dokumentanzeige, Spiele > iOS-Einstellungen](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gilt für: iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender Advanced Threat Protection-Baseline (Vorschauversion)  <!--  3754134 -->
Wir haben eine Vorschauversion der Sicherheitsbaseline für [Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md)-Einstellungen hinzugefügt. Diese Baseline ist verfügbar, wenn Ihre Umgebung den Anforderungen zur Verwendung von [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) entspricht.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Statusseite für die Windows-Registrierung ist jetzt allgemein verfügbar <!-- 3605348 -->
Die Statusseite für die Registrierung ist jetzt in der Vorschauversion nicht mehr enthalten. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Update bei Intune-Benutzeroberfläche – Erstellung eines Autopilot-Registrierungsprofils  <!-- 4593669 -->
Die Benutzeroberfläche zum Erstellen eines Autopilot-Registrierungsprofils wurde aktualisiert und an die Stile von Azure-Benutzeroberflächen angepasst. Weitere Informationen finden Sie unter [Erstellen eines Autopilot-Registrierungsprofils](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Zukünftig werden weitere Intune-Szenarien auf diesen neuen Stil der Benutzeroberfläche aktualisiert.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>„Autopilot-Zurücksetzung aktivieren“ bei allen Windows-Geräten <!-- 4225665 -->
„Autopilot-Zurücksetzung aktivieren “ funktioniert jetzt bei allen Windows-Geräten – sogar denen, die nicht zur Verwendung der Statusseite für die Registrierung konfiguriert wurden. Wenn für ein Gerät bei der Erstregistrierung keine Statusseite für die Registrierung konfiguriert wurde, wechselt das Gerät nach der Anmeldung direkt zum Desktop. Es kann bis zu acht Stunden dauern, bis die Synchronisierung abgeschlossen ist und das Gerät in Intune als konform angezeigt wird. Weitere Informationen finden Sie unter [Reset devices with remote Windows Autopilot Reset (Zurücksetzen von Geräten mit Remote-Windows Autopilot-Zurücksetzung)](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Exaktes IMEI-Format beim Durchsuchen von „Alle Geräte“ nicht erforderlich <!--30407680 -->
Wenn Sie **Alle Geräte** durchsuchen, müssen Sie in IMEI-Nummern keine Leerzeichen einbeziehen.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Das Löschen eines Geräts im Apple-Portal wird im Intune-Portal widergespiegelt <!--2489996 -->
Wenn ein Gerät aus dem Programm zur Geräteregistrierung von Apple oder den Apple Business Manager-Portalen gelöscht wird, wird das Gerät bei der nächsten Synchronisierung automatisch aus Intune gelöscht.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>Die Nachverfolgung auf der Seite zum Registrierungsstatus umfasst jetzt Win32-Apps <!-- 2714451 -->
Dies gilt nur für Geräte mit Windows 10, Version 1903 und höher. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](windows-enrollment-status.md).

### <a name="device-management"></a>Geräteverwaltung

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Zurücksetzen von Geräten in einem Massenvorgang mithilfe der Graph-API <!-- 3295288 -->
Mithilfe der Graph-API können Sie jetzt in einem Massenvorgang bis zu 100 Geräte zurücksetzen.


### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Der Verschlüsselungsbericht ist in der öffentlichen Vorschau nicht mehr enthalten   <!-- 4587546      -->
Der [report for BitLocker and device encryption](encryption-monitor.md) (Bericht für BitLocker-Geräteverschlüsselung) ist jetzt allgemein verfügbar und nicht mehr Teil der öffentlichen Vorschau. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Outlook-Signatur und biometrische Einstellungen für iOS- und Android-Geräte <!-- 4050557 -->
Sie können jetzt angeben, ob die Standardsignatur in Outlook auf iOS- und Android-Geräten aktiviert ist. Darüber hinaus können Sie wählen, dass Benutzer die biometrische Einstellung in Outlook für iOS ändern dürfen.

## <a name="week-of-may-6-2019"></a>Woche vom 6. Mai 2019 

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>NAC-Unterstützung (Network Access Control, Netzwerkzugriffssteuerung) für F5 Access für iOS-Geräte <!-- 4500808 -->

F5 hat ein Update zu BIG-IP 13 veröffentlicht, dass NAC-Funktionalität für F5 Access unter iOS in Intune ermöglicht. Zur Nutzung dieses Features ist Folgendes erforderlich:

- Aktualisieren Sie BIG-IP auf 13.1.1.5. BIG-IP 14 wird nicht unterstützt.
- Integrieren Sie BIG-IP für NAC in Intune. Lesen Sie dazu die Schritte in [Übersicht: Konfigurieren von APM für Gerätestatusüberprüfungen mit Endpunktverwaltungssystemen](https://support.f5.com/kb/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89).
- Überprüfen Sie die Einstellung **Netzwerkzugriffssteuerung (NAC) aktivieren** im VPN-Profil in Intune.

Die verfügbaren Einstellungen finden Sie unter [Configure VPN settings on iOS devices (Konfigurieren von VPN-Einstellungen auf iOS-Geräten)](vpn-settings-ios.md).

Gilt für: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>PFX-Zertifikatconnector für Microsoft Intune aktualisiert <!-- doc-vso 1521237  -->  
Wir haben ein Update für den [PFX-Zertifikatconnector für Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht, wodurch das Abrufintervall von 5 Minuten auf 30 Sekunden verkürzt wird.

## <a name="week-of-april-22-2019"></a>Woche vom 22. April 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Verwenden des Compliance-Managers zum Erstellen von Bewertungen für Microsoft Intune<!-- 4404750 -->

Der [Compliance-Manager](https://servicetrust.microsoft.com/ComplianceManager) (Link öffnet eine andere Microsoft-Website) ist ein Workflow-basiertes Tool für die Risikobewertung in Microsoft Service Trust Portal. Mit dem Tool können Sie die Aktivitäten zur Einhaltung behördlicher Bestimmung Ihres Unternehmens im Bezug auf Microsoft-Diensten überwachen, zuweisen und überprüfen. Sie können Ihre eigene Bewertung der Konformität mit Office 365, Azure, Dynamics, Professional Services und Intune erstellen. Zwei Bewertungen sind in Intune verfügbar: FFIEC und DSGVO.

Der Compliance-Manager unterstützt Sie beim Aufteilen der Kontrollen: Kontrollen, die von Microsoft verwaltet werden und Kontrollen, die von Ihrer Organisation verwaltet werden. Sie können die Bewertungen abschließen und anschließend extrahieren und drucken.

Die Konformität mit [FFIEC (Federal Financial Institutions Examination Council)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (Link öffnet eine andere Microsoft-Website) umfasst mehrere Standards für Onlinebanking, die vom FFIEC erlassen wurden. Diese Bewertung ist die am häufigsten angeforderte Bewertung von Finanzinstituten, die Intune verwenden. Sie interpretiert, wie Intune die Konformität mit Cybersicherheitsrichtlinien des FFIEC für öffentliche Cloud-Workloads unterstützt. Die FFIEC-Bewertung von Intune ist die zweite FFIEC-Bewertung im Compliance-Manager.

Im folgenden Beispiel werden die FFIEC-Kontrollen aufgeschlüsselt. 64 Kontrollen werden von Microsoft verwaltet. Ihre Organisation ist für die restlichen 12 Kontrollen zuständig.

![Beispielbewertung für die FFIEC-Bewertung in Intune, einschließlich Kundenaktionen und Microsoft-Aktionen](./media/intune-ffiec-assessment-status.png)

Die [DSGVO (Datenschutz-Grundverordnung)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (Link öffnet eine andere Microsoft-Website) ist ein Gesetz der Europäischen Union (EU), das die Rechte von Personen und ihren Daten schützt. Die DSGVO-Bewertung ist die am häufigsten angeforderte Bewertung zur Unterstützung der Konformität mit Datenschutzbestimmungen. 

Im folgenden Beispiel werden die DSGVO-Kontrollen aufgeschlüsselt. 49 Kontrollen werden von Microsoft verwaltet. Ihre Organisation ist für die restlichen 66 Kontrollen zuständig.

![Beispielbewertung für die DSGVO-Bewertung in Intune, einschließlich Kundenaktionen und Microsoft-Aktionen](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Woche vom 15. April 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>OpenSSL-Verschlüsselung für Android-App-Schutzrichtlinien <!-- 3747362 -->
Intune-App-Schutzrichtlinien für Android-Geräte nutzen nun eine OpenSSL-Verschlüsselungsbibliothek, die FIPS 140-2-konform ist. Weitere Informationen finden Sie im Abschnitt [Verschlüsselung](app-protection-policy-settings-android.md#encryption) unter [Einstellungen für App-Schutzrichtlinien in Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Aktivieren von Win32-App-Abhängigkeiten <!-- 2617348  -->
Als Administrator können Sie voraussetzen, dass Apps als Abhängigkeiten installiert werden, bevor Ihre Win32-App installiert wird. Das heißt, das Gerät muss die abhängige(n) App(s) installieren, bevor die Win32-App installiert wird. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen. Wählen Sie **Windows-App (Win32)** als **App-Typ** aus. Nachdem Sie die App hinzugefügt haben, können Sie auf **Abhängigkeiten** klicken, um die abhängigen Apps hinzuzufügen, die installiert werden müssen, bevor die Win32-App installiert werden kann. Weitere Informationen finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Installationsinformationen zur App-Version für Apps im Microsoft Store für Unternehmen <!-- 3537391   -->
Berichte zur App-Installation enthalten Informationen zur App-Version für Apps im Microsoft Store für Unternehmen. Klicken Sie in Intune auf **Client-Apps** > **Apps**. Wählen Sie eine **App im Microsoft Store für Unternehmen** aus, und klicken Sie dann im Abschnitt **Überwachen** auf **Geräteinstallationsstatus**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Ergänzungen zu Anforderungsregeln für Win32-Apps <!-- 3676883   -->
Sie können Anforderungsregeln mithilfe von PowerShell-Skripts, Registrierungswerten und Dateisysteminformationen erstellen. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann **Windows-App (Win32)** als **App-Typ** auf dem Blatt **App hinzufügen** aus.  Klicken Sie auf **Anforderungen** > **Hinzufügen**, um zusätzliche Anforderungsregeln zu konfigurieren. Wählen Sie dann entweder **Dateityp**, **Registrierung** oder **Skript** als **Anforderungstyp** aus. Weitere Informationen finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](apps-win32-app-management.md).

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Konfigurieren von Win32-Apps für die Installation auf in Intune registrierten, in Azure AD eingebundenen Geräten <!-- 3695227  -->
Sie können Ihre Win32-Apps für die Installation auf in Intune registrierten, in Azure AD eingebundenen Geräten zuweisen. Weitere Informationen zu Win32-Apps in Intune finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---794259----"></a>Primärer Benutzer in der Geräteübersicht <!--794259  -->
Die Seite „Geräteübersicht“ zeigt den primären Benutzer (Affinität zwischen Benutzer und Gerät) an. Klicken Sie auf **Intune** > **Geräte** > **Alle Geräte**, und wählen Sie dann ein Gerät aus, um den primären Benutzer eines Geräts anzuzeigen. Der primäre Benutzer wird außerdem oben auf der Seite **Übersicht** angezeigt.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Zusätzliche Berichterstellung für verwaltete Google Play-Apps für Android Enterprise-Arbeitsprofilgeräte <!-- 4105925  -->
Sie können die Versionsnummer von auf Android Enterprise-Arbeitsprofilgeräten bereitgestellten, verwalteten Google Play-Apps anzeigen. Dies gilt nur für erforderliche Apps.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Tastaturen von Drittanbietern für iOS <!-- 4111843   -->
Die Intune APP-Unterstützung (App Protection Policy, App-Schutzrichtlinie) für die Einstellung **Tastaturen von Drittanbietern** für iOS wird aufgrund einer Änderung an der iOS-Plattform beendet. Sie können diese Einstellung in der Intune-Verwaltungskonsole nicht mehr konfigurieren, und sie wird auf dem Client im Intune App SDK nicht mehr erzwungen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Festlegen der Anmeldeeinstellungen und Steuern der Neustartoptionen für macOS-Geräte <!-- 1210083  -->
Sie können auf macOS-Geräten ein Gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **macOS** auswählen > **Gerätefunktionen**). Dieses Update umfasst neue Einstellungen im Fenster „Anmelden“, z. B. die Anzeige eines benutzerdefinierten Banners, die Auswahl der Anmeldemethode für Benutzer, das Anzeigen oder Ausblenden von Energieeinstellungen und mehr.

Informationen zu diesen Einstellungen finden Sie unter [macOS device feature settings in Intune (Einstellungen von macOS-Gerätefeatures)](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Konfigurieren von WLAN auf dedizierten Geräten im Multi-App-Kioskmodus für Android Enterprise-Gerätebesitzer <!--3041940  -->
Sie können die Einstellungen für Android Enterprise-Gerätebesitzer aktivieren, wenn das Gerät als dediziertes Gerät im Multi-App-Kioskmodus ausgeführt wird. Mit diesem Update können Sie Benutzern ermöglichen, WLAN-Netzwerke zu konfigurieren und Verbindungen mit diesen herzustellen (**Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp) > **Dedizierte Geräte** > **Kioskmodus**: **Multi-App** > **WLAN-Konfiguration**). 

Eine Liste aller konfigurierbaren Einstellungen finden Sie unter [Android Enterprise device settings to allow or restrict features (Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-android-for-work.md).

Gilt für: Dedizierte Android Enterprise-Geräte im Multi-App-Kioskmodus


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Konfigurieren von Bluetooth und Kopplung auf dedizierten Geräten im Multi-App-Kioskmodus für Android Enterprise-Gerätebesitzer <!-- 3041941  -->
Sie können die Einstellungen für Android Enterprise-Gerätebesitzer aktivieren, wenn das Gerät als dediziertes Gerät im Multi-App-Kioskmodus ausgeführt wird. Mit diesem Update können Sie Benutzern ermöglichen, Bluetooth zu aktivieren und Geräte per Bluetooth zu koppeln (**Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp) > **Dedizierte Geräte** > **Kioskmodus**): **Multi-App** > **Bluetooth-Konfiguration**). 

Eine Liste aller konfigurierbaren Einstellungen finden Sie unter [Android Enterprise device settings to allow or restrict features (Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-android-for-work.md).

Gilt für: Dedizierte Android Enterprise-Geräte im Multi-App-Kioskmodus

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Erstellen und Verwenden von OEMConfig-Gerätekonfigurationsprofilen in Intune <!-- 3305883  -->
Mit diesem Update unterstützt Intune die Konfiguration von Android Enterprise-Geräten mit OEMConfig. Das heißt, Sie können ein Gerätekonfigurationsprofil erstellen und Einstellungen auf Android Enterprise-Geräte mit OEMConfig anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform)).

Die Unterstützung wird derzeit auf einer pro-OEM-Basis bereitgestellt. Wenden Sie sich an `IntuneOEMConfig@microsoft.com`, wenn eine OEMConfig-App, die Sie benötigen, nicht in der Liste von OEMConfig-Apps verfügbar ist.

Weitere Informationen zu diesem Feature finden Sie unter [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune (Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig in Microsoft Intune)](android-oem-configuration-overview.md).

Gilt für: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows Update-Benachrichtigungen  <!-- 3316758, 3316782  -->
Wir haben den Windows Update-Ringkonfigurationen zwei *Einstellungen für die Benutzeroberfläche* hinzugefügt, die Sie über die Intune-Konsole verwalten können. Sie können nun:
- Benutzern erlauben oder verweigern, [nach Windows-Updates zu suchen](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- die [Windows Update-Benachrichtigungsebene](windows-update-settings.md#windows-update-notification-level) verwalten, die Benutzern angezeigt wird.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Neue Einstellungen zur Geräteeinschränkung für Android Enterprise-Gerätebesitzer <!-- 3574254  -->
Sie können ein Geräteeinschränkungsprofil auf Android Enterprise-Geräten erstellen, um Features zuzulassen oder einzuschränken, Kennwortregeln festzulegen und mehr (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp)). 

Dieses Update umfasst neue Kennworteinstellungen, ermöglicht Vollzugriff auf Apps im Google Play Store für vollständig verwaltete Geräte und mehr. Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](device-restrictions-android-for-work.md). 

Gilt für: Vollständig verwaltete Android Enterprise-Geräte

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie <!-- 3617671 -->

Die Bereitstellung dieses Features verzögert sich und ist in einem zukünftigen Release geplant.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Änderungen der Benutzeroberfläche für den Microsoft Edge-Browser auf Geräten mit Windows 10 und höher <!-- 3775833   -->
Wenn Sie ein Gerätekonfigurationsprofil erstellen, können Sie Microsoft Edge-Features auf Geräten mit Windows 10 und höher zulassen oder einschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Microsoft Edge-Browser**). Die Microsoft Edge-Einstellungen werden in diesem Update besser beschrieben und sind einfacher zu verstehen. 

Diese Features finden Sie unter [Einstellungen für Geräteeinschränkungen in Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

Gilt für: Windows 10 und höher

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Erweiterte Unterstützung für vollständig verwaltete Android Enterprise-Geräte (Preview)  <!--   3903241, 3903244, 3903246   -->
Die sich noch in der Public Preview befindende Unterstützung vollständig verwalteter Android Enterprise-Geräte ([erstmals im Januar 2019 angekündigt](whats-new.md#week-of-january-14-2019)) wurde wie folgt erweitert: 

- Auf vollständig verwalteten und dedizierten Geräten können Sie [Konformitätsrichtlinien](compliance-policy-create-android-for-work.md) erstellen, die Kennwortregeln und Betriebssystemanforderungen enthalten (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android Enterprise** (Plattform) > **Gerätebesitzer** (Profiltyp)). 

  Auf dedizierten Geräten wird das Gerät möglicherweise als **nicht konform** angezeigt. Der bedingte Zugriff ist auf dedizierten Geräten nicht verfügbar. Stellen Sie sicher, dass Sie alle Aufgaben und Aktionen fertig stellen, damit dedizierte Geräte Ihre zugewiesenen Richtlinien einhalten.

- [Bedingter Zugriff:](conditional-access.md) Richtlinien für den bedingten Zugriff, die für Android gelten, gelten auch für vollständig verwaltete Android Enterprise-Geräte. Benutzer können ihre vollständig verwalteten Geräte nun mithilfe der **Microsoft Intune-App** in Azure Active Directory registrieren. Anschließend können sie Kompatibilitätsprobleme anzeigen und beheben, um auf Unternehmensressourcen zuzugreifen.

- Neue Microsoft Intune-App für Endbenutzer: Für vollständig verwaltete Android-Geräte gibt es die neue Endbenutzer-App **Microsoft Intune**. Diese neue App ist besonders schlank und modern. Sie bietet ähnliche Funktionen wie die Unternehmensportal-App, aber für vollständig verwaltete Geräte. Weitere Informationen finden Sie unter der [Microsoft Intune-App auf Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Um vollständig verwaltete Android-Geräte einzurichten, wechseln Sie zu **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte**. Die Unterstützung für vollständig verwaltete Android-Geräte befindet sich weiterhin in der Preview, und einige Intune-Features sind möglicherweise noch nicht voll funktionsfähig.  

Weitere Informationen zu dieser Public Preview finden Sie im Blog unter [Microsoft Intune – Preview 2 for Android Enterprise Fully Managed devices (Microsoft Intune: Preview 2 für vollständig verwaltete Android Enterprise-Geräte)](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>Konfigurieren des Profils zum Überspringen einiger Bildschirme während des Setup-Assistenten <!-- 2276470  wnstaged-->
Wenn Sie ein macOS-Registrierungsprofil erstellen, können Sie dieses konfigurieren, um die folgenden Anzeigen zu überspringen, wenn ein Benutzer den Setup-Assistenten durchläuft:
- Darstellung
- Anzeigefarbton
- iCloudStorage: Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden.  Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.
Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung oder Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Massengerätebenennung beim Registrieren unternehmenseigener iOS-Geräte<!--3566569  -->
Wenn Sie eine der Unternehmensbereitstellungsmethoden (DEP/ABM/ASM) von Apple verwenden, können Sie ein Format für Gerätenamen festlegen, um eingehende iOS-Geräte automatisch zu benennen. Sie können ein Format festlegen, das den Gerätetyp und die Seriennummer in der Vorlage enthält. Klicken Sie hierzu auf **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Token auswählen** >**Profil erstellen** > **Device naming format** (Format für die Gerätebenennung). Sie können vorhandene Profile bearbeiten, der Name wird jedoch nur auf neu synchronisierte Geräte angewendet.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Update der Standardtimeoutnachricht für die Registrierungsstatusseite <!-- 3959331 -->
Die Standardtimeoutnachricht, die Benutzern angezeigt wird, wenn der im Profil für die Registrierungsstatusseite festgelegte Timeoutwert überschritten wird, wurde aktualisiert. Die neue Standardnachricht soll Benutzern dabei helfen, die nächsten Schritte für die Bereitstellung der Registrierungsstatusseite zu verstehen.  

### <a name="device-management"></a>Geräteverwaltung

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Ausmustern nicht konformer Geräte  <!-- 1827291   -->
Die Bereitstellung dieses Features verzögert sich und ist in einem zukünftigen Release geplant.


### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Übernahme der Änderungen an Intune Data Warehouse V1.0 in die Betaversion <!-- 4403765 -->
Als V1.0 in Version 1808 erstmals eingeführt wurde, gab es wichtige Unterschiede zur Beta-API. Diese Änderungen werden mit Version 1903 in der Betaversion der API berücksichtigt. Wenn Sie über wichtige Berichte verfügen, die die Betaversion der API nutzen, wird dringend empfohlen, dass Sie diese Berichte in V1.0 konvertieren, um Breaking Changes zu vermeiden. Weitere Informationen finden Sie im [Änderungsprotokoll für die Intune Data Warehouse-API](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Überwachen des Status der Sicherheitsbaseline (Public Preview) <!-- 3082047 --> 
Der Überwachung von Sicherheitsbaselines wurde eine [Ansicht für einzelne Kategorien](security-baselines-monitor.md#per-category-view) hinzugefügt. (Sicherheitsbaselines befinden sich weiterhin in Preview). Die Ansicht für einzelne Kategorien zeigt jede Kategorie der Baseline mit dem Prozentsatz der Geräte an, die in jede Statusgruppe dieser Kategorie fallen. Sie können nun anzeigen, wie viele Geräte nicht mit den individuellen Kategorien übereinstimmen und falsch konfiguriert oder nicht anwendbar sind.

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Bereichsmarkierungen für Apple-VPP-Token <!--2371886  -->
Sie können nun Bereichsmarkierungen zu Apple-VPP-Token hinzufügen. Nur Benutzer, denen die gleiche Bereichsmarkierung zugewiesen ist, können auf das Apple-VPP-Token mit dieser Markierung zugreifen. VPP-Apps und E-Books, die mit diesem Token erworben werden, erben seine Bereichsmarkierungen. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Woche vom 1. April 2019

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Update für Zertifikatconnectors  <!-- ICM 113304612 -->
Wir haben Updates für den [Intune-Zertifikatconnector und den PFX-Zertifikatconnector für Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht. Mit diesen neuen Releases wurden einige bekannte Probleme behoben.  

### <a name="app-management"></a>App-Verwaltung

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Update für die Benutzeroberfläche für die Unternehmensportal-App für iOS <!-- 2536024 -->
Die Startseite der Unternehmensportal-App für iOS-Geräte wurde neu gestaltet. Sie entspricht nun mehr dem Muster der iOS-Benutzeroberfläche, und zudem können Apps und E-Books besser gefunden werden.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Änderungen der Unternehmensportal-Registrierung für Benutzer von iOS 12-Geräten <!--3448635 -->  
Die Anzeigen und Schritte bei der Registrierung im Unternehmensportal für iOS wurden aktualisiert und entsprechen nun den Änderungen der MDM-Registrierung, die mit Apple iOS 12.2 veröffentlicht wurden. Der aktualisierte Workflow fordert Benutzer zu Folgendem auf:  

* Zulassen, dass Safari die Unternehmensportal-Website öffnet, das Verwaltungsprofil herunterlädt und dann zur Unternehmensportal-App zurückkehrt.  
* Öffnen der App „Settings“ (Einstellungen), um das Verwaltungsprofil auf dem Gerät zu installieren.
* Rückkehr zur Unternehmensportal-App, um die Registrierung abzuschließen.  

Die aktualisierten Registrierungsschritte und -anzeigen finden Sie unter [Enroll iOS device in Intune (Registrieren eines iOS-Geräts in Intune)](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Woche vom 25. März 2019

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Unterstützung der Power BI-Compliance-App über das Data Warehouse-Blatt in Microsoft Intune <!-- 4260871 -->
Zuvor wurde mit dem Link **Power BI-Datei herunterladen** auf dem Blatt **Intune Data Warehouse** ein Intune Data Warehouse-Bericht heruntergeladen (PBIX-Datei). Dieser Bericht wurde nun durch die Power BI-Compliance-App ersetzt. Die Power BI-Compliance-App erfordert kein gesondertes Laden oder Setup. Sie wird direkt im Power BI-Onlineportal geöffnet und zeigt Daten spezifisch für Ihren Intune-Mandanten basierend auf Ihren Anmeldeinformationen an. Klicken Sie in Intune auf der rechten Seite des Intune-Blatts auf den Link **Intune Data Warehouse einrichten**. Klicken Sie dann auf **Power BI-App abrufen**. Weitere Informationen finden Sie unter [Connect to the Data Warehouse with Power BI (Verbinden von Data Warehouse mit Power BI)](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Woche vom 18. März 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Bereitstellen von Microsoft Visio und Microsoft Project <!-- 3725386  -->
Sie können nun Microsoft Visio Pro für Office 365 und den Microsoft Project Online-Desktopclient mithilfe von Microsoft Intune als unabhängige Apps auf Windows 10-Geräten bereitstellen, wenn Sie die Lizenzen für diese Apps besitzen. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen. Wählen Sie auf dem Blatt **App hinzufügen** den **App-Typ** **Windows 10** aus. Klicken Sie dann auf **App-Suite konfigurieren**, um zu installierende Apps auszuwählen. Weitere Informationen über Office 365-Apps für Windows 10-Geräte finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Änderung des Produktnamens von Microsoft Visio Pro für Office 365 <!-- 3593653  -->
**Microsoft Visio Pro für Office 365** heißt jetzt **Microsoft Visio Online Plan 2**.  Weitere Informationen zu Microsoft Visio finden Sie unter [Visio Online Plan 2](https://products.office.com/visio/visio-online-plan-2). Weitere Informationen über Office 365-Apps für Windows 10-Geräte finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Einstellung für die Zeichenbeschränkung für Intune-App-Schutzrichtlinien <!-- 3291302  -->
Intune-Administratoren können eine Ausnahme für die Intune-App-Richtlinieneinstellung zum **Einschränken des Ausschneidens, Kopierens und Einfügens bei anderen Apps** festlegen.  Als Administrator können Sie die Anzahl von Zeichen festlegen, die aus einer verwalteten App ausgeschnitten oder kopiert werden können. Mit dieser Einstellungen kann die festgelegte Zeichenanzahl, unabhängig von der Einstellung für das Einschränken von Ausschneiden, Kopieren und Einfügen bei anderen Apps, mit einer beliebigen App geteilt werden. Beachten Sie, dass die Version der Intune-Unternehmensportal-App für Android Version 5.0.4364.0 oder höher erfordert. Weitere Informationen finden Sie unter [iOS-Datenschutz](app-protection-policy-settings-ios.md#data-protection), [Android-Datenschutz](app-protection-policy-settings-android.md#data-protection) und [Überprüfen der Schutzprotokolle für Client-Apps](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Office-Bereitstellungstool-XML für die Bereitstellung von Office ProPlus <!-- 3192477   -->
Sie können das Office-Bereitstellungstool-XML bereitstellen, wenn Sie eine Instanz von Office ProPlus in der Intune-Verwaltungskonsole erstellen. Dadurch wird die Anpassbarkeit erweitert, wenn die vorhandenen Benutzeroberflächenoptionen von Intune nicht Ihre Anforderungen erfüllen. Weitere Informationen finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) und [Konfigurationsoptionen für das Office-Bereitstellungstool](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>App-Symbole werden nun mit einem automatisch generierten Hintergrund angezeigt <!-- 1429026  -->
App-Symbole werden nun in der Windows-Unternehmensportal-App mit einem automatisch generierten Hintergrund basierend auf der dominanten Farbe des Symbols angezeigt (sofern diese ermittelt werden kann). Wenn möglich, ersetzt dieser Hintergrund den grauen Rahmen, der zuvor auf App-Kacheln sichtbar war. Diese Änderung wird ab Version 10.3.3451.0 des Unternehmensportals angezeigt.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installieren verfügbarer Apps mithilfe der Unternehmensportal-App nach der Windows-Massenregistrierung <!-- 2751523   -->
Windows-Geräte, die mit der [Windows-Massenregistrierung](windows-bulk-enroll.md) (Bereitstellungspakete) in Intune registriert wurden, können die Unternehmensportal-App nutzen, um verfügbare Apps zu installieren. Weitere Informationen über die Unternehmensportal-App finden Sie unter [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](store-apps-company-portal-app.md) und [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

> [!Note]
> Dieses Feature ist noch nicht für alle Kunden vollständig bereitgestellt. Wenn Sie das Unternehmensportal nicht auf Geräten verwenden können, die mit der Massenregistrierung registriert wurden, müssen Sie möglicherweise darauf warten, dass diese Änderung für Ihr Konto bereitgestellt wird.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Die Microsoft Teams-App kann als Teil der Office-App-Suite ausgewählt werden <!-- 3828932  -->
Die Microsoft Teams-App kann als Teil der Office ProPlus-App-Suite enthalten oder ausgeschlossen werden. Dieses Feature funktioniert ab Buildnummer 16.0.11328.20116 von Office ProPlus. Der Benutzer muss sich vom Gerät abmelden und neu anmelden, damit die Installation abgeschlossen werden kann. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie einen **Office 365 Suite**-App-Typ aus, und klicken Sie dann auf **App-Suite konfigurieren**.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Automatisches Starten einer App, wenn mehrere Apps auf Geräten mit Windows 10 oder höher im Kioskmodus ausgeführt werden <!-- 2351390 -->

Auf Geräten mit Windows 10 und höher können Sie viele Apps im Kioskmodus ausführen. Dieses Update umfasst eine **AutoLaunch**-Einstellung (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Kiosk** (Profiltyp) > **Multi-App-Kiosk**). Verwenden Sie diese Einstellung, um eine App automatisch zu starten, wenn der Benutzer sich auf dem Gerät anmeldet.

Eine Liste und Beschreibungen aller Kioskeinstellungen finden Sie unter [Windows 10 and later device settings to run as a kiosk in Intune (Geräteeinstellungen unter Windows 10 und höher für die Ausführung als Kiosk in Intune)](kiosk-settings-windows.md).

Gilt für: Windows 10 und höher

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Betriebsprotokolle enthalten Details zu nicht konformen Geräten <!-- 4063755  -->
Beim Weiterleiten von Intune-Protokollen an Azure-Überwachungsfeatures können Sie auch Betriebsprotokolle weiterleiten. In diesem Update stellen Betriebsprotokolle auch Informationen zu nicht konformen Geräten bereit. 

Weitere Informationen zu diesem Feature finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Weiterleiten von Protokollen an Azure Monitor in mehreren Intune-Workloads <!-- 3804627 -->
In Intune können Sie Überwachungs- und Betriebsprotokolle an Event Hubs, Speicher und Log Analytics in Azure Monitor weiterleiten (**Intune** > **Überwachung** > **Diagnoseeinstellungen**). In diesem Update können Sie diese Protokolle in mehreren Intune-Workloads weiterleiten, einschließlich Konformität, Konfigurationen, Client-Apps und mehr. 

Weitere Informationen zum Weiterleiten von Protokollen an Azure Monitor finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Erstellen und Verwenden von Mobility Extensions für Android Zebra-Geräte in Intune <!-- 3305880   -->
Mit diesem Update unterstützt Intune die Konfiguration von Android Zebra-Geräten. Das heißt, Sie können ein Gerätekonfigurationsprofil erstellen und Einstellungen mithilfe von mit StageNow generierten MX-Profilen (Mobility Extensions) auf Android Zebra-Geräte anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android** (Plattform) > **MX-Profil (nur Zebra)** (Profiltyp)).

Weitere Informationen zu diesem Feature finden Sie unter [Use and manage Zebra devices with mobility extensions in Intune (Verwenden und Verwalten von Zebra-Geräten mit Mobility Extensions in Intune)](android-zebra-mx-overview.md).

Gilt für: Android

### <a name="device-management"></a>Geräteverwaltung

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Verschlüsselungsbericht für Windows 10-Geräte (Public Preview)<!-- 2351538 -->  
Verwenden Sie den neuen [Verschlüsselungsbericht (Vorschau)](encryption-monitor.md), um Details zum Verschlüsselungsstatus Ihrer Windows 10-Geräte anzuzeigen. Die verfügbaren Details umfassen die TPM-Version des Geräts, die Verschlüsselungsbereitschaft und den -status, die Fehlerberichterstattung und mehr.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Zugriff auf BitLocker-Wiederherstellungsschlüssel über das Intune-Portal (Public Preview) <!-- 2351547   -->  
Sie können nun Intune zum [Anzeigen von Details](encryption-monitor.md) zur BitLocker-Schlüssel-ID und den BitLocker-Wiederherstellungsschlüsseln in Azure Active Directory verwenden.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-Unterstützung für Intune-Szenarios auf iOS- und Android-Geräten <!-- 3411007 -->
Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser unterstützt, und enthält Verbesserungen für die Benutzerfreundlichkeit. Zu den von Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures gehören doppelte Identitäten, die Integration von App-Schutzrichtlinien, die Integration von Azure-Anwendungsproxys sowie verwaltete Favoriten und Verknüpfungen auf der Startseite. Weitere Informationen finden Sie unter [Microsoft Edge support (Microsoft Edge-Unterstützung)](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune-Connector unterstützen Geräte mit nur Exchange Active Sync nicht mehr <!--3105122  -->
Die Intune-Konsole unterstützt das Anzeigen und Verwalten von Geräten mit nur EAS, die über den Intune-Connector mit Exchange Online verbunden sind, nicht mehr. Stattdessen stehen Ihnen folgende Optionen zur Verfügung:
- Registrieren von Geräten in der mobilen Geräteverwaltung (Mobile Device Management, MDM)
- Verwenden von App-Schutzrichtlinien zum Verwalten Ihrer Geräte
- Verwenden von Exchange-Steuerelementen gemäß den Anweisungen unter [Clients and mobile in Exchange Online (Clients und Mobilgeräte in Exchange Online)](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Suchen eines bestimmten Geräts auf der Seite „Alle Geräte“ mithilfe von [Name] <!--4254930 -->
Sie können nun nach exakten Gerätenamen suchen. Wechseln Sie zu **Intune** > **Geräte** > **Alle Geräte**, und umschließen Sie den gesuchten Gerätenamen im Suchfeld mit {}, um nach einer genauen Übereinstimmung zu suchen. Zum Beispiel: **{Gerät12345}** .

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Unterstützung für zusätzliche Connectors auf der Seite „Mandantenstatus“ <!-- 3617202  -->
Auf der [Mandantenstatusseite](tenant-status.md) werden nun Statusinformationen zu zusätzlichen Connectors, einschließlich *Windows Defender Advanced Threat Protection* (ATP) und anderen Mobile Threat Defense-Connectors, angezeigt.

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Gewähren des schreibgeschützten Zugriffs auf Intune für einige Azure Active Directory-Rollen <!-- 3637917  -->
Der schreibgeschützte Zugriff auf Intune wurde den folgenden Azure AD-Rollen gewährt. Berechtigungen, die mit Azure AD-Rollen gewährt werden, haben Vorrang vor der rollenbasierten Zugriffssteuerung von Intune.

Schreibgeschützter Zugriff auf Intune-Überwachungsdaten:

- Complianceadministrator
- Administrator für Konformitätsdaten

Schreibgeschützter Zugriff auf alle Intune-Daten:

- Sicherheitsadministrator
- Sicherheitsoperator
- Sicherheitsleseberechtigter

Weitere Informationen finden Sie unter [Rollenbasierte Zugriffssteuerung mit Microsoft Intune](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Bereichsmarkierungen für iOS-App-Bereitstellungsprofile <!--2934430   -->
Sie können einem iOS-App-Bereitstellungsprofil eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie das iOS-App-Bereitstellungsprofil auf diese zugreifen können. Weitere Informationen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Bereichsmarkierungen für App-Konfigurationsrichtlinien <!--2371891   -->
Sie können einer App-Konfigurationsrichtlinie eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie die App-Konfigurationsrichtlinie auf diese zugreifen können. Die App-Konfigurationsrichtlinie kann nur den Apps zugeordnet werden, denen dieselben Bereichsmarkierungen zugewiesen sind. Weitere Informationen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-Unterstützung für Intune-Szenarios auf iOS- und Android-Geräten <!-- 3411007 -->
Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser unterstützt, und enthält Verbesserungen für die Benutzerfreundlichkeit. Zu den von Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures gehören doppelte Identitäten, die Integration von App-Schutzrichtlinien, die Integration von Azure-Anwendungsproxys sowie verwaltete Favoriten und Verknüpfungen auf der Startseite. Weitere Informationen finden Sie unter [Microsoft Edge support (Microsoft Edge-Unterstützung)](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Woche vom 25. Februar 2019

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell-Modul <!-- 951068  -->
Das Intune PowerShell-Modul, das Unterstützung für die Intune-API über Microsoft Graph bereitstellt, ist jetzt im [PowerShell-Katalog](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10) verfügbar.

- [Informationen zur Verwendung dieses Moduls](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Beispielszenarios für die Verwendung dieses Moduls](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Verbesserte Unterstützung für die Übermittlungsoptimierung  <!--3183757  -->
Die Unterstützung für die Konfiguration der Übermittlungsoptimierung in Intune wurde erweitert. Sie können nun eine erweiterte Liste von [Einstellungen für die Übermittlungsoptimierung](delivery-optimization-settings.md) konfigurieren und direkt über die Intune-Konsole auf Ihre Geräte abstimmen.


## <a name="week-of-february-18-2019"></a>Woche vom 18. Februar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Verwendung von Google Play Protect-APIs für Android-Geräte in Intune <!-- 2577355   -->
Manche IT-Administratoren arbeiten in einer Bring Your Own Device-Umgebung (BYOD), in der manche Endbenutzer ihre Mobiltelefone möglicherweise rooten oder jailbreaken. Viele Benutzer handeln zwar nicht in schlechter Absicht, dennoch kann dieses Verhalten dazu führen, dass viele Intune-Richtlinien umgangen werden, die zum Schutz der Organisationsdaten auf dem Gerät des Endbenutzers eingerichtet wurden. Deshalb enthält Intune eine Erkennung von Rooting und Jailbreaks für registrierte und nicht registrierte Geräte. Ab diesem Release verwendet Intune die Google Play Protect-APIs, um die bisherigen Überprüfungen auf Rooting für nicht registrierte Geräte zu ergänzen. Google stellt zwar nicht alle Überprüfungsmechanismen für Rooting zur Verfügung, aber diese APIs sollten dennoch Benutzer ermitteln können, die Ihre Geräte abweichend von der Gerätekonfiguration gerootet haben, um neuere Betriebssystemupdates für ältere Geräte zu erhalten. Diesen Benutzern kann der Zugriff auf Unternehmensdaten verwehrt werden, oder ihre Unternehmenskonten können aus den Apps entfernt werden, für die Richtlinien aktiviert sind. Es wurden zudem einige Updates für die Berichterstellung auf dem Blatt „Intune-App-Schutz“ vorgenommen, um IT-Administratoren die Arbeit zu erleichtern: Der Bericht „Gekennzeichnete Benutzer“ enthält die Benutzer, die durch eine Überprüfung mit der SafetyNet-API von Google Play Protect ermittelt wurden, und der Bericht „Potentially Harmful Apps“ (Potenziell schädliche Apps) enthält die Apps, die durch eine Überprüfung mit der Verify Apps-API von Google ermittelt wurden. Dieses Feature ist unter Android verfügbar.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informationen zu Win32-Apps auf dem Blatt „Problembehandlung“ <!-- 2617342   -->
Sie können nun Protokolldateien zu Fehlern bei der Installation von Win32-Apps über das Blatt **Problembehandlung** der Intune-App abrufen. Weitere Informationen zur Behandlung von Problemen mit der App-Installation finden Sie unter [Troubleshoot app installation issues (Problembehandlung bei der App-Installation)](troubleshoot-app-install.md) und [Behandeln von Win32-App-Problemen](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Details zum Status von iOS-Apps <!-- 3761235   -->
Es wurden neue Fehlermeldungen eingeführt, die bei folgenden Problemen bei der Installation von Apps ausgelöst werden:
- Fehler beim Installieren von VPP-Apps auf gemeinsam genutzten iPads
- Fehler bei deaktiviertem App Store
- Fehler beim Suchen von VPP-Lizenzen für Apps
- Fehler beim Installieren von System-Apps mit MDM-Anbietern
- Fehler beim Installieren von Apps, wenn das Gerät sich im Kioskmodus oder im Modus für verlorene Geräte befindet
- Fehler beim Installieren von Apps wenn der Benutzer nicht im App Store angemeldet ist

Navigieren Sie in Intune zu **Client-Apps** > **Apps** > Name der App > **Geräteinstallationsstatus**. Die neuen Fehlermeldungen werden in der Spalte **Statusdetails** angezeigt.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Neue Anzeige „App-Kategorien“ in der Unternehmensportal-App für Windows 10<!-- 3834780  -->
Eine neue Anzeige namens **App-Kategorien** wurde hinzugefügt, um das Durchsuchen und Auswählen von Apps im Unternehmensportal für Windows 10 zu verbessern. Für Benutzer werden Apps nun sortiert nach Kategorien wie **Empfohlen**, **Bildung** und **Produktivität** angezeigt. Diese Änderung ist im Unternehmensportal ab Version 10.3.3451.0 vorhanden. Informationen zu dieser neuen Anzeige finden Sie unter [Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune](https://docs.microsoft.com/intune/whats-new-app-ui). Weitere Informationen zu den Apps im Unternehmensportal finden Sie unter [Install and share apps on your device (Installieren und Freigeben von Apps auf Ihrem Gerät)](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI-Compliance-App <!-- 1455231 doc-work-item -->
Sie können über die App [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) in Power BI auf Ihre Intune Data Warehouse-Instanz zugreifen. Mit dieser Power BI-App können Sie nun auf vorab erstellte Berichte zugreifen und diese freigeben, ohne dafür ein Setup durchzuführen und ohne Ihren Webbrowser zu verlassen. Weitere Informationen finden Sie im [Änderungsprotokoll für die Intune Data Warehouse-API](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Ausführung von PowerShell-Skripts auf einem 64-Bit-Host auf 64-Bit-Geräten <!-- 1862675   -->
Wenn Sie ein PowerShell-Skript zu einem Gerätekonfigurationsprofil hinzufügen, wird das Skript immer im 32-Bit-Modus ausgeführt, auch auf einem 64-Bit-Betriebssystem. Seit diesem Update kann ein Administrator das Skript auf einem 64-Bit-Gerät auf einem 64-Bit-Host von PowerShell ausführen (**Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen** > **Konfigurieren** > **Skript in 64-Bit-PowerShell-Host ausführen**).

Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte](intune-management-extension.md).

Gilt für: Windows 10 und höher

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS-Benutzer werden aufgefordert, ihr Kennwort zu aktualisieren <!-- 1873216 -->
Intune erzwingt die Einstellung **ChangeAtNextAuth** für macOS-Geräte. Diese Einstellung wirkt sich auf Benutzer und Geräte aus, die über Konformitätskennwortrichtlinien oder Geräteeinschränkungsprofile für Kennwörter verfügen. Benutzer werden einmal aufgefordert, ihr Kennwort zu aktualisieren. Diese Aufforderung wird angezeigt, wenn ein Benutzer zum ersten Mal eine Aufgabe ausführt, für die Authentifizierung erforderlich ist, z. B. die Anmeldung auf dem Gerät. Benutzer können ebenfalls dazu aufgefordert werden, ihre Kennwörter zu aktualisieren, wenn sie etwas tun, für das Administratorberechtigungen erforderlich sind, z. B. das Anfordern des Keychain-Zugriffs. 

Auch bei Änderungen an neuen oder vorhandenen Kennwortrichtlinien durch den Administrator werden Benutzer dazu aufgefordert, ihre Kennwörter zu aktualisieren.

Gilt für:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>Zuweisen von SCEP-Zertifikaten zu einem macOS-Gerät ohne Benutzer  <!-- 2340521  -->
Sie können SCEP-Zertifikate (Simple Certificate Enrollment-Protokoll) mit Geräteattributen zu macOS-Geräten hinzufügen (dies gilt auch für Geräte ohne Benutzeraffinität) und die Zertifikatprofile zu WLAN- oder VPN-Profilen zuordnen. Dadurch wird die bereits vorhandene Unterstützung erweitert, sodass [SCEP-Zertifikate zu Geräten mit und ohne Benutzeraffinität zugewiesen werden können](certificates-scep-configure.md#create-a-scep-certificate-profile), auf denen Windows, iOS oder Android ausgeführt wird.  Mit diesem Update wurde die Option hinzugefügt, den Zertifikattyp *Gerät* beim Konfigurieren eines SCEP-Zertifikatprofils für macOS auszuwählen.

Gilt für: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Update der Intune-Benutzeroberfläche für den bedingten Zugriff   <!-- 2432313   -->
Die Benutzeroberfläche für den bedingten Zugriff über die Intune-Konsole wurde verbessert. Dazu gehören:
-  Das Intune-Blatt *Bedingter Zugriff* wurde durch das entsprechende Blatt aus Azure Active Directory ersetzt. Dadurch wird sichergestellt, dass Sie alle Einstellungen und Konfigurationen für den [bedingten Zugriff](conditional-access.md) (eine Technologie von Azure AD) innerhalb der Intune-Konsole nutzen können. 
- Das Blatt *Lokaler Zugriff* wurde in *Exchange-Zugriff* umbenannt, und das Setup für den *Exchange-Dienstconnector* wurde auf dieses Blatt verschoben.  Dadurch ändert sich der Ort, an dem Sie [Details zu Exchange (online und lokal) konfigurieren und überwachen](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Ausführung von Kioskbrowsern und Microsoft Edge-Browser-Apps auf Windows 10-Geräten im Kioskmodus <!-- 2935135   -->
Sie können Windows 10-Geräte im Kioskmodus verwenden, um eine oder mehrere Apps auszuführen. Durch dieses Update wurden unter anderem folgende Änderungen an der Verwendung von Browser-Apps im Kioskmodus vorgenommen:

- Der Microsoft Edge-Browser und der Kioskbrowser können nun als ausführbare Apps zu Kioskgeräten hinzugefügt werden (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) bzw. **Kiosk** (Profiltyp)).
- Es stehen neue Features und Einstellungen zum Zulassen oder Gewähren zur Verfügung (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp)), einschließlich:

  - Microsoft Edge-Browser:
  - Verwenden des Microsoft Edge-Kioskmodus
  - Aktualisieren des Browsers nach einer Leerlaufzeit

 - Favoriten und Suche:
  - Zulassen von Änderungen an der Suchmaschine

Eine Liste dieser Einstellungen finden Sie unter:

- [Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als Kiosk in Intune](kiosk-settings-windows.md)
- [Microsoft Edge-Browser](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](device-restrictions-windows-10.md##favorites-and-search)

Gilt für: Windows 10 und höher

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Neue Einstellungen für Einschränkungen für iOS- und macOS-Geräte <!-- 3448774   -->
Sie können einige Einstellungen und Features auf iOS- und macOS-Geräten einschränken (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** bzw. **macOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Mit diesem Update werden weitere Features und Einstellungen hinzugefügt, die Sie steuern können. Sie können auf iOS-Geräten beispielsweise die Bildschirmzeit festlegen, eSIM-Einstellungen und Mobilfunktarife ändern und mehr. Außerdem können Sie Softwareupdates später für Benutzer bereitstellen oder das Content Caching auf macOS-Geräten blockieren. 

Weitere Informationen zu den einschränkbaren Features und Einstellungen finden Sie unter:

- [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md)
- [Einstellungen für Geräteeinschränkungen für macOS-Geräte in Microsoft Intune](device-restrictions-macos.md)

Gilt für:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>„Kioskgeräte“ heißen bei Android Enterprise-Geräten jetzt „Dedizierte Geräte“ <!-- 3598402   -->
Zur Anpassung an die Android-Terminologie wurde **Kiosk** für Android Enterprise-Geräte in **dedizierte Geräte** umbenannt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer** > **Geräteeinschränkungen** > **Dedizierte Geräte**).

Eine Liste der verfügbaren Einstellungen finden Sie unter [Device settings to allow or restrict features (Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-android-for-work.md#dedicated-device-settings).

Gilt für:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Verschiebung der iOS-Einstellungen von Safari und zum Verzögern der Sichtbarkeit von Updates für Benutzer auf der Benutzeroberfläche von Intune <!-- 3640850, 3803313   -->
Für iOS-Geräte können Sie Safari-Einstellungen festlegen und Softwareupdates konfigurieren. Mit diesem Update werden diese Einstellungen auf der Intune-Benutzeroberfläche verschoben:

- Die Safari-Einstellungen wurden von **Safari** (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)) zu **[Integrierte Apps](device-restrictions-ios.md#built-in-apps)** verschoben.
- Die Einstellung **Delaying user software update visibility for supervised iOS devices** (Sichtbarkeit von Updates für Benutzer von überwachten iOS-Geräten verzögern) (**Softwareupdates** > **Richtlinien für iOS aktualisieren**) wurde zu **Geräteeinschränkungen** >  **[Allgemein](device-restrictions-ios.md#general)** verschoben.  Weitere Informationen zu den Auswirkungen auf vorhandene Richtlinien finden Sie unter [Konfigurieren von iOS-Updaterichtlinien in Intune](software-updates-ios.md#configure-the-policy). 

Eine Liste der Einstellungen finden Sie unter:

- [iOS-Geräteeinschränkungen](device-restrictions-ios.md) 
- [iOS-Softwareupdates](software-updates-ios.md)

Diese Funktion gilt für: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Umbenennung von „Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)“ auf iOS-Geräten in „Bildschirmzeit“ <!-- 3699164   -->
Sie können die Einstellung **Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)** für überwachte iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Allgemein**) konfigurieren. Mit diesem Update wurde die Einstellung in **Bildschirmzeit (nur überwacht)** umbenannt. 

Das Verhalten ändert sich nicht. Genauer gesagt: 

- iOS 11.4.1 und früher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltenden Einschränkungen in den Geräteeinstellungen bearbeiten. 
- iOS 12.0 und höher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltende **Bildschirmzeit** (einschließlich Einschränkungen von Inhalt und Datenschutz) in den Geräteeinstellungen bearbeiten. Auf Geräten, auf denen mindestens iOS 12.0 ausgeführt wird, wird die Registerkarte „Einschränkungen“ in den Geräteeinstellungen nicht mehr angezeigt. Diese Einstellungen befinden sich unter **Bildschirmzeit**. 

Eine Liste der Einstellungen finden Sie in den [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#general).

Gilt für: 
- iOS


### <a name="device-management"></a>Geräteverwaltung

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Umbenennen eines registrierten Windows-Geräts <!-- 1911112  -->
Sie können registrierte Windows 10-Geräte (RS4 oder höher) jetzt umbenennen. Navigieren Sie hierfür zu **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Gerät umbenennen**. Dieses Feature unterstützt derzeit nicht das Umbenennen von Windows-Geräten mit Azure AD Hybrid.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Automatische Zuweisung von Bereichsmarkierungen zu Ressourcen, die von einem Administrator für diesen Bereich erstellt wurden <!-- 3173823  -->
Wenn ein Administrator eine Ressource erstellt, werden alle Bereichstags, die dem Administrator zugewiesen sind, automatisch auch den neuen Ressourcen zugewiesen.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Bericht für fehlgeschlagene Registrierungen wurde auf das Blatt „Geräteregistrierung“ verschoben <!-- 3560202  -->
Der Bericht zu **fehlgeschlagenen Registrierungen** wurde in den Abschnitt **Überwachen** des Blatts **Geräteregistrierung** verschoben. Zwei neue Spalten („Registrierungsmethode“ und „Betriebssystemversion“) wurden hinzugefügt.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Umbenennung des Berichts „Unternehmensportalabbruch“ in „Unvollständige Benutzerregistrierungen“ <!--3815076 eemiss -->
Der Bericht **Unternehmensportalabbruch** wurde in **Unvollständige Benutzerregistrierungen** umbenannt.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Woche vom 4. Februar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Dunkler Modus für Intune-Unternehmensportal für macOS <!-- 3300524  -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Unternehmensportal an die Farben dieses Modus angepasst.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Woche vom 21. Januar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Popupbenachrichtigungen für Win32-Apps <!-- 3136566   -->
Sie können die Anzeige von Popupbenachrichtigungen für die Benutzer pro App-Zuweisung unterdrücken. Wählen Sie in Intune **Client-Apps** > **Apps** > App-Auswahl > **Zuweisungen** > **Gruppen einschließen**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Update der Benutzeroberfläche für Intune-App-Schutzrichtlinien <!-- 3251427  -->
Wir haben die Bezeichnungen für Einstellungen und Schaltflächen für den Intune-App-Schutz geändert, um die Verständlichkeit zu erleichtern. Einige Änderungen sind:  
- Die Steuerelemente **Ja** / **Nein** wurden in erster Linie in die Steuerelemente **Blockieren** / **Zulassen** und **Deaktivieren** / **Aktivieren** geändert. Die Bezeichnungen wurden ebenfalls aktualisiert.  
- Einstellungen wurden darüber hinaus neu formatiert, um die Einstellungen und ihre Bezeichnungen im Steuerelement nebeneinander anzuzeigen und eine bessere Navigation zu ermöglichen.   

Die Standardeinstellungen und die Anzahl von Einstellungen bleiben gleich, aber durch die oben genannten Änderungen werden Verständlichkeit, Navigation und Verwendung der Einstellungen verbessert, um dem Benutzer eine einfachere Anwendung der ausgewählten App-Schutzrichtlinien zu ermöglichen. Weitere Informationen finden Sie unter [iOS-Einstellungen](app-protection-policy-settings-ios.md) und [Android-Einstellungen](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Zusätzliche Einstellungen für Outlook <!-- 3301182  -->
Sie können nun die folgenden zusätzlichen Einstellungen für Outlook für iOS und Android mit Intune konfigurieren:

- Lassen Sie nur die Verwendung von Geschäfts-, Schul- oder Unikonten in Outlook in iOS und Android zu.
- Stellen sie eine moderne Authentifizierung für Office 365 und eine hybride moderne Authentifizierung für lokale Konten bereit.
- Verwenden Sie `SAMAccountName` für das Feld „Benutzername“ im E-Mail-Profil, wenn die Basisauthentifizierung aktiviert ist.
- Ermöglichen Sie das Speichern von Kontakten.
- Konfigurieren von E-Mail-Infos externer Empfänger
- Konfigurieren Sie **Posteingang mit Relevanz**.
- Erfordern Sie biometrische Daten für den Zugriff auf Outlook für iOS.
- Blockieren Sie externe Bilder.

> [!NOTE]
> Wenn Sie die Richtlinien für den Intune-App-Schutz zur Verwaltung des Zugriffs auf Unternehmensidentitäten verwenden, sollten Sie ggf. nicht aktivieren, dass **biometrische Daten erforderlich** sind. Weitere Informationen finden Sie unter **Unternehmensanmeldeinformationen für Zugriff erforderlich** für [iOS-Zugriffseinstellungen](app-protection-policy-settings-ios.md#access-requirements) und [Android-Zugriffseinstellungen](app-protection-policy-settings-android.md#access-requirements).

Weitere Informationen finden Sie unter [Microsoft Outlook-Konfigurationseinstellungen](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Löschen von Android Enterprise-Apps <!-- 1352553 -->
Sie können verwaltete Google Play-Apps aus Microsoft Intune löschen. Um eine verwaltete Google Play-App zu löschen, öffnen Sie Microsoft Intune im Azure-Portal und wählen **Client-Apps** > **Apps** aus. Klicken Sie in der App-Liste auf die Auslassungspunkte (...) rechts neben der verwalteten Google Play-App, und wählen Sie dann in der angezeigten Liste die Option **Löschen** aus. Wenn Sie eine verwaltete Google Play-App aus der App-Liste löschen, wird die Genehmigung für die Google Play-App automatisch aufgehoben.

#### <a name="managed-google-play-app-type----1352580---"></a>App-Typ „Verwaltetes Google Play“ <!-- 1352580 -->
Der App-Typ **Verwaltetes Google Play** ermöglicht es Ihnen, [verwaltete Google Play-Apps](https://play.google.com/work/search?q=microsoft&c=apps) gezielt zu Intune hinzuzufügen. Als Intune-Administrator können Sie verwaltete Google Play-Apps ab sofort in Intune suchen, genehmigen, synchronisieren und genehmigte verwaltete Google Play-Anwendungen zuweisen.  Sie müssen nicht mehr separat zur verwalteten Google Play-Konsole navigieren, und es ist keine erneute Authentifizierung mehr erforderlich.  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie in der Liste **App-Typ** als App-Typ **Verwaltetes Google Play** aus.

### <a name="default-android-pin-keyboard----3802457---"></a>Android-Standardtastatur für die PIN <!-- 3802457 -->
Endbenutzer, die eine Intune-App-Schutzrichtlinien-PIN auf ihren Android-Geräten vom Typ „Numerisch“ festgelegt haben, wird nun die Android-Standardtastatur anstelle der zuvor entworfenen, festen Android-Tastaturbenutzeroberfläche angezeigt. Diese Änderung wurde implementiert, damit die Standardtastaturen für die PIN-Typen „Numerisch“ und/oder „Passcode“ auf Android- und iOS-Geräten konsistent sind. Weitere Informationen über die Zugriffseinstellungen für Endbenutzer unter Android, z.B. APP-PIN, finden Sie unter [Android-Zugriffsanforderungen](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines (Public Preview) <!-- 2055484   -->

Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

Dieses Feature befindet sich in der Public Preview, d.h. Profile, die in dieser Version erstellt werden, werden nicht in die allgemein verfügbaren Vorlagen für Sicherheitsbaselines übernommen. Es wird davon abgeraten, diese Preview-Vorlagen in Produktionsumgebungen zu verwenden.

Weitere Informationen zu Sicherheitsbaselines finden Sie unter [Erstellen einer Windows 10-Sicherheitsbaseline in Intune](security-baselines-monitor.md).

Diese Funktion gilt für: Windows 10 und höher

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Nicht-Administratoren können BitLocker auf Windows 10-Geräten aktivieren, die in Azure AD eingebunden sind<!-- 2147379   -->
Beim Aktivieren der BitLocker-Einstellungen auf Windows 10-Geräten (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** als Plattform > **Endpunktschutz** als Profiltyp > **Windows-Verschlüsselung**) fügen Sie BitLocker-Einstellungen hinzu. 

Dieses Update enthält eine neue BitLocker-Einstellung, um Standardbenutzern (Nicht-Administratoren), die Verschlüsselung zu ermöglichen. 

Diese Einstellungen finden Sie unter [Endpunktschutzeinstellungen für Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Überprüfen der Konformität von Configuration Manager <!-- 2192052  eepublished  -->
Dieses Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10 und höher** > **Configuration Manager-Konformität**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über diese Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

[Configuration Manager-Konformität](compliance-policy-create-windows.md#configuration-manager-compliance) beschreibt diese Einstellung.

Gilt für: Windows 10 und höher

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Anpassen des Hintergrundbilds auf überwachten iOS-Geräten mithilfe eines Gerätekonfigurationsprofils <!-- 2809324   -->
Wenn Sie ein Gerätekonfigurationsprofil für iOS-Geräte erstellen, können Sie einige Features in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für die Plattform > **Gerätefeatures** anpassen. Dieses Update enthält neue **Hintergrundbildeinstellungen**, die es einem Administrator ermöglichen, ein.png-,.jpg- oder.jpeg-Bild auf dem Startbildschirm oder Sperrbildschirm zu verwenden. Die Einstellungen für das Hintergrundbild gelten nur für überwachte Geräte. 

Eine Liste dieser Einstellungen finden Sie [iOS-Einstellungen für Gerätefeatures](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10-Kiosk ist allgemein verfügbar <!-- 3594661  -->
In diesem Update wird das Kiosk-Feature auf Windows 10 und höher allgemein verfügbar (GA) gemacht. Alle Einstellungen, die Sie hinzufügen und konfigurieren können, finden Sie unter [Kioskeinstellungen für Windows 10 (und höher)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Die Kontaktfreigabe über Bluetooth in „Geräteeinschränkungen“ > „Gerätebesitzer für Android Enterprise“ wurde entfernt <!-- 3598396   -->
Wenn Sie ein Geräteeinschränkungsprofil für Android Enterprise-Geräte erstellen, gibt es die Einstellung **Kontaktfreigabe über Bluetooth**. In diesem Update wird die Einstellung **Kontaktfreigabe über Bluetooth** entfernt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen > Gerätebesitzer** für Profiltyp > **Allgemein**). 

Die Einstellung **Kontaktfreigabe über Bluetooth** wird für die Verwaltung von Android Enterprise-Gerätebesitzern nicht unterstützt. Die Entfernung dieser Einstellung hat deshalb keine Auswirkungen auf Geräte oder Mandanten – selbst dann, wenn diese Einstellung in Ihrer Umgebung aktiviert und konfiguriert ist.

Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](device-restrictions-android-for-work.md).

Gilt für: Android Enterprise-Gerätebesitzer

### <a name="device-management"></a>Geräteverwaltung

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Unterstützung für selektives Zurücksetzen für WIP-Geräte ohne Registrierung <!-- 1434452 -->
Windows Information Protection Without Enrollment (WIP-WE) ermöglicht es Kunden, ihre Unternehmensdaten auf Windows 10-Geräten zu schützen, ohne dass eine vollständige MDM-Registrierung erforderlich ist. Sobald Dokumente durch eine WIP-WE-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-WE-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Mobile App** > **Selektive App-Zurücksetzung** aus.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Neue Betriebsprotokolle und Möglichkeit zum Senden von Protokollen an Azure Monitor-Dienste <!-- 3762211  -->
Intune bietet ein integrierte Überwachungsprotokollierung, die Ereignisse bei Änderungen verfolgt. Dieses Update enthält neue Protokollierungsfeatures, darunter: 
- Betriebsprotokolle (Vorschau), die Details für Benutzer und Geräte anzeigen, die registriert sind, einschließlich der erfolgreichen und fehlerhaften Versuche.
- Die Überwachungs- und Betriebsprotokolle können an Azure Monitor gesendet werden, einschließlich Speicherkonten, Event Hubs und Log Analytics. Diese Dienste ermöglichen es Ihnen, Analysen wie Splunk und QRadar zu speichern, zu nutzen und Visualisierungen Ihrer Protokolldaten zu erhalten.

In [Senden von Daten an den Speicher, Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md) finden Sie weitere Informationen zu diesem Feature.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Überspringen weiterer Setup-Assistent-Anzeigen auf einem iOS-DEP-Gerät <!-- 2687509  -->
Zusätzlich zu den Bildschirmanzeigen, die derzeit übersprungen werden können, können Sie festlegen, dass iOS-DEP-Geräte die folgenden Anzeigen im Setup-Assistenten überspringen, wenn ein Benutzer das Gerät registriert: Displayton, Privatsphäre, Android-Migration, Startschaltfläche, iMessage & FaceTime, Onboarding, Watch-Migration, Darstellung, Bildschirmzeit, Softwareupdate und SIM-Setup.
Um die zu überspringenden Bildschirme auszuwählen, wechseln Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, wählen Sie das Token und unter **Profile** das Profil aus, wählen Sie **Eigenschaften** > **Anpassung des Setup-Assistenten** und **Ausblenden**  für alle Bildschirme aus, die Sie überspringen möchten, und wählen Sie **OK** aus.
Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden. Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung <!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie jetzt verwaltetes Google Play zum Bereitstellen von Store-Apps und branchenspezifischen Apps für Benutzer verwenden. Insbesondere können Sie Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte kompromittieren müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Woche vom 14. Januar 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Vorschau der Unterstützung für vollständig verwaltete Android-Unternehmensgeräte <!-- 1574342  -->
Intune unterstützt jetzt vollständig verwaltete Android-Geräte in einem „Gerätebesitzer“-Szenario, in dem das Unternehmen Besitzer ist und die Geräte konsequent von der IT-Abteilung verwaltet und einzelnen Benutzern zugewiesen werden. So können Administratoren das gesamte Gerät verwalten, einen erweiterten Bereich von Richtlinienkontrollen erzwingen, die Arbeitsprofilen nicht zur Verfügung stehen, und Benutzer werden derart eingeschränkt, dass sie nur Apps von verwaltetem Google Play installieren können. Weitere Informationen finden Sie unter [Einrichten der Intune-Registrierung von vollständig verwalteten Android-Geräten](android-fully-managed-enroll.md) und [Registrieren Ihrer dedizierten Geräte oder vollständig verwalteten Geräte](android-dedicated-devices-fully-managed-enroll.md).  Hinweis: Dieses Feature befindet sich in der Vorschau. Einige Intune-Funktionen, wie z.B. Zertifikate, Konformität und bedingter Zugriff, stehen momentan für vollständig verwaltete Android-Benutzergeräte nicht zur Verfügung.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Woche vom 7. Januar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-app-pin----2298397---"></a>Intune-App-PIN <!-- 2298397 -->
Als IT-Administrator können Sie die Anzahl der Tage konfigurieren, die ein Endbenutzer warten kann, bis seine Intune-App-PIN geändert werden muss. Die neue Einstellung *Anzahl von Tagen für PIN-Zurücksetzung* steht im Azure-Portal unter **Intune** > **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie erstellen** > **Einstellungen** > **Zugriffsanforderungen** zur Verfügung. Dieses Feature kann auf [iOS](app-protection-policy-settings-ios.md)- und [Android](app-protection-policy-settings-android.md)-Geräten verwendet werden und unterstützt positive ganze Zahlen als Wert.


#### <a name="intune-device-reporting-fields----2748738---"></a>Felder zur Geräteberichterstellung in Intune <!-- 2748738 -->
Intune bietet zusätzliche Felder zur Geräteberichtserstellung, einschließlich Feldern für App-Registrierungs-ID, Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-Modell. In Intune sind diese Felder unter **Client-Apps** > **Status des App-Schutzes** und **Bericht zum App-Schutz: iOS, Android** verfügbar. Darüber hinaus werden diese Parameter Sie bei der Konfiguration der **Zulassen**-Liste für den Gerätehersteller (Android), der **Zulassen**-Liste für das Gerätemodell (Android und iOS) sowie der Einstellung der mindestens erforderlichen Android-Sicherheitspatchversion unterstützen. 


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und wurden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->

Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update:

- Administrative Vorlagen umfassen über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
- Administrative Vorlagen befinden sich in der öffentlichen Vorschauphase.
- Administrative Vorlagen werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
- Die Berichterstellung ist aktiviert.

Unter [Windows 10 templates to configure group policy settings (Windows 10-Vorlagen zur Konfiguration von Gruppenrichtlinieneinstellungen)](administrative-templates-windows.md) erfahren Sie mehr zu diesem Feature.

Gilt für: Windows 10 und höher

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Verwenden von S/MIME zum Verschlüsseln und Signieren von mehreren Geräten für einen Benutzer  <!-- 1333642 -->
Mit diesem Update wird die E-Mail-Verschlüsselung mit S/MIME mittels eines neuen Profils für importierte Zertifikate eingeführt. Navigieren Sie zu deren Verwendung zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, und wählen Sie zuerst die Plattform und dann den Profiltyp **Importiertes PKCS-Zertifikat** aus. In Intune können Sie Zertifikate im PFX-Format importieren. Intune kann dann genau diese Zertifikate an mehrere Geräte übergeben, die durch einen einzelnen Benutzer registriert wurden. Außerdem enthalten:
- Das native iOS-E-Mail-Profil unterstützt die Aktivierung der S/MIME-Verschlüsselung mithilfe importierter Zertifikate im PFX-Format.
- Die native E-Mail-App auf Windows Phone 10-Geräten verwendet automatisch das S/MIME-Zertifikat.
- Die privaten Zertifikate können über mehrere Plattformen übermittelt werden. Jedoch unterstützen nicht alle E-Mail-Apps S/MIME.
- Auf anderen Plattformen müssen Sie möglicherweise die E-Mail so konfigurieren, dass Sie S/MIME zulässt.  
- E-Mail-Apps, die die S/MIME-Verschlüsselung unterstützen, behandeln das Abrufen von Zertifikaten für die S/MIME-E-Mail-Verschlüsselung womöglich in einer Art und Weise, die von MDM nicht unterstützt werden kann, z.B. durch Lesen über den Zertifikatspeicher des Verlegers.
Weitere Informationen zu diesem Feature finden Sie unter [S/MIME für die Signierung und Verschlüsselung von E-Mails in Intune](certificates-s-mime-encryption-sign.md).
Unterstützt auf: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Neue Optionen zum automatischen Herstellen einer Verbindung und Beibehalten von Regeln bei der Verwendung von DNS-Einstellungen unter Windows 10 und höher <!-- 1333665, 2999078 -->
Auf Geräten unter Windows 10 und höher können Sie ein VPN-Konfigurationsprofil erstellen, das eine Liste von DNS-Servern zum Auflösen von Domänen enthält, z. B. „contoso.com“. Dieses Update enthält neue Einstellungen für die Namensauflösung (Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**. Wählen Sie **Windows 10 und höher** als Plattform und **VPN** als Profiltyp aus, und wählen Sie **DNS-Einstellungen** >**Hinzufügen** aus): 
- **Automatisch verbinden:** Wenn diese Option **Aktiviert** ist, stellt das Gerät automatisch eine Verbindung mit dem VPN her, wenn ein Gerät mit einer Domäne Kontakt aufnimmt, die Sie eingeben, z.B. „contoso.com“.
- **Persistent:** Standardmäßig sind alle Regeln der Namensauflösungsrichtlinie-Tabelle (Name Resolution Policy Table, NRPT) aktiv, solange das Gerät über dieses VPN-Profil verbunden ist. Wenn diese Einstellung für eine NRPT-Regel **aktiviert** ist, bleibt die Regel auch dann auf dem Gerät aktiv, wenn das VPN getrennt ist. Die Regel bleibt in Kraft, bis das VPN-Profil entfernt wird oder bis die Regel manuell entfernt wird – dies kann über PowerShell erfolgen.
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) werden die Einstellungen beschrieben. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Verwenden vertrauenswürdiger Netzwerkerkennung für VPN-Profile auf Windows 10-Geräten <!-- 1500165 -->
Wenn Sie die Erkennung vertrauenswürdiger Netzwerke verwenden, können Sie verhindern, dass VPN-Profile automatisch eine VPN-Verbindung herstellen, wenn der Benutzer sich bereits in einem vertrauenswürdigen Netzwerk befindet. Sie können DNS-Suffixe zum Aktivieren der Erkennung vertrauenswürdiger Netzwerke auf Geräten mit Windows 10 und höher hinzufügen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** als Plattform und **VPN** als Profiltyp).
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) sind die aktuellen VPN-Einstellungen aufgeführt.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Verwalten von Windows Holographic for Business-Geräten, die von mehreren Benutzern verwendet werden <!-- 1907917, 1063203 -->
Derzeit können Sie gemeinsame PC-Einstellungen auf Windows 10- und Windows Holographic for Business-Geräten mithilfe einer benutzerdefinierten OMA-URI-Einstellung konfigurieren. Mit diesem Update wird ein neues Profil zum Konfigurieren gemeinsamer PC-Einstellungen hinzugefügt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Freigegebenes, von mehreren Benutzern verwendetes Gerät**).
Im Artikel zu [Intune-Einstellungen zum Verwalten gemeinsam verwendeter Geräte](shared-user-device-settings.md) erfahren Sie mehr zu diesem Feature.
Gilt für: Windows 10 und höher, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Neue Windows 10-Updateeinstellungen <!--2626030  2512994  -->
Für Ihre [Windows 10-Updateringe](windows-update-for-business-configure.md) können Sie folgende Konfigurationen vornehmen:
- **Verhalten bei automatischen Updates**: Verwenden Sie die neue Option *Standard wiederherstellen* zum Wiederherstellen der ursprünglichen Einstellungen für automatische Updates auf einem Windows 10-Computer auf Computern, die das *Oktober 2018-Update* ausführen
- **Verweigern des Anhalten eines Updates**: Konfigurieren Sie eine neuen Softwareupdateseinstellung, mit der Sie blockieren oder zulassen können, dass Ihre Benutzer Updateinstallationen über die *Einstellungen* ihrer Computer anhalten. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS-E-Mail-Profile können S/MIME-Signatur und -Verschlüsselung verwenden <!-- 2662949 -->
Sie können ein E-Mail-Profil erstellen, das unterschiedliche Einstellungen enthält. Dieses Update umfasst S/MIME-Einstellungen, die zum Signieren und Verschlüsseln der E-Mail-Kommunikation auf iOS-Geräten verwendet werden können (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **E-Mail** als Profiltyp aus).
Unter [iOS-E-Mail-Konfigurationseinstellungen](email-settings-ios.md) werden die Einstellungen aufgelistet.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Einige BitLocker-Einstellungen unterstützen die Windows 10 Pro-Edition<!-- 2727036 -->
Sie können ein Konfigurationsprofil erstellen, das die Endpunktschutzeinstellungen auf Windows 10-Geräten einschließlich BitLocker festlegt. Mit diesem Update wird die Unterstützung für Windows 10 Professional für einige BitLocker-Einstellungen hinzugefügt. Diese Schutzeinstellungen finden Sie unter [Endpoint protection settings for Windows 10 (Endpunktschutzeinstellungen für Windows 10)](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>„Konfiguration freigegebener Geräte“ wurde für iOS-Geräte im Azure-Portal in „Nachricht auf Sperrbildschirm“ umbenannt<!-- 2809362 -->
Bei der Erstellung eines Konfigurationsprofils für iOS-Geräte können Sie **Konfigurationen für gemeinsam verwendete Geräte** vornehmen, um einem bestimmten Text auf dem Sperrbildschirm anzuzeigen. Dieses Update umfasst folgende Änderungen: 
- Die **Konfiguration freigegebener Geräte**-Einstellungen im Azure-Portal werden umbenannt in „Nachricht auf Sperrbildschirm (nur überwacht)“ (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **Gerätefunktionen** als Profiltyp aus, wählen Sie **Nachricht auf Sperrbildschirm** aus).
- Beim Hinzufügen von Sperrbildschirmnachrichten können Sie eine Seriennummer, einen Gerätenamen oder einen anderen gerätespezifischen Wert als Variable in **Bestandskennzeicheninformationen** und einer **Fußnote im Sperrbildschirm** einfügen. Sie können z.B. `Device name: {{devicename}}` oder `Serial number is {{serialnumber}}` mit geschweiften Klammern eingeben. [iOS-Token](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) listet die verfügbaren Token auf, die verwendet werden können.
In den [Einstellungen zur Anzeige von Nachrichten auf dem Sperrbildschirm](shared-device-settings-ios.md) werden die aktuellen Einstellungen aufgelistet.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Neue Einstellungen für App Store, Dokumentanzeige, Gaminggeräteeinschränkungen auf iOS-Geräten <!-- 2827760-->
Unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** als Plattform, **Geräteeinschränkungen** als Profiltyp und **App Store, Dokumentanzeige, Spiele** wurden die folgenden Einstellungen hinzugefügt: „Verwaltete Apps können Kontakt in nicht verwaltete Kontaktkonten schreiben“, „Nicht verwaltete Apps können aus verwalteten Kontaktkonten lesen“. In der [Liste der Einstellungen für iOS-Geräteeinschränkungen](device-restrictions-ios.md#app-store-doc-viewing-gaming) können Sie sich diese Einstellungen ansehen.

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Neue Benachrichtigungen, Hinweise und Keyguard-Einstellungen für Geräte von Android Enterprise-Gerätebesitzern <!-- 3201839 3201843 -->
Dieses Update umfasst mehrere neue Features für Android Enterprise-Geräte bei Ausführung als Gerätebesitzer. Um diese Features zu verwenden, wechseln Sie zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie als **Plattform** **Android Enterprise** und als **Profiltyp** **Nur Gerätebesitzer** > **Geräteeinschränkungen** aus.

Es sind folgende neue Features verfügbar: 

- Deaktivieren der Anzeige von Systembenachrichtigungen einschließlich eingehender Anrufe, Systemwarnungen, Systemfehler und mehr.
- Das Überspringen des Startens von Tutorials und von Hinweisen für Apps, die erstmals geöffnet werden, wird vorgeschlagen.
- Deaktivieren erweiterter Keyguard-Einstellungen, z.B. Kamera, Benachrichtigungen, Fingerabdruckentsperrung und mehr.


Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Geräte von Android Enterprise-Gerätebesitzern können Always On-VPN-Verbindungen verwenden <!-- 3202194 -->
In diesem Update können Sie Always On-VPN-Verbindungen mit Geräten von Android Enterprise-Gerätebesitzern verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Sie können Always On-VPN wie folgt aktivieren: Wählen Sie in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** als Plattform, **Geräteeinschränkungen** für „Nur Gerätebesitzer“ und die Einstellungen für **Konnektivität** aus. Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Neue Einstellung zum Beenden von Prozessen im Task-Manager auf Windows 10-Geräten <!-- 3285177 --> 
Dieses Update umfasst eine neue Einstellung für Endprozesse im Task-Manager auf Windows 10-Geräten. Mithilfe eines Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform**  **Windows 10** und für **Profiltyp** **Geräteeinschränkungen** > **Allgemein** aus) lassen Sie diese Einstellung zu oder verhindern sie.
Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10](device-restrictions-windows-10.md).
Gilt für: Windows 10 und höher


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Ausführlicheres Messaging zu Registrierungseinschränkungsfehlern <!-- 3111564 -->
Wenn die Einschränkungen für die Registrierung nicht erfüllt werden, werden nun aussagekräftigere Fehlermeldungen ausgegeben. Um diese Meldungen anzuzeigen, wechseln Sie zu **Intune** > **Problembehandlung**, und überprüfen Sie die Tabelle „Registrierungsfehler“. Weitere Informationen finden Sie in der Liste mit den [Registrierungsfehlern](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard zum Mandantenstatus  <!-- 1124854 -->
Auf der neuen Seite mit dem [Mandantenstatus](tenant-status.md) können Sie auf einen Blick den Status Ihres Mandanten und damit verbundene Informationen sehen.  Dieses Dashboard ist in vier Bereiche unterteilt:
- **Tenant Details** (Mandantendetails): Hier werden z. B. Ihre MDM-Autorität, die insgesamt bei Ihrem Mandanten angemeldeten Geräte und die Anzahl Ihrer Lizenzen angezeigt. In diesem Abschnitt wird auch die aktuelle Dienstversion für Ihren Mandanten angezeigt.
- **Connector Status** (Connectorstatus): Hier werden Informationen zu verfügbaren konfigurierten Connectors angezeigt und deaktivierte Connectors aufgelistet.  
   Basierend auf ihrem aktuellen Status werden die Connectors als „Healthy“ (Fehlerfrei), „Warning“ (Warnung) oder „Unhealthy“ (Fehlerhaft) gekennzeichnet. Wählen Sie einen Connector aus, den Sie sich genauer ansehen möchten, und zeigen Sie weitere Details an, oder konfigurieren Sie zusätzliche Informationen.
-  **Intune Service Health** (Intune-Dienstintegrität): Hier werden aktive Vorfälle oder Ausfälle für Ihren Mandanten angezeigt. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen.
-  **Intune News** (Neuigkeiten zu Intune): Hier werden aktive Meldungen Ihres Mandanten angezeigt. Dazu zählen u. a. Benachrichtigungen zu den neuesten Intune-Features.  Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Neue Hilfe- und Supportbenutzeroberfläche im Unternehmensportal für Windows 10 <!-- 1488939-->
Über die neue Seite für Hilfe und Support im Intune-Unternehmensportal können Benutzer Probleme beheben und Hilfe zu App- und Zugriffsproblemen erhalten. Über die neue Seite können sie Informationen zu Fehler- und Diagnoseprotokollen per E-Mail versenden und Informationen zum Helpdesk ihrer Organisation erhalten. Zudem gibt es einen Bereich mit häufig gestellten Fragen und Links zu relevanten Intune-Dokumentationsartikeln. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Neue Benutzeroberfläche für Hilfe und Support für Intune   <!-- #3307080 -->
Innerhalb der nächsten Tage wird diese neue Hilfe- und Supportbenutzeroberfläche für alle Mandanten verfügbar gemacht. Diese neue Benutzeroberfläche ist für Intune verfügbar und kann über das Blatt „Intune“ im [Azure-Portal](https://portal.azure.com/) verwendet werden.
Über die neue Benutzeroberfläche können Sie Ihr Problem in eigenen Worten beschreiben und erhalten Einblicke in die Problembehandlung sowie webbasierte Anleitungen zur Selbsthilfe. Diese Lösungen werden über einen regelbasierten Algorithmus für maschinelles Lernen angeboten, der auf Benutzeranfragen basiert. Zusätzlich zur themenspezifischen Anleitung können Sie auch den neuen Workflow zur Anfragestellung nutzen, um eine Supportanfrage per E-Mail oder Telefon zu stellen. Diese neue Benutzeroberfläche ersetzen die alte Benutzeroberfläche für Hilfe und Support, die statische, vorab ausgewählte Optionen enthielt. Diese basieren auf dem Bereich der Konsole, in dem Sie sich befinden, wenn Sie „Hilfe und Support“ öffnen. Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-apps----1081941---"></a>Bereichsmarkierungen für Apps <!-- 1081941 -->
Sie können Bereichsmarkierungen erstellen, um den Zugriff für Rollen und Apps einzuschränken. Sie können einer App eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie die App auf diese zugreifen können. Derzeit können Apps, die Intune über den verwalteten Google Play Store hinzugefügt wurden oder die mithilfe des Apple Volume Purchase Program (VPP) erworben wurden, keine Bereichsmarkierungen hinzugefügt werden (zukünftige Unterstützung dafür ist geplant). Weitere Informationen finden Sie unter [Use scope tags to filter policies (Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien)](scope-tags.md).

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>Woche des 10. Dezember 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="updates-for-application-transport-security----748318---"></a>Updates der Application Transport Security-Technologie <!-- 748318 -->

Microsoft Intune unterstützt Version 1.2 und höher des TLS-Protokolls (Transport Layer Security). Dieses Protokoll bietet erstklassige Verschlüsselungsfunktionen, um eine höhere standardmäßige Sicherheit von Intune zu gewährleisten und Intune auf andere Microsoft-Dienste wie Microsoft Office 365 abzustimmen. Um diese Anforderung zu erfüllen, erzwingen die iOS- und macOS-Unternehmensportale die aktualisierte ATS-Technologie (Application Transport Security) von Apple, die ebenfalls die Verwendung von TLS 1.2 und höher erfordert. ATS wird verwendet, um eine strengere Sicherheit in allen App-Kommunikationen über HTTPS zu erzwingen. Diese Änderung hat Auswirkungen für Intune-Kunden, die Unternehmensportal-Apps unter iOS und macOS verwenden. Weitere Informationen finden Sie im [Intune-Supportblog](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Das Intune App SDK unterstützt 256-Bit-Verschlüsselungsschlüssel <!-- 1832174 -->
Das Intune App SDK für Android verwendet jetzt 256-Bit-Verschlüsselungsschlüssel, wenn die Verschlüsselung durch App-Schutzrichtlinien aktiviert wird. Das SDK bietet zur Kompatibilität mit Inhalten und Apps, die ältere SDK-Versionen verwenden, weiterhin Unterstützung der 128-Bit-Schlüssel.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Microsoft AutoUpdate Version 4.5.0 für macOS-Geräte erforderlich <!-- 3503442 -->
Von Intune verwaltete macOS-Geräte müssen auf Microsoft AutoUpdate 4.5.0 upgegradet werden, um weiterhin Updates für das Unternehmensportal und andere Office-Anwendungen zu erhalten. Benutzer verfügen möglicherweise bereits über diese Version für ihre Office-Apps.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Für Intune ist macOS 10.12 oder höher erforderlich <!-- 2827778 -->
Für Intune ist jetzt macOS Version 10.12 oder höher erforderlich. Geräte mit früheren macOS-Versionen können sich nicht über das Unternehmensportal in Intune registrieren. Wenn Benutzer Unterstützung und neue Features erhalten möchten, müssen sie für ihr Gerät ein Upgrade auf macOS 10.12 oder höher und für das Unternehmensportal ein Upgrade auf die neueste Version durchführen.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Woche vom 26. November 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Deinstallieren von Apps auf unternehmenseigenen überwachten iOS-Geräten <!-- 1281677 -->

Sie können beliebige unternehmenseigene überwachte iOS-Geräte entfernen. Sie können eine beliebige App entfernen, indem Sie entweder Benutzer- oder Gerätegruppen mit dem Zuweisungstyp **Deinstallieren** als Ziel verwenden. Für persönliche oder nicht überwachte iOS-Geräte können weiterhin nur Apps entfernt werden, die mit Intune installiert wurden.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Herunterladen von Intune Win32-App-Inhalten <!-- 2617320 -->
Clients von Windows 10 RS3 und höher laden Intune Win32-App-Inhalte mit einer Komponente zur Übermittlungsoptimierung auf den Windows 10-Client herunter. Die Übermittlungsoptimierung bietet Peer-zu-Peer-Funktionen, die standardmäßig eingeschaltet sind. Die Übermittlungsoptimierung kann derzeit mit einer Gruppenrichtlinie konfiguriert werden. Weitere Informationen finden Sie unter [Übermittlungsoptimierung für Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Endbenutzergerät und App-Inhaltsmenü <!-- 2771453 -->
Endbenutzer können jetzt über das Kontextmenü auf Geräten und in Apps häufig verwendete Aktionen auslösen, z.B. das Umbenennen eines Geräts oder die Prüfung der Konformität.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Festlegen eines benutzerdefinierten Hintergrunds in der Managed Home Screen-App  <!-- 3041945 -->
Es wird eine Einstellung hinzugefügt, mit der Sie den Hintergrund der Managed Home Screen-App auf Android Enterprise-, Multi-App- und Kioskmodusgeräten anpassen können.  Um eine **URL für einen benutzerdefinierten Hintergrund** zu konfigurieren, wechseln Sie im Azure-Portal zu Intune und dann zur Gerätekonfiguration. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Speichern und Anwenden von App-Schutzrichtlinienzuweisungen <!-- 3104570 -->
Sie erhalten jetzt eine bessere Kontrolle über Ihre [App-Schutzrichtlinienzuweisungen](app-protection-policies.md#deploy-a-policy-to-users). Wenn Sie *Zuweisungen* auswählen, um die Zuweisungen einer Richtlinie festzulegen oder zu bearbeiten, müssen Sie Ihre Konfiguration **speichern**, bevor die Änderung angewendet wird. Löschen Sie mit **Verwerfen** alle Änderungen, die Sie vornehmen, ohne Änderungen in den Listen zum Einschließen oder Ausschließen zu speichern.  Wenn Speichern oder Verwerfen erforderlich ist, werden nur die von Ihnen vorgesehenen Benutzer einer App-Schutzrichtlinie zugewiesen.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Neue Microsoft Edge-Browsereinstellungen für Windows 10 und höher <!-- 3174639 -->
Dieses Update enthält neue Einstellungen, die Sie dabei unterstützen, den Microsoft Edge-Browser auf Ihren Geräten zu steuern und zu verwalten. Eine Liste dieser Einstellungen finden Sie in den [Geräteeinschränkungen für Windows 10 (und höher)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Unterstützung neuer Apps mit App-Schutzrichtlinien <!-- 3330037 -->
Sie können jetzt die folgenden Apps mit [Intune-App-Schutzrichtlinien](app-protection-policies.md) verwalten:
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Verwenden Sie App-Schutzrichtlinien, um für diese Apps Unternehmensdaten zu schützen und die Datenübertragung zu steuern, wie andere richtlinienverwaltete Intune-Apps. Hinweis: Wenn Flow noch nicht in der Konsole sichtbar ist, fügen Sie Flow beim Erstellen oder Bearbeiten von App-Schutzrichtlinien hinzu. Verwenden Sie hierzu die Option **+ Weitere Apps**, und geben Sie dann die *App-ID* für Flow in das Eingabefeld ein. Verwenden Sie für Android *com.microsoft.flow* und für iOS *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Anzeige der Versionsnummern und Buildnummern von iOS und macOS <!-- 1892471 -->
Unter **Gerätekonformität** > **Gerätekonformität** wird die iOS-und macOS-Betriebssystemversion angezeigt, für die Konformitätsrichtlinien verwendet werden können. Dieses zukünftige Update umfasst auch die Buildnummer, die für beide Plattformen konfigurierbar ist.
Wenn Sicherheitsupdates veröffentlicht werden, bleibt die Versionsnummer von Apple in der Regel unverändert bestehen, die Buildnummer wird jedoch aktualisiert. Wenn Sie die Buildnummer in einer Konformitätsrichtlinie verwenden, können Sie einfach überprüfen, ob ein Sicherheitsupdate installiert wurde.
Wie Sie dieses Feature verwenden, erfahren Sie in den [iOS](compliance-policy-create-ios.md#device-health)- und [macOS](compliance-policy-create-mac-os.md#device-properties)-Konformitätsrichtlinien.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Updateringe wurden durch Einstellungen zur Übermittlungsoptimierung für Windows 10 und höher ersetzt <!-- 2753807 -->
Die Übermittlungsoptimierung ist ein neues Konfigurationsprofil für Windows 10 und höher. Diese Funktion bietet eine optimierte Benutzeroberfläche zum Übermitteln von Softwareupdates an Geräte in Ihrer Organisation. Mit diesem Update können Sie die Einstellungen auch mithilfe eines Konfigurationsprofils an neue und vorhandene Updateringe übermitteln.
Wie Sie ein Konfigurationsprofil für die Übermittlungsoptimierung konfigurieren, erfahren Sie unter [Einstellungen zur Übermittlungsoptimierung in Microsoft Intune in Windows 10 (und höher)](delivery-optimization-windows.md).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Neue Einstellungen für Geräteeinschränkungen wurden für iOS- und macOS-Geräte hinzugefügt <!-- 2827760 -->
Dieses Update enthält neue Einstellungen für Ihre iOS- und macOS-Geräte, die mit iOS 12 veröffentlicht werden:

**iOS-Einstellungen**: 
- Allgemein: Entfernen von Apps blockieren (nur überwacht)
- Allgemein: Modus mit USB-Einschränkung blockieren (nur überwacht)
- Allgemein: Automatische Datums- und Uhrzeiteinstellung erzwingen (nur überwacht)
- Kennwort: AutoAusfüllen für Kennwörter blockieren (nur überwacht)
- Kennwort: Kennwortanforderungen durch Näherung blockieren (nur überwacht)
- Kennwort: Kennwortfreigabe blockieren (nur überwacht)

**macOS-Einstellungen**: 
- Kennwort: AutoAusfüllen für Kennwörter blockieren
- Kennwort: Kennwortanforderungen durch Näherung blockieren
- Kennwort: Kennwortfreigabe blockieren

Mehr über diese Einstellungen finden Sie in den Einstellungen für Geräteeinschränkungen unter [iOS](device-restrictions-ios.md) und [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Auswählen von Apps zur Nachverfolgung auf der Registrierungsstatusseite<!-- 2531007 -->
Sie können auswählen, welche Apps auf der Registrierungsstatusseite nachverfolgt werden. Solange diese Apps nicht installiert sind, kann der Benutzer das Gerät nicht verwenden. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Suchen nach dem Autopilot-Gerät mithilfe der Seriennummer <!--2595788 -->
Sie können jetzt mithilfe der Seriennummer nach dem Autopilot-Gerät suchen. Wählen Sie zu diesem Zweck **Geräteregistrierung** > **Windows-Registrierung** > **Geräte** aus, geben Sie die Seriennummer in das Feld **Nach Seriennummer suchen** ein, und drücken Sie die EINGABETASTE.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Nachverfolgen der Installation von Office ProPlus <!--2620217 -->
Benutzer können den Installationsfortschritt von [Office ProPlus](apps-add-office365.md) mithilfe der [Seite zum Registrierungsstatus](windows-enrollment-status.md) nachverfolgen. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und die Lizenzen für das Unternehmensportal knapp werden.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Unterstützung des Programms zur macOS-Geräteregistrierung für Apple School Manager-Konten <!--3006133 -->
Intune unterstützt jetzt die Verwendung des Programms zur Geräteregistrierung für macOS-Geräte für Apple School Manager-Konten.  Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Neue Abonnement-SKU für Intune-Geräte <!--3312071-->
Eine neue gerätebasierte Abonnement-SKU ist nun verfügbar, mit der die Kosten für die Geräteverwaltung in Unternehmen reduziert werden können. Diese SKU für Intune-Geräte wird monatlich pro Gerät lizenziert. Der Preis hängt vom Lizenzierungsprogramm ab. Dieses ist direkt im Microsoft 365 Admin Center sowie über das [Enterprise Agreement](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), das [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA), [Microsoft Open Agreements](https://partner.microsoft.com/licensing/licensing-agreements) und [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) verfügbar.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Temporäres Anhalten des Kioskmodus auf Android-Geräten zum Durchführen von Änderungen <!-- 3041935 -->
Bei Verwendung von Android-Geräten im Multi-App-Kioskmodus kann es erforderlich werden, dass ein IT-Administrator Änderungen am Gerät vornimmt. Dieses Update beinhaltet eine neue Multi-App-Kioskeinstellung, die dem IT-Administrator erlaubt, den Kioskmodus unter Verwendung einer PIN temporär anzuhalten und Zugriff auf das gesamte Gerät zu erhalten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Aktivieren einer virtuellen Startschaltfläche auf Android Enterprise-Kioskgeräten  <!-- 3042021 -->
Eine neue Einstellung erlaubt es den Benutzern, auf ihrem Gerät auf einen Softkey zu tippen, um auf ihrem Multi-App-Kioskgerät zwischen der Managed Home Screen-App und anderen zugewiesenen Apps zu wechseln. Diese Einstellung ist insbesondere dann nützlich, wenn eine Kiosk-App des Benutzers nicht ordnungsgemäß auf die ZURÜCK-Taste reagiert. Sie können diese Einstellung für unternehmenseigene, einzeln genutzte Android-Geräte konfigurieren. Wechseln Sie im Azure-Portal zu Intune und anschließend zur Gerätekonfiguration, um die Einstellung **Virtuelle Startschaltfläche** zu aktivieren oder zu deaktivieren. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Woche vom 12. November 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Unterstützung der Netzwerkzugriffssteuerung für Citrix SSO für iOS <!-- 3259404 -->

Citrix hat ein Update für Citrix Gateway veröffentlicht, um die Netzwerkzugriffssteuerung (Network Access Control, NAC) für Citrix SSO für iOS in Intune zu ermöglichen. Sie können eine Geräte-ID in einem VPN-Profil in Intune einschließen und dieses Profil dann mithilfe von Push an Ihre iOS-Geräte übertragen. Sie müssen das neueste Update für Citrix Gateway installieren, um diese Funktion nutzen zu können.

Der Artikel [Konfigurieren von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune](vpn-settings-ios.md#base-vpn-settings) enthält weitere Informationen zur Verwendung der NAC sowie einige zusätzliche Anforderungen. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Woche vom 5. November 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Unterstützung von iOS 12 OAuth in iOS-E-Mail-Profilen <!--2155106 -->

Die iOS-E-Mail-Profile in Intune unterstützen nun Open Authorization (OAuth) für iOS 12. Wenn Sie dieses Feature verwenden möchten, erstellen Sie ein neues Profil (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **E-Mail** (Profiltyp)), oder aktualisieren Sie ein vorhandenes iOS-E-Mail-Profil. Wenn Sie OAuth in einem Profil aktivieren, das bereits für Benutzer bereitgestellt wurde, werden die Benutzer zur erneuten Authentifizierung und zum Erneuten Herunterladen ihrer E-Mails aufgefordert.

Unter [Einstellungen für E-Mail-Profile für iOS-Geräte](email-settings-ios.md) finden Sie weitere Informationen zur Verwendung von OAuth für E-Mail-Profile.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Autopilot-Unterstützung für in Azure Active Directory Hybrid eingebundene Geräte (Preview) <!-- 1048100-->
Sie können ab sofort in Azure Active Directory Hybrid eingebundene Geräte mithilfe von Autopilot einrichten. Geräte müssen mit dem Netzwerk Ihres Unternehmens verbunden sein, um das Hybrid-Autopilot-Feature nutzen zu können. Weitere Informationen finden Sie unter [Bereitstellen von in Azure AD Hybrid eingebundenen Geräten mit Intune und Windows Autopilot](windows-autopilot-hybrid.md).
Dieses Feature wird in den nächsten Tagen für Benutzer eingeführt. Daher können Sie diese Schritte möglicherweise erst ausführen, wenn es für Ihr Konto eingeführt wurde.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Woche vom 29. Oktober 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Anfordern der nicht biometrischen PIN nach festgelegtem Timeout <!-- 1506985 -->
Durch die erzwungene Verwendung einer nicht biometrischen PIN nach einem vom Administrator festgelegten Zeitraum wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, Verwaltung mobiler Anwendungen) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen. Weitere Informationen zu den Zugriffseinstellungen finden Sie unter [iOS-Einstellungen](app-protection-policy-settings-ios.md#access-requirements) und [Android-Einstellungen](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Intune-App-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten <!-- 2244713 -->
Sie können die Steuerung der Intune-App-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten von der Angabe der Identität des registrierten Benutzers (auch als Benutzerprinzipalname (UPN) bekannt) trennen. Administratoren, die IntuneMAMUPN nicht verwenden, werden keine Verhaltensänderung feststellen. Wenn diese Funktion verfügbar ist, sollten Administratoren, die mit IntuneMAMUPN das Datenübertragungsverhalten auf registrierten Geräten steuern, die neuen Einstellungen überprüfen und ihre APP-Einstellungen nach Bedarf aktualisieren.

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10-Win32-Apps <!-- 2617325 -->
Sie können die Win32-Apps kontextbezogen für einzelne Benutzer konfigurieren, anstatt die App für alle Benutzer des Geräts zu installieren.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows-Win32-Apps und PowerShell-Skripts <!-- 2617330 -->
Endbenutzer müssen nicht mehr beim Gerät angemeldet sein, um Win32-Apps zu installieren und PowerShell-Skripts auszuführen. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Problembehandlung bei der Installation von Client-Apps <!-- 1363711 -->
Sehen Sie sich im Blatt **Problembehandlung** die Spalte **App-Installation** an, um bei Problemen Client-Apps erfolgreich zu installieren. Um das Blatt **Problembehandlung** anzuzeigen, wählen Sie im Intune-Portal unter **Hilfe und Support** die Option **Problembehandlung**.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Unterstützung der Netzwerkzugriffssteuerung auf iOS-VPN-Clients <!-- 1333693 -->
Mit diesem Update gibt es eine neue Einstellung zum Aktivieren der Netzwerkzugriffssteuerung (Network Access Control, NAC), wenn Sie ein VPN-Konfigurationsprofil für Cisco AnyConnect, F5 Access und Citrix SSO für iOS erstellen. Über diese Einstellung kann die NAC-ID des Geräts in das VPN-Profil aufgenommen werden. Derzeit gibt es keine VPN-Clients oder NAC-Partnerlösungen, die diese neue NAC-ID unterstützen, aber wir werden Sie über unseren [Supportblogbeitrag](ttps://aka.ms/iOS12_and_vpn) auf dem Laufenden halten.

Zur Nutzung der Netzwerkzugriffssteuerung ist Folgendes erforderlich:
1. Aktivieren Sie diese Option, damit Intune Geräte-IDs in VPN-Profile aufnehmen kann.
2. Aktualisieren Sie Ihre NAC-Anbietersoftware bzw. -Firmware entsprechend der Anleitungen direkt von Ihrem NAC-Anbieter.

Informationen zu dieser Einstellung innerhalb eines iOS-VPN-Profils finden Sie unter [Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune](vpn-settings-ios.md). Weitere Informationen zur Netzwerkzugriffssteuerung finden Sie unter [Integrieren der Netzwerkzugriffssteuerung (NAC) mit Intune](network-access-control-integrate.md). 

Gilt für: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Entfernen eines E-Mail-Profils von einem Gerät, wenn nur ein solches Profil vorhanden ist <!-- 1818139 -->
Zuvor konnte ein E-Mail-Profil nicht von einem Gerät entfernt werden, *wenn* es das einzige E-Mail-Profil war. Dies wurde mit dem vorliegenden Update geändert. Nun können Sie ein E-Mail-Profil entfernen, auch wenn es das einzige E-Mail-Profil auf dem Gerät ist. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell-Skripts und AAD <!-- 2309469 -->
PowerShell-Skripts in Intune können auf AAD-Gerätesicherheitsgruppen ausgerichtet werden.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Neue Standardeinstellung „Erforderlicher Kennworttyp“ für Android und Android Enterprise<!-- 2649963 -->
Wenn Sie eine neue Konformitätsrichtlinie erstellen (**Intune** > **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** oder **Android Enterprise** für Plattform > Systemsicherheit), ändert sich der Standardwert für **Erforderlicher Kennworttyp**:

Von: Gerätestandard In: Mindestens numerisch

Gilt für: Android, Android Enterprise

Um diese Einstellungen anzuzeigen, wechseln Sie zu [Android](compliance-policy-create-android.md) bzw. [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Verwenden eines vorinstallierten Schlüssels in einem Windows 10-WLAN-Profil <!-- 2662938 -->
Mit diesem Update können Sie einen vorinstallierten Schlüssel (Pre-Shared Key, PSK) mit dem WPA/WPA2-Personal-Sicherheitsprotokoll verwenden, um ein WLAN-Konfigurationsprofil für Windows 10 zu authentifizieren. Sie können auch die Kostenkonfiguration für ein getaktetes Netzwerk für Geräte unter Windows 10 mit dem Update von Oktober 2018 angeben.

Derzeit müssen Sie ein WLAN-Profil importieren oder ein benutzerdefiniertes Profil erstellen, um einen vorinstallierten Schlüssel zu verwenden. [WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune](wi-fi-settings-windows.md) werden die aktuellen Einstellungen aufgeführt. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Entfernen von PKCS- und SCEP-Zertifikaten von Ihren Geräten <!-- 3218390 -->
In einigen Szenarios waren PKCS- und SCEP-Zertifikate weiterhin auf Geräten vorhanden, auch wenn eine Richtlinie aus einer Gruppe entfernt, eine Konfiguration oder eine Konformitätsbereitstellung gelöscht wurde oder ein Administrator ein vorhandenes SCEP- oder PKCS-Profil aktualisiert hat. Dies wurde mit dem vorliegenden Update geändert. In einigen Szenarios werden PKCS- und SCEP-Zertifikate von Geräten entfernt, in anderen verbleiben diese Zertifikat auf dem Gerät. Einen Überblick über diese Szenarios finden Sie unter [Remove SCEP and PKCS certificates in Microsoft Intune (Entfernen von SCEP- und PKCS-Zertifikaten in Microsoft Intune)](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Verwenden von Gatekeeper auf macOS-Geräten für Konformität <!-- 2504381 -->
Dieses Update beinhaltet die macOS-Gatekeeper-Anwendung, um Geräte auf Konformität zu prüfen. Um die Gatekeeper-Eigenschaft festzulegen, [fügen Sie eine Gerätekonformitätsrichtlinie für macOS-Geräte hinzu](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="enrollment-abandonment-report----1382924---"></a>Bericht zum Registrierungsabbruch <!-- 1382924 -->
Ein neuer Bericht, der Details zu abgebrochenen Registrierungen enthält, ist unter **Geräteregistrierung** > **Überwachen** verfügbar. Weitere Informationen finden Sie unter [Abbruchbericht des Unternehmensportals](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Neues Feature zu Azure Active Directory-Nutzungsbedingungen <!-- 2870393 -->
Azure Active Directory verfügt über ein Feature für Nutzungsbedingungen, das Sie anstelle der bestehenden Intune-Nutzungsbedingungen verwenden können. Die Azure AD Nutzungsbedingungen bieten mehr Flexibilität bei der Anzeige von Bedingungen (Umfang und Zeitpunkt), eine bessere Lokalisierungsunterstützung, mehr Kontrolle über die Darstellung von Nutzungsbedingungen und eine verbesserte Berichterstellung. Die Azure AD-Nutzungsbedingungen erfordern Azure Active Directory Premium P1, das ebenfalls Teil der Enterprise Mobility + Security E3 Suite ist. Weitere Informationen finden Sie im Artikel [Verwalten der Geschäftsbedingungen Ihres Unternehmens für den Benutzerzugriff](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Unterstützung des Modus für Android-Gerätebesitzer <!--3188762-->
Für die Samsung Knox Mobile-Registrierung unterstützt Intune jetzt die Registrierung von Geräten im Verwaltungsmodus für Android-Geräteeigentümer. Benutzer mit einer WLAN- oder Mobilfunknetzverbindung können die Registrierung mit nur wenigen Tippbewegungen ausführen, wenn sie ihre Geräte zum ersten Mal einschalten. Weitere Informationen finden Sie unter [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Geräteverwaltung
#### <a name="new-settings-for-software-updates------1907869---"></a>Neue Einstellungen für Softwareupdates   <!-- 1907869 -->  
- Sie können jetzt einige Benachrichtigungen konfigurieren, um Endbenutzer vor Neustarts zu warnen, die erforderlich sind, um die Installation der neuesten Softwareupdates abzuschließen.   
- Sie können jetzt eine Warnmeldung für Neustarts konfigurieren, die außerhalb der Arbeitszeit stattfinden, wodurch BYOD-Szenarios unterstützt werden.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Gruppieren von mit Windows Autopilot registrierten Geräten nach Korrelator-ID <!-- 2075110 -->
Intune unterstützt nun die Gruppierung von Windows-Geräten nach einer Korrelator-ID, wenn sie mit [Autopilot für bestehende Geräte](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) über den Configuration Manager registriert werden. Die Korrelator-ID ist ein Parameter der Autopilot-Konfigurationsdatei. Intune legt das [Azure AD-Geräteattribut „enrollmentProfileName“](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) automatisch auf „OfflineAutopilotprofile-<correlator ID>“ fest. Dadurch können beliebige dynamische Azure AD-Gruppen basierend auf der Korrelator-ID über das Attribut „enrollmentprofileName“ für Offlineregistrierungen von Autopilot erstellt werden. Weitere Informationen finden Sie unter [Windows Autopilot für vorhandene Geräte](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Intune-App-Schutzrichtlinien <!-- 2984657 -->
Mithilfe von Intune-App-Schutzrichtlinien können Sie verschiedene Einstellungen zum Schutz von Daten für mit Intune geschützte Apps konfigurieren, zum Beispiel Microsoft Outlook und Microsoft Word. Aussehen und Verhalten dieser Einstellungen wurden sowohl für [iOS](app-protection-policy-settings-ios.md) als auch für [Android](app-protection-policy-settings-android.md) geändert, um das Auffinden individueller Einstellungen zu erleichtern. Es gibt drei Kategorien von Richtlinieneinstellungen:
- **Datenverschiebung**: Diese Gruppe umfasst Steuerelemente zum Verhindern von Datenverlust, wie z.B. Einschränkungen für Ausschneiden, Kopieren, Einfügen und „Speichern unter“. Diese Einstellungen bestimmen, wie Benutzer mit Daten in den Apps interagieren können.
- **Zugriffsanforderungen**: Diese Gruppe enthält die PIN-Optionen pro App. Sie bestimmen, wie der Endbenutzer in einem Arbeitskontext auf die Apps zugreifen kann.  
- **Bedingter Start**: Diese Gruppe enthält Einstellungen wie z.B. die mindestens erforderliche Betriebssystemversion, Einstellungen zur Erkennung von Jailbreak und entfernten Nutzungsbeschränkungen und die Offlinetoleranzperiode.  
  
Die Funktionalität der Einstellungen ändert sich nicht, aber es wird einfacher sein, sie bei der Richtlinienerstellung zu finden.

### <a name="intune-apps"></a>Intune-Apps

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune-Unterstützung für eine maximale Paketgröße von 8 GB für LOB-Anwendungen <!-- 1727158 -->
Intune erhöht die maximale Paketgröße auf 8 GB für LOB-Anwendungen. Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Hinzufügen eines benutzerdefinierten Markenbilds für die Unternehmensportal-App <!-- 1916266 -->
Als Microsoft Intune-Administrator können Sie ein benutzerdefiniertes Markenbild hochladen, das als Hintergrundbild auf der Profilseite des Benutzers in der iOS-Unternehmensportal-App angezeigt wird. Weitere Informationen zum Konfigurieren der Unternehmensportal-App finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune behält die lokalisierte Sprache für Office bei, wenn Office auf den Computern der Endbenutzer aktualisiert wird <!-- 2971030 -->
Wenn Intune Office auf den Computern Ihrer Endbenutzer installiert, erhalten sie automatisch dieselben Sprachpakete wie bei früheren MSI-Office-Installationen. Weitere Informationen finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Neue Benutzeroberfläche für Intune-Support im Portal für die Microsoft 365-Geräteverwaltung <!-- 3076965 -->
Im [Portal für die Microsoft 365-Geräteverwaltung]( http://devicemanagement.microsoft.com) wird eine neue Benutzeroberfläche für „Hilfe und Support“ in Intune eingeführt. Über die neue Benutzeroberfläche können Sie Ihr Problem in eigenen Worten beschreiben und erhalten Einblicke in die Problembehandlung sowie webbasierte Anleitungen zur Selbsthilfe. Diese Lösungen werden über einen regelbasierten Algorithmus für maschinelles Lernen angeboten, der auf Benutzeranfragen basiert.  

Zusätzlich zur themenspezifischen Anleitung können Sie auch den neuen Workflow zur Fallerstellung nutzen, um einen Supportfall per E-Mail oder Telefon zu öffnen.  

Für Kunden, die am Rollout teilnehmen, ersetzt diese neue Benutzeroberfläche die aktuelle Ansicht für Hilfe und Support, die einen statischen Satz an vorab ausgewählten Optionen enthält. Diese basieren auf dem Bereich der Konsole, in dem Sie sich befinden, wenn Sie „Hilfe und Support“ öffnen.  

*Diese neue Benutzeroberfläche für Hilfe und Support steht derzeit ausgewählten Mandanten über das Portal für die Geräteverwaltung zur Verfügung. Die Teilnehmer für diese neue Benutzeroberfläche werden nach dem Zufallsprinzip aus den verfügbaren Intune-Mandanten ausgewählt. Neue Mandanten werden bei Erweiterung des Rollouts hinzukommen.*  

Weitere Informationen finden Sie in „Anfordern von Support für Microsoft Intune“ unter [Neue Benutzeroberfläche für Hilfe und Support](get-support.md#help-and-support-experience).  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Vorschauversion für das PowerShell-Modul für Intune <!-- 951068 -->
Ein neues PowerShell-Modul, das über Microsoft Graph eine Unterstützung für die Intune-API bietet, ist nun als Vorschauversion auf [GitHub]( https://aka.ms/intunepowershell) verfügbar. Weitere Informationen zur Verwendung dieses Moduls finden Sie dort unter README. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Woche vom 15. Oktober 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>PIN-Eingabeaufforderung beim Ändern von Fingerabdrücken oder der Gesichts-ID auf einem iOS-Gerät  <!-- 2637704  -->
Benutzer werden jetzt zur Eingabe einer PIN aufgefordert, nachdem sie Änderungen an biometrischen Daten auf ihrem iOS-Gerät vorgenommen haben. Hierzu zählen Änderungen an registrierten Fingerabdrücken oder Gesichts-IDs. Die Zeitplanung für die Aufforderung hängt von der Konfiguration des Timeouts *Zugriffsanforderungen erneut prüfen nach (Minuten)* ab.  Wenn keine PIN festgelegt ist, wird der Benutzer aufgefordert, eine festzulegen. 
 
Dieses Feature ist nur für iOS verfügbar und erfordert, dass das Intune App SDK für iOS, Version 9.0.1 oder höher in betreffende Anwendungen integriert wird. Die Integration des SDK ist erforderlich, damit das Verhalten für die Zielanwendungen erzwungen werden kann. Diese Integration erfolgt kontinuierlich und ist abhängig von den jeweiligen Anwendungsteams. Zu den betreffenden Apps zählen z.B. WXP, Outlook, Managed Browser und Yammer.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>Woche vom 1. Oktober 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Zugriff auf wichtige Profileigenschaften über die Unternehmensportal-App <!-- 772203 -->
Endbenutzer können ab jetzt auf wichtige Eigenschaften und Aktionen über die Unternehmensportal-App zugreifen, z.B. die Kennwortzurücksetzung. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der App-Einstellungen <!-- 1248481 -->
Intune-Administratoren können auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (Application Protection Policy, APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Benutzerkontozugriff von Intune-Apps auf verwalteten Android- und iOS-Geräten <!-- 1248496 -->
Wie der Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Konfigurationsrichtlinie für die Outlook-App für iOS und Android <!--1828527 -->
Ab sofort können Sie für lokale Benutzer, die die grundlegende Authentifizierung mit dem ActiveSync-Protokoll nutzen, eine Konfigurationsrichtlinie für die Outlook-App für iOS und Android erstellen. Zusätzliche Konfigurationseinstellungen werden hinzugefügt, sobald sie für Outlook für iOS und Android aktiviert werden.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 ProPlus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Erweiterung für Dateien von branchenspezifischen Windows-Apps (LOB-Apps) <!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps umfassen jetzt *.msi*, *.appx*, *.appxbundle*, *.msix* und *.msixbundle*. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Client-Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Windows 10-App-Bereitstellung mit Intune <!-- 2309001 -->
Basierend auf der bestehenden Unterstützung für Branchenanwendungen (LOB) und Microsoft Store for Business-Apps können Administratoren mit Intune die meisten der vorhandenen Anwendungen ihres Unternehmens für Endbenutzer auf Windows 10-Geräten bereitstellen. Administratoren können Anwendungen für Windows 10-Benutzer in einer Vielzahl von Formaten wie MSI, Setup.exe oder MSP hinzufügen, installieren und deinstallieren. Intune wertet vor dem Herunterladen und Installieren, dem Benachrichtigen von Endbenutzern über den Status oder Neustartanforderungen die Anforderungsregeln über das Info-Center von Windows 10 aus. Diese Funktionalität wird Unternehmen, die daran interessiert sind, diesen Workload auf Intune und die Cloud zu verlagern, effektiv entlasten. Dieses Feature befindet sich derzeit in der öffentlichen Vorschauversion und wir erwarten, dass es in den nächsten Monaten um bedeutende neue Funktionen erweitert wird. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>App-Schutzrichtlinieneinstellungen für Webdaten <!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Endbenutzergerät und App-Inhaltsmenü <!-- 2771453 -->
Endbenutzer können nun das Kontextmenü für Geräte und Apps verwenden, um häufig verwendete Aktionen auszulösen, z.B. das Umbenennen eines Geräts oder die Überprüfung der Konformität. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Tastenkombinationen für die Windows-Unternehmensportal-App <!-- 2771518 -->
Endbenutzer können ab sofort mithilfe von Tastenkombinationen (Tastenkombinations-Editor) App- und Geräteaktionen in der Windows-Unternehmensportal-App auslösen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Erstellen von DNS-Suffixen in VPN-Konfigurationsprofilen auf Geräten mit Windows 10<!-- 1333668 -->
Beim Erstellen eines VPN-Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** Plattform > **VPN**-Profiltyp) geben Sie DNS-Einstellungen ein. Mit diesem Update können Sie auch mehrere **DNS-Suffixe** in Intune eingeben. Wenn Sie DNS-Suffixe verwenden, können Sie nach einer Netzwerkressource mithilfe ihres Kurznamens anstelle des vollqualifizierten Domänennamens (Fully Qualified Domain Name, FQDN) suchen. Mit diesem Update können Sie auch die Reihenfolge der DNS-Suffixe in Intune ändern.
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md#dns-settings) sind die aktuellen DNS-Einstellungen aufgeführt.
Gilt für: Windows 10-Geräte

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Unterstützung für Always On-VPN für Android-Enterprise-Arbeitsprofile <!-- 1333705 -->
In diesem Update können Sie Always On-VPN-Verbindungen auf Android Enterprise-Geräten mit verwalteten Arbeitsprofilen verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Sie können Always On-VPN in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen** > **Konnektivitätseinstellungen** aktivieren.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Ausstellen von SCEP-Zertifikaten für Geräte ohne Benutzer <!-- 1744554 -->
Derzeit werden Zertifikate an Benutzer ausgegeben. Mit diesem Update können SCEP-Zertifikate für Geräte ausgestellt werden, einschließlich benutzerloser Geräte wie Kioske (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** für Plattform > **SCEP-Zertifikat** für Profil). Weitere Updates enthalten:
- Die **Betreff**-Eigenschaft in einem SCEP-Profil ist nun ein benutzerdefiniertes Textfeld und kann neue Variablen enthalten. 
- Die **Alternativer Antragstellername**-Eigenschaft (Subject Alternative Name, SAN) in einem SCEP-Profil ist nun ein Tabellenformat und kann neue Variablen enthalten. In der Tabelle kann ein Administrator ein Attribut hinzufügen und den Wert in einem benutzerdefinierten Textfeld ausfüllen. Der SAN unterstützt die folgenden Attribute: 
  - DNS
  - E-Mail-Adresse
  - UPN

  Diese neuen Variablen können mit statischem Text in einem benutzerdefinierten Werttextfeld hinzugefügt werden. Beispielsweise kann das DNS-Attribut als `DNS = {{AzureADDeviceId}}.domain.com` hinzugefügt werden.

  > [!NOTE]
  > Geschweifte Klammern, Semikolons und Pipesymbole „{}; |“ funktionieren nicht im statischen SAN-Text. Geschweifte Klammern dürfen nur eine der neuen Gerätezertifikatvariablen umschließen, die entweder für `Subject` oder `Subject alternative name` akzeptiert werden. 

Neue Gerätezertifikatvariablen:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` funktioniert nur für Windows und in die Domäne eingebundene Geräte. 
>  -  Bei der Angabe von Geräteeigenschaften wie IMEI, Seriennummer und vollständig qualifiziertem Domänennamen im Betreff oder SAN für ein Gerätezertifikat achten Sie unbedingt darauf, dass diese Eigenschaften von einer Person mit Zugriff auf das Gerät gespooft sein könnten. 

[SCEP-Zertifikatprofil erstellen](certificates-scep-configure.md#create-a-scep-certificate-profile) listet beim Erstellen eines SCEP-Konfigurationsprofils die aktuellen Variablen auf. 

Gilt für: Windows 10 und höher sowie iOS, für WLAN unterstützt

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Remotesperren nicht konformer Geräte <!-- 2064495 -->
Wenn ein Gerät nicht konform ist, können Sie eine Aktion in der Konformitätsrichtlinie erstellen, die das Gerät remote sperrt. Erstellen Sie in Intune > **Gerätekonformität** eine neue Richtlinie, oder wählen Sie eine vorhandene Richtlinie > **Eigenschaften** aus. Wählen Sie **Aktionen bei Inkompatibilität** > **Hinzufügen** und dann das Remotesperren des Geräts aus.
Unterstützt auf: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 und höher 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Verbesserungen des Kioskprofils im Azure-Portal für Windows 10 und höher <!-- 2748224 -->
Dieses Update umfasst die folgenden Verbesserungen am Windows 10-Kiosk-Gerätekonfigurationsprofil (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** für Plattform > **Kioskvorschau** für Profiltyp): 
- Derzeit können Sie mehrere Kioskprofile auf demselben Gerät erstellen. Ab diesem Update unterstützt Intune nur ein Kioskprofil pro Gerät. Wenn Sie noch mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen benutzerdefinierten URI verwenden.
- In einem **Multi-App-Kioskprofil** können Sie die Anwendungskachelgröße und Reihenfolge für das **Startmenülayout** im Raster der Anwendung auswählen. Wenn Sie eine umfassendere Anpassung bevorzugen, können Sie weiterhin eine XML-Datei hochladen.
- Die Kioskbrowsereinstellungen werden in die **Kiosk**-Einstellungen verschoben. Derzeit haben die **Kioskwebbrowser**-Einstellungen ihre eigene Kategorie im Azure-Portal.
Gilt für: Windows 10 und höher




### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Anwenden des Autopilot-Profils auf Win 10-Geräte, die noch nicht für Autopilot registriert sind <!-- 1558983 -->
Sie können Autopilot-Profile auf registrierte Win 10-Geräte anwenden, die noch nicht für Autopilot registriert sind. Wählen Sie im Autopilot-Profil die Option **Alle Zielgeräte in Autopilot-Geräte konvertieren** aus, um Nicht-Autopilot-Geräte automatisch mit dem Autopilot-Bereitstellungsdienst zu registrieren. Die Verarbeitung der Registrierung kann 48 Stunden dauern. Wenn die Registrierung des Geräts aufgehoben und es zurückgesetzt ist, stellt Autopilot es bereit.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Erstellen und Zuweisen mehrerer Profile für Registrierungsstatusseiten für Azure AD-Gruppen <!-- 2526564 -->
Sie haben jetzt folgende Möglichkeit: [Erstellen und Zuweisen](windows-enrollment-status.md) mehrerer Registrierungsstatus-Seitenprofile für Azure ADD-Gruppen.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migration vom Programm zur Geräteregistrierung zum Apple Business Manager in Intune <!--2748613-->
Der Apple Business Manager (ABM) ist mit Intune konform, und Sie können ein Upgrade für Ihr Konto vom Programm zur Geräteregistrierung (Device Enrollment Program, DEP) zum ABM durchführen. Der Prozess in Intune ist identisch. Um ein Upgrade für Ihr Apple-Konto vom DEP zum ABM durchzuführen, rufen Sie [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817) auf.

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Registerkarten für Warnungen und Registrierungsstatus auf der Übersichtsseite der Geräteregistrierung <!--2748656-->
Warnungs- und Registrierungsfehler werden jetzt auf separaten Registerkarten auf der Übersichtsseite für die Geräteregistrierung angezeigt.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Einschränken von Apps und Blockieren des Zugriffs auf Unternehmensressourcen auf Android-Geräten <!-- 2451462  -->  
In **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** > **Systemsicherheit** gibt es eine neue Einstellung unter dem Abschnitt *Gerätesicherheit* namens **Eingeschränkte Apps**. Die Einstellung **Eingeschränkte Apps** verwendet eine Konformitätsrichtlinie, um den Zugriff auf Unternehmensressourcen zu blockieren, wenn bestimmte Apps auf dem Gerät erstellt werden. Das Gerät wird so lange als nicht kompatibel betrachtet, bis die eingeschränkten Apps von diesem Gerät entfernt werden.
Gilt für: 
- Android

<!-- ########################### -->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
