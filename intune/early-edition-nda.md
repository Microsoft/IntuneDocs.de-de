---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab6c808fc860491ddece5751983071d40864c8dd
ms.sourcegitcommit: 8f68cd3112a71d1cd386da6ecdae3cb014d570f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39575082"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Early Edition für Microsoft Intune – August 2018

> [!Note]
> Benachrichtigung zum Geheimhaltungsvertrag: Die folgenden Änderungen befinden sich in der Entwicklung für Intune. Die Freigabe dieser Informationen erfolgt im Geheimhaltungsvertrag (GHV) auf einer sehr begrenzten Basis. Posten Sie keine der folgenden Informationen in sozialen Medien oder auf öffentlichen Websites wie Twitter, UserVoice, Reddit usw. 

Die **Early Edition** enthält eine Liste der Features, die im Rahmen des Geheimhaltungsvertrags freigegeben und in späteren Releases von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Verfassen Sie außerhalb Ihres Unternehmens keinen Tweet oder Post auf UserVoice o.Ä. über diese Informationen. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello ist für Benutzer und Geräte konzipiert <!-- 1106609 -->
Wenn Sie eine [Windows Hello for Business](windows-hello.md)-Richtlinie erstellen, gilt diese für alle Benutzer innerhalb der Organisation (mandantenweit). Mit diesem Update kann die Richtlinie mithilfe einer Gerätekonfigurationsrichtlinie (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Identity Protection** > **Windows Hello for Business**) auch auf bestimmte Benutzer oder Geräte angewendet werden.

In Intune im Azure-Portal sind die Windows Hello-Konfiguration und die dazugehörigen Einstellungen jeweils unter **Geräteregistrierung** und **Gerätekonfiguration** verfügbar. Die **Geräteregistrierung** ist für die gesamte Organisation (mandantenweit) konzipiert und unterstützt Windows AutoPilot (OOBE). Die **Gerätekonfiguration** ist für Geräte und Benutzer konzipiert, die eine Richtlinie verwenden, die während des Check-In angewendet wird.

Gilt für:  
- Windows 10 und höher
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Steuern des S Modus für Geräte unter Windows 10 und höher – Public Preview <!-- 1958649 -->
Sie können ein Gerätekonfigurationsprofil erstellen, das den S Modus auf einem Windows 10-Gerät deaktiviert oder den Benutzer davon abhält, den S Modus eines Geräts zu deaktivieren. Dieses Feature ist in Intune verfügbar. Navigieren Sie zu **Gerätekonfiguration** > **Profile** >  **Windows 10 und höher** > **Edition upgrade and mode switch** (Editionsupgrade und Moduswechsel).
Auf der Seite [Willkommen bei Windows 10 im S Modus](https://www.microsoft.com/windows/s-mode) finden Sie weitere Informationen zum S Modus.
Gilt für: Windows 10 und höher (1809 und höher)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Updates für die Unterstützung für modernes VPN für iOS <!-- 2459928, 1819876, and 2650856 -->
Ein zukünftiges Update unterstützt die folgenden iOS-VPN-Clients: 
- F5 Access (Version 3.0.1 und höher)
- Citrix SSO
- Palo Alto Networks GlobalProtect (Version 5.0 und höher). Ebenso in zukünftigen Updates:
- Vorhandene **F5 Access**-Verbindungstypen werden in **F5 Access Legacy** (pro Branding-Updates für F5) umbenannt.
- Vorhandene **Palo Alto Networks GlobalProtect**-Verbindungstypen werden in **Legacy Palo Alto Networks GlobalProtect** (pro Palo Alto-Branding-Updates) umbenannt. 

Vorhandene Profile mit diesen Verbindungstypen funktionieren weiterhin mit dem Legacyclient für VPN. Wenn Sie Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN oder Legacy Palo Alto Networks GlobalProtect mit iOS verwenden, sollten Sie zu den neuen Apps wechseln. Führen Sie diesen Wechsel so früh wie möglich aus, um sicherzustellen, dass der VPN-Zugriff für iOS-Geräte zugänglich ist, sobald diese ein Update auf iOS 12 durchführen.

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Sperren des Unternehmensportals im Einzelanwendungsmodus, bis sich Benutzer anmelden <!--1067692 --> 
Sie haben die Möglichkeit, das Unternehmensportal im Einzelanwendungsmodus auszuführen, wenn Sie einen Benutzer über das Unternehmensportal statt über den Setup-Assistenten während der DEP-Registrierung authentifizieren. Durch diese Option wird das Gerät sofort nach dem Abschluss des Setup-Assistenten gesperrt, sodass sich ein Benutzer anmelden muss, um auf das Gerät zuzugreifen. Durch diese Methode wird sichergestellt, dass das Gerät den Onboardingprozess abschließt und nicht in einem verwaisten Zustand ohne verknüpften Benutzer verbleibt.

### <a name="scope-tags-for-policies---1081974-eeready--"></a>Bereichsmarkierungen für Richtlinien <!--1081974 eeready-->

Sie können Bereichsmarkierungen erstellen, um den Zugriff auf Intune-Ressourcen einzuschränken. Fügen Sie einer Rollenzuweisung eine Bereichsmarkierung hinzu, und fügen Sie diese anschließend einem Konfigurationsprofil hinzu. Die Rolle hat nur Zugriff auf Ressourcen mit Konfigurationsprofilen, die über übereinstimmende Bereichsmarkierungen (oder keine Bereichsmarkierung) verfügen.
Um eine Bereichsmarkierung zu erstellen, klicken Sie auf **Intune-Rollen** > **Bereich (Markierungen)** > **Erstellen**.
Um einer Rollenzuweisung eine Bereichsmarkierung hinzuzufügen, klicken Sie auf **Intune-Rollen** > **Alle Rollen** > **Policy and Profile Manager** (Richtlinien- und Profil-Manager) > **Zuweisungen** > **Bereich (Gruppen)**.
Um eine Bereichsmarkierung zu einem Konfigurationsprofil hinzuzufügen, klicken Sie auf **Gerätekonfiguration** > **Profile**, wählen Sie ein Profil aus, und klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)**.

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Hinzufügen eines Benutzer- und Anzeigenamens zu einem AutoPilot-Gerät <!--1346521 -->
Eine zukünftige öffentliche Vorschauversion ermöglicht es Administratoren, einen Benutzer einem einzelnen AutoPilot-Gerät zuzuweisen.  Administratoren können Anzeigenamen auch vergeben, um den Benutzer zu begrüßen, wenn dieser sein Gerät mit AutoPilot einrichtet.

Gilt für: Windows Insider 1809 oder einen späteren Build (während der Vorschauversion).

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-Token, das von einer anderen MDM-Software verwendet wird <!-- 1488946 -->
Intune erkennt und zeigt Details an, wenn ein VPP-Token (Apple Volume Purchase Program) von Intune und einer anderen MDM-Software verwendet wird.

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Pakettunnelunterstützung für Pro-App-VPN-Profile für iOS für die benutzerdefinierten und Pulse Secure-Verbindungstypen <!-- 1520957 -->
Wenn Sie Pro-App-VPN-Profile für iOS verwenden, können Sie das Tunneln auf App-Ebene (app-proxy) oder auf Paketebene (packet-tunnel) nutzen. Diese Optionen stehen mit den folgenden Verbindungstypen zur Verfügung:
- Benutzerdefiniertes VPN
- Pulse Secure: Wenn Sie sich nicht sicher sind, welcher Wert benutzt werden soll, sehen Sie sich die Dokumentation Ihres VPN-Anbieters an.
Gilt für: iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler ist eine verfügbare Verbindung für VPN-Profile unter iOS <!-- 1769858 eeready -->
Wenn Sie ein VPN-Gerätekonfigurationsprofil für iOS erstellen (unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS**, wechseln Sie zu Plattform und dann zum Profiltyp **VPN**), sind mehrere Verbindungstypen vorhanden, einschließlich Cisco, Citrix usw. In einem zukünftigen Update wird Zscaler als Verbindungstyp hinzugefügt. 
Unter [VPN settings for devices running iOS (VPN-Einstellungen für Geräte unter iOS)](vpn-settings-ios.md) sind die verfügbaren Verbindungstypen aufgeführt.

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Blockieren von Registrierungen persönlicher Windows-Geräte <!-- 1849498 -->
Sie können persönliche Windows-Geräte von der Registrierung mit der [Verwaltung mobiler Geräte](windows-enroll.md) in Intune blockieren. Geräte, die mit dem [Intune-PC-Agent](manage-windows-pcs-with-microsoft-intune.md) registriert sind, können nicht über dieses Feature blockiert werden.
Klicken Sie auf **Geräteregistrierung** > **Geräteeinschränkungen**, um dieses Feature anzuzeigen.
Das Aktivieren dieser Einschränkung hat keine Auswirkungen auf Geräte, die bereits registriert sind.
Nachdem eine Einschränkung aktiviert wurde, überprüft Intune, ob alle neuen Windows-Registrierungsanforderungen als Unternehmensregistrierung autorisiert wurden. Die folgenden Methoden sind als Unternehmensregistrierung autorisiert:
- Der Benutzer, der sich registriert, verwendet ein [Konto für den Geräteregistrierungs-Manager]( device-enrollment-manager-enroll.md).

- Das Gerät wird über [Windows AutoPilot](enrollment-autopilot.md) registriert.
- Die IME-Nummer des Geräts ist unter **Geräteregistrierung** > **[Bezeichner von Unternehmensgeräten]( corporate-identifiers-add.md)** aufgeführt.
- Das Gerät wird über ein [Massenbereitstellungspaket](windows-bulk-enroll.md) registriert.
- Das Gerät wird über eine [automatische Registrierung von SCCM für die Co-Verwaltung](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management) registriert.
Nicht autorisierte Registrierungen werden blockiert.
Die folgenden Registrierungen werden von Intune als unternehmenseigen markiert. Da diese jedoch nicht die gerätespezifische Steuerung über den Intune-Administrator bieten, werden sie blockiert:
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) mit der [Azure Active Directory-Einbindung während der Windows-Einrichtung](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) mit der [Azure Active Directory-Einbindung bei der Windows-Einrichtung](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
Die folgenden persönlichen Registrierungsmethoden werden ebenso blockiert:
- [Automatische MDM-Registrierung](windows-enroll.md#enable-windows-10-automatic-enrollment) durch [Hinzufügen eines Geschäftskontos über die Windows-Einstellungen](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup).

- Die Option [MDM enrollment only]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) (Nur MDM-Registrierung) in den Windows-Einstellungen.

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Angeben von Computernamensmustern in einem AutoPilot-Profil <!--1849855-->
Sie können eine Vorlage für einen Computernamen angeben, um den [Computernamen](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) während der AutoPilot-Registrierung zu generieren und festzulegen. Nehmen Sie diese Einstellung im AutoPilot-Profil vor, das sich unter **Geräteregistrierung** > **Windows-Registrierung** > **Windows Autopilot Deployment-Dienst** > **Profile** befindet. Es können nur alphanumerische Zeichen und Zeichen mit Bindestrichen verwendet werden.
Gilt für: Windows Insider 1809 oder einen späteren Build (während der Vorschauversion).

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS-Versionsnummer und Buildnummer werden angezeigt <!-- 1892471 -->
Unter **Gerätekompatibilität** > **Gerätekompatibilität** wird die iOS-Betriebssystemversion angezeigt. In einem zukünftigen Update wird auch die Buildnummer angezeigt.
Wenn Sicherheitsupdates veröffentlicht werden, bleibt die Versionsnummer von Apple in der Regel unverändert bestehen, die Buildnummer wird jedoch aktualisiert. Durch Anzeigen der Buildnummer können Sie einfach überprüfen, ob ein Sicherheitsupdate installiert wird.

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Ausblenden der Kontoänderungsoptionen für Windows AutoPilot-Profile auf der Anmeldeseite für Geschäftskontos und der Domänenfehlerseite <!--1901669 -->
Eine öffentliche Vorschauversion enthält neue Windows AutoPilot-Profiloptionen für Administratoren zum Ausblenden der Kontoänderungsoptionen auf der Anmeldeseite für Geschäftskontos und auf der Domänenfehlerseite. Für das Ausblenden dieser Optionen muss das Unternehmensbranding in Azure Active Directory konfiguriert sein. Gilt für: Windows Insider 1809 oder einen späteren Build (während der Vorschauversion).

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Verzögerung, wenn iOS-Softwareupdates auf dem Gerät angezeigt werden <!-- 1949583 -->
Sie können in Intune unter **Softwareupdates** > **Update policies for iOS** (Updaterichtlinien für iOS) die Tage und Uhrzeiten konfigurieren, an denen die Geräte keine Updates installieren sollen. In einem zukünftigen Update können Sie einen Zeitraum von 1 bis 90 Tagen einstellen, in dem ein Softwareupdate auf dem Gerät angezeigt wird. 
Unter [Configure iOS update policies in Microsoft Intune (Konfigurieren von iOS-Updaterichtlinien in Microsoft Intune)](software-updates-ios.md) sind die aktuellen Einstellungen aufgeführt.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Abgekoppelte Geräte im Gerätekonformitätsdashboard <!-- 1981119 -->
In einem zukünftigen Update werden abgekoppelte Geräte aus dem Gerätekonformitätsdashboard entfernt. Dadurch werden Ihre Konformitätsnummern geändert.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968 -->
Der Unternehmensportalwebsite werden auf der Grundlage von Kundenfeedback neue Features hinzugefügt. Dadurch werden auf Android-, iOS- und Windows-Geräten bereits vorhandene Funktionen verbessert, und die Benutzerfreundlichkeit erhöht sich. Bestimmte Bereiche der Website – z.B. Gerätedetails, Feedback und Support sowie die Geräteübersicht – werden mit einem neuen, modernen und dynamischen Design ausgestattet. Weiterhin sind enthalten:
- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- eine benutzerfreundlichere Sprache und weniger Fachbegriffe
- Möglichkeit, direkte Links zu Apps zu teilen
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 ProPlus-Version <!-- 2213968 eeready -->
Wenn Sie Ihren Windows 10-Geräten Office 365 ProPlus-Apps über Intune hinzufügen, können Sie die Office-Version auswählen. Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Apps** > **App hinzufügen**. Wählen Sie dann in der **Typ**-Dropdownliste die Option **Office 365 ProPlus-Suite (Windows 10)** aus. Klicken Sie auf **Einstellungen der App-Suite**, um das entsprechende Blatt anzuzeigen. Legen Sie den **Updatekanal** auf einen Wert fest, z.B. **Monatlich**. Entfernen Sie optional andere Office-Versionen (msi) von den Endbenutzergeräten, indem Sie auf **Yes** (Ja) klicken. Wählen Sie **Specific** (Spezifisch) aus, um eine bestimmte Office-Version für den ausgewählten Kanal oder die Endbenutzergeräte zu installieren. Zu diesem Zeitpunkt können Sie die **spezifische Version** von Office auswählen, die verwendet werden soll. Die verfügbaren Versionen werden im Laufe der Zeit geändert. Wenn Sie eine neue Bereitstellung erstellen, können deshalb die verfügbaren Versionen aktueller sein, und bestimmte ältere Versionen sind möglicherweise nicht mehr verfügbar. Für aktuelle Bereitstellungen sind weiterhin die älteren Versionen verfügbar, jedoch wird die Liste mit den Versionen nicht ständig pro Kanal aktualisiert. Weitere Informationen finden Sie unter [Übersicht über die Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Konfigurieren des Profils zum Überspringen einiger Bildschirme während des Setup-Assistenten <!-- 2276470 -->
Wenn Sie ein macOS-Registrierungsprofil erstellen, können Sie dieses konfigurieren, um folgende Bildschirme zu überspringen, wenn ein Benutzer den Setup-Assistenten durchläuft:
- Android-Migration
- Anzeigefarbton
- Datenschutz
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Änderungen im Updateprozess für lokale Connectors <!-- 2277554 -->
Auf Grundlage von Kundenfeedback wird die Art und Weise, wie Updates für lokale Connectors ausgeführt werden, geändert. Nachdem Sie erstmalig einen lokalen Connector installiert haben, werden Updates automatisch ausgeführt. Diese Änderung beginnt mit dem neuen PFX Certificate Connector für Microsoft Intune und wird dann langsam auf andere Typen lokaler Connectors ausgeweitet. 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Unterstützung für das Registrieren von DNS-Einstellungen für Windows 10-VPN <!-- 2282852 -->
Sie können VPN-Profile für Windows 10 konfigurieren, um die IP-Adressen dynamisch zu registrieren, die der VPN-Schnittstelle mit internem DNS zugewiesen sind, ohne benutzerdefinierte Profile verwenden zu müssen.
In den [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) sind die aktuell verfügbaren VPN-Profileinstellungen aufgeführt. 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>Einschränken von Apps und Blockieren des Zugriffs auf Unternehmensressourcen auf iOS- und Android for Work-Geräten <!-- 2451462 -->
Unter **Gerätekompatibilität** > **Richtlinien** > **Richtlinie erstellen** > **Android for Work** > **Systemsicherheit** ist eine neue Einstellung verfügbar: **Restricted applications** (Eingeschränkte Anwendungen). Diese neue Einstellung verwendet eine Konformitätsrichtlinie, um den Zugriff auf Unternehmensressourcen zu blockieren, wenn bestimmte Apps auf dem Gerät erstellt werden. Das Gerät wird so lange als nicht kompatibel betrachtet, bis die eingeschränkten Apps von diesem Gerät entfernt werden.
Gilt für: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Exportieren der Konformitätsrichtlinien des klassischen Azure-Portals in eine CSV-Datei <!-- 2469637 -->
Konformitätsrichtlinien, die im klassischen Azure-Portal erstellt wurden, werden als veraltet markiert.  In diesem Fall können Sie vorhandenen Richtlinien überprüfen und löschen. Diese Richtlinien können jedoch nicht aktualisiert werden. Sie können diese Richtlinien als durch Trennzeichen getrennte Datei (CSV-Datei) exportieren. Verwenden Sie anschließend die Informationen in der Datei, um die Richtlinien im Intune Azure-Portal neu zu erstellen.
> [!IMPORTANT]
> Wenn das klassische Azure-Portal eingestellt wird, können Sie nicht mehr auf Ihre Richtlinien zugreifen und diese auch nicht anzeigen. Exportieren Sie sie deshalb auf jeden Fall, und erstellen Sie sie im Azure-Portal neu, bevor das klassische Azure-Portal eingestellt wird.

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Weitere Synchronisierungsoptionen in der Unternehmensportal-App für Windows <!-- 2683177 -->
In der Unternehmensportal-App für Windows wird eine neue Gerätesynchronisierungsaktion zu den Sprunglisten der Windows-Taskleiste und dem Startmenü hinzugefügt. Navigieren Sie zu einer dieser Optionen, um Ihre Geräte schnell zu synchronisieren und Zugriff auf Unternehmensressourcen zu erhalten.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Zurücksetzen von Gerätekennungen über die Unternehmensportal-App für Windows 10 <!-- 2101282 --> 
Ihre Mitarbeiter können schon bald die PIN bzw. die Kennung ihres Geräts direkt über die Unternehmensportal-App für Windows 10 zurücksetzen. Diese Funktion ist dann jeweils auf remoten und lokal verwalteten Intune-Geräten verfügbar, die Zurücksetzungen der Kennung unterstützen. Je nach Gerätetyp entfernt eine Anforderung, die für ein Remotegerät gestellt wird, entweder die aktuelle Kennung des Geräts oder erstellt eine temporäre Kennung. Benutzer, die eine Zurücksetzung für ein lokales Gerät anfordern, werden an die App „Einstellungen“ des Geräts weitergeleitet.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Geänderte Durchsuchen-Funktion in der Unternehmensportal-App für Windows <!-- 2317227 -->  
Beim Durchsuchen oder Suchen nach Apps in der Unternehmensportal-App für Windows können Sie zwischen der Ansicht **Kacheln** und der neu hinzugefügten Ansicht **Details** wechseln. In der neuen Ansicht werden Details zu Anwendungen wie Namen, Herausgeber, Veröffentlichungsdatum und Installationsstatus angezeigt.  

Auf der Seite **Apps** wird die Ansicht **Installiert** hinzugefügt, über die Sie Details zu abgeschlossenen und laufenden App-Installationen anzeigen können. Möchten Sie uns Ihre Meinung oder Anregungen zu den neuesten Änderungen mitteilen? Über die Unternehmensportal-App können Sie uns Feedback senden.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Verbesserungen an den Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager <!-- 675800 -->
Wenn ein Geräteregistrierungs-Manager (DEM) sich in der Unternehmensportal-App für Windows anmeldet, listet die App nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserungen werden Timeouts vermindert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte zu laden.  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Verwendung von VPP-Gerätelizenzen, zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung <!-- 1608345 -->
Sie können Gerätelizenzen des Volume Purchase Program (VPP) verwenden, um das Unternehmensportal während der Registrierungsvorgänge des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) vorab bereitzustellen. Geben Sie dazu bei der Erstellung oder Bearbeitung eines Registrierungsprofils das VPP-Token an, das Sie zum Installieren des Unternehmensportals verwenden möchten. Stellen Sie sicher, dass Ihr Token nicht abläuft, und dass Sie über genügend Lizenzen für die Unternehmensportal-App verfügen. In Fällen, in denen das Token abläuft oder über keine Lizenzen mehr verfügt, überträgt Intune stattdessen das App Store-Unternehmensportal mithilfe von Push (dafür ist die Eingabe eine Apple-ID erforderlich).

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Dateierweiterung branchenspezifischer Windows-Apps (LOB-Apps) <!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps umfassen jetzt *.msi*, *.appx*, *.appxbundle*, *.msix* und *.msixbundle*. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Mobile Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Das automatisch dem Konfigurationsprofil zugewiesene Windows Defender ATP-Konfigurationspaket <!-- 2144658 -->
Wenn Sie [Advanced Threat Protection verwenden und Geräte in Intune onboarden](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile), laden Sie derzeit ein Konfigurationspaket herunter und fügen es Ihrem Konfigurationsprofil hinzu. In einem zukünftigen Update ruft Intune das Paket automatisch aus dem Windows Defender Security Center ab und fügt es Ihrem Profil hinzu.

Gilt für Windows 10 und höher.

### <a name="check-for-sccm-compliance----2192052---"></a>Überprüfung auf SCCM-Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (SCCM) (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). SCCM sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle SCCM-Signale auffordern, „compliant“ (konform) zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. In SCCM hat diese Anforderung den Zustand „Installed“ (Installiert). Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und wenn die Lizenzen für das Unternehmensportal knapp werden.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Erforderliche Bestätigung zur Löschung von VPP-Token, die für die Vorabbereitstellung des Unternehmensportals verwendet werden <!-- 2237634 -->
Für die Löschung eines VPP-Tokens (Volume Purchase Program) ist eine Bestätigung notwendig, falls das Token zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwendet wird.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Zusätzliche Sicherheitseinstellungen für Windows Installer <!-- 2282430 -->
Sie können Benutzern erlauben, App-Installationen zu steuern. Wenn diese Option aktiviert ist, werden Installationen, die normalerweise wegen Sicherheitsverstößen unterbrochen werden würden, weiterhin ausgeführt. Sie können festlegen, dass Windows Installer bei der Installation eines beliebigen Programms auf einem System erhöhte Berechtigungen verwendet. Zusätzlich können Sie festlegen, dass Windows Information Protection-Elemente (WIP) indiziert und die zugehörigen Metadaten an einem nicht verschlüsselten Speicherort gespeichert werden. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente weder indiziert noch in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Diese Optionen sind standardmäßig deaktiviert. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können zukünftig auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts <!-- 1506985 -->

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, mobile Anwendungsverwaltung) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968 -->
Die Unternehmensportalwebsite bzw. der iOS-App-Katalog wird auf der Grundlage von Kundenfeedback um neue Features ergänzt. Dadurch werden auf Android-, iOS- und Windows-Geräten bereits vorhandene Funktionen verbessert, und die Benutzerfreundlichkeit erhöht sich. Bestimmte Bereiche der Website – z.B. Gerätedetails, Feedback und Support sowie die Geräteübersicht – werden mit einem neuen, modernen und dynamischen Design ausgestattet. Weiterhin sind enthalten:

- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- eine benutzerfreundlichere Sprache und weniger Fachbegriffe
- Möglichkeit, direkte Links zu Apps zu teilen
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer

Das Update ist derzeit als Vorschauversion verfügbar. Sie können sich unter http://aka.ms/webcpflighting für die Vorschauversion registrieren.

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts <!-- 1506985 --> 

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird zukünftig die Sicherheit von MAM-fähigen Apps durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Die Möglichkeit, erforderliche branchenspezifische Apps (LOB) für alle Benutzer von Windows 10 Desktop-Geräten bereitzustellen <!-- 1627835 RS4 -->.
Kunden können erforderliche branchenspezifische Apps unter Windows 10 bereitstellen, um in Gerätekontexte zu installieren. Dadurch können diese Apps für alle Benutzer auf dem Gerät verfügbar sein. Dies gilt nur für Windows 10 Desktop-Geräte.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aktualisieren der „Hilfe und Feedback“-Oberfläche in der Unternehmensportal-App für Android <!--1631531 -->

Die „Hilfe und Feedback“-Benutzeroberfläche in der Unternehmensportal-App für Android wird zukünftig aktualisiert, um den Best Practices für Android-Apps zu entsprechen. Die Unternehmensportal-App für Android wird in den nächsten Monaten aktualisiert. Das **Hilfe und Feedback**-Menüelement wird in die Menüelemente **Hilfe** und **Feedback senden** unterteilt. Auf der **Hilfe**-Seite wird es einen **Häufig gestellte Fragen**-Abschnitt und eine **E-Mail-Support**-Schaltfläche zum Hochladen von Protokollen an Microsoft und Senden von E-Mails an die Supportabteilung Ihres Unternehmens geben, in denen die Probleme beschrieben werden. Die Option **Feedback senden** führt den Benutzer durch den Standardprozess zur Feedbackübermittlung von Microsoft, in dem der Benutzer angeben kann, ob ihm etwas gefällt, nicht gefällt und Vorschläge machen kann.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



