---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titlesuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: ed6a79142c2bbe3bd93b02c17e92f4f11f2583f3
ms.sourcegitcommit: b93db06ba435555f5b126f97890931484372fcfb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829197"
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Sie erhalten auch Informationen zu bevorstehenden Änderungen, [wichtige Hinweise](#notices) und Informationen zu [früheren Releases](whats-new-archive.md). Einige Features werden im Laufe mehrerer Wochen bereitgestellt und sind in der ersten Woche möglicherweise nicht für alle Kunden verfügbar.

> [!Note]
> Informationen zu neuen Funktionen der hybriden Verwaltung mobiler Geräte (MDM) finden Sie auf der Seite [Neuheiten bei der hybriden Verwaltung mobiler Geräte](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     

## <a name="week-of-november-26-2018"></a>Woche vom 26. November 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Deinstallieren von Apps auf unternehmenseigenen überwachten iOS-Geräten<!-- 1281677 -->

Sie können beliebige unternehmenseigene überwachte iOS-Geräte entfernen. Sie können eine beliebige App entfernen, indem Sie entweder Benutzer- oder Gerätegruppen mit dem Zuweisungstyp **Deinstallieren** als Ziel verwenden. Für persönliche oder nicht überwachte iOS-Geräte können weiterhin nur Apps entfernt werden, die mit Intune installiert wurden.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Herunterladen der Intune Win32-App-Inhalte <!-- 2617320 -->
Clients von Windows 10 RS3 und höher laden Intune Win32-App-Inhalte mit einer Komponente zur Übermittlungsoptimierung auf den Windows 10-Client herunter. Die Übermittlungsoptimierung bietet Peer-zu-Peer-Funktionen, die standardmäßig eingeschaltet sind. Die Übermittlungsoptimierung kann mit einer Gruppenrichtlinie und in der Zukunft über Intune MDM konfiguriert werden. Weitere Informationen finden Sie unter [Übermittlungsoptimierung für Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Endbenutzergeräte- und App-Inhaltsmenü <!-- 2771453 -->
Endbenutzer können jetzt über das Kontextmenü auf Geräten und in Apps häufig verwendete Aktionen auslösen, z.B. das Umbenennen eines Geräts oder die Prüfung der Konformität.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Festlegen eines benutzerdefinierten Hintergrunds in der Managed Home Screen-App <!-- 3041945 -->
Es wird eine Einstellung hinzugefügt, mit der Sie den Hintergrund der Managed Home Screen-App auf Android Enterprise-, Multi-App- und Kioskmodusgeräten anpassen können.  Um eine **URL für einen benutzerdefinierten Hintergrund** zu konfigurieren, wechseln Sie im Azure-Portal zu Intune und dann zur Gerätekonfiguration. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Speichern und Anwenden von App-Schutzrichtlinienzuweisungen <!-- 3104570 -->
Sie erhalten jetzt eine bessere Kontrolle über Ihre [App-Schutzrichtlinienzuweisungen](app-protection-policies.md#deploy-a-policy-to-users). Wenn Sie *Zuweisungen* auswählen, um die Zuweisungen einer Richtlinie festzulegen oder zu bearbeiten, müssen Sie Ihre Konfiguration **speichern**, bevor die Änderung angewendet wird. Löschen Sie mit **Verwerfen** alle Änderungen, die Sie vornehmen, ohne Änderungen in den Listen zum Einschließen oder Ausschließen zu speichern.  Wenn Speichern oder Verwerfen erforderlich ist, werden nur die von Ihnen vorgesehenen Benutzer einer App-Schutzrichtlinie zugewiesen.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Neue Microsoft Edge-Browsereinstellungen für Windows 10 und höher <!-- 3174639 -->
Dieses Update enthält neue Einstellungen, die Sie dabei unterstützen, den Microsoft Edge-Browser auf Ihren Geräten zu steuern und zu verwalten. Eine Liste dieser Einstellungen finden Sie in den [Geräteeinschränkungen für Windows 10 (und höher)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Neue Apps-Unterstützung mit App-Schutzrichtlinien <!-- 3330037 -->
Sie können jetzt die folgenden Apps mit [Intune-App-Schutzrichtlinien](app-protection-policies.md) verwalten:
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Verwenden Sie App-Schutzrichtlinien, um für diese Apps Unternehmensdaten zu schützen und die Datenübertragung zu steuern, wie andere richtlinienverwaltete Intune-Apps. Hinweis: Wenn Flow noch nicht in der Konsole sichtbar ist, fügen Sie Flow beim Erstellen oder Bearbeiten von App-Schutzrichtlinien hinzu. Verwenden Sie hierzu die Option **+ Weitere Apps**, und geben Sie dann die *App-ID* für Flow in das Eingabefeld ein. Verwenden Sie für Android *com.microsoft.flow* und für iOS *com.microsoft.procsimo*.

#### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Aktualisierte Benutzeroberfläche für Intune-App-Schutzrichtlinien <!-- 3251427 -->
Wir haben die Bezeichnungen für Einstellungen und Schaltflächen für den Intune-App-Schutz geändert, um die Verständlichkeit zu erleichtern. Einige Änderungen sind:  

- **Ja** / **Nein**-Steuerelemente wurden in erster Linie in **Blockieren** / **Zulassen**- und **Deaktivieren** / **Aktivieren**-Steuerelemente geändert. Die Bezeichnungen wurden ebenfalls aktualisiert.  
- Einstellungen wurden darüber hinaus neu formatiert, um die Einstellungen und ihre Bezeichnungen im Steuerelement nebeneinander anzuzeigen und eine bessere Navigation zu ermöglichen.   

Die Standardeinstellungen und die Anzahl von Einstellungen bleiben gleich, aber durch die oben genannten Änderungen werden Verständlichkeit, Navigation und Verwendung der Einstellungen verbessert, um dem Benutzer eine einfachere Anwendung der ausgewählten App-Schutzrichtlinien zu ermöglichen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Die iOS- und macOS-Versionsnummern und -Buildnummern werden angezeigt <!-- 1892471 -->
Unter **Gerätekonformität** > **Gerätekonformität** wird die iOS-und macOS-Betriebssystemversion angezeigt, für die Konformitätsrichtlinien verwendet werden können. Dieses zukünftige Update umfasst auch die Buildnummer, die für beide Plattformen konfigurierbar ist.
Wenn Sicherheitsupdates veröffentlicht werden, bleibt die Versionsnummer von Apple in der Regel unverändert bestehen, die Buildnummer wird jedoch aktualisiert. Wenn Sie die Buildnummer in einer Konformitätsrichtlinie verwenden, können Sie einfach überprüfen, ob ein Sicherheitsupdate installiert wurde.
Wie Sie dieses Feature verwenden, erfahren Sie in den [iOS](compliance-policy-create-ios.md#device-health)- und [macOS](compliance-policy-create-mac-os.md#device-properties)-Konformitätsrichtlinien.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Updateringe werden mit Einstellungen zur Übermittlungsoptimierung für Windows 10 und höher ersetzt <!-- 2753807 -->
Die Übermittlungsoptimierung ist ein neues Konfigurationsprofil für Windows 10 und höher. Diese Funktion bietet eine optimierte Benutzeroberfläche zum Übermitteln von Softwareupdates an Geräte in Ihrer Organisation. Mit diesem Update können Sie die Einstellungen auch mithilfe eines Konfigurationsprofils an neue und vorhandene Updateringe übermitteln.
Wie Sie ein Konfigurationsprofil für die Übermittlungsoptimierung konfigurieren, erfahren Sie unter [Einstellungen zur Übermittlungsoptimierung in Microsoft Intune in Windows 10 (und höher)](delivery-optimization-windows.md).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Auswählen von Apps zur Nachverfolgung auf der Seite mit dem Registrierungsstatus <!-- 2531007 -->
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
Eine neue gerätebasierte Abonnement-SKU ist nun verfügbar, mit der die Kosten für die Geräteverwaltung in Unternehmen reduziert werden können. Diese SKU für Intune-Geräte wird monatlich pro Gerät lizenziert. Der Preis hängt vom Lizenzierungsprogramm ab. Die SKU ist in den Lizenzierungsprogrammen Direct Channel, Enterprise Agreement (EA), Microsoft Products and Services Agreement (MPSA), Open License und Cloud Solution Provider (CSP) verfügbar.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Temporäres Anhalten des Kioskmodus auf Android-Geräten zum Durchführen von Änderungen <!-- 3041935 -->
Bei Verwendung von Android-Geräten im Multi-App-Kioskmodus kann es erforderlich werden, dass ein IT-Administrator Änderungen am Gerät vornimmt. Dieses Update beinhaltet eine neue Multi-App-Kioskeinstellung, die dem IT-Administrator erlaubt, den Kioskmodus unter Verwendung einer PIN temporär anzuhalten und Zugriff auf das gesamte Gerät zu erhalten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Aktivieren einer virtuellen Startschaltfläche auf Android Enterprise-Kioskgeräten <!-- 3042021 -->
Eine neue Einstellung erlaubt es den Benutzern, auf ihrem Gerät auf einen Softkey zu tippen, um auf ihrem Multi-App-Kioskgerät zwischen der Managed Home Screen-App und anderen zugewiesenen Apps zu wechseln. Diese Einstellung ist insbesondere dann nützlich, wenn eine Kiosk-App des Benutzers nicht ordnungsgemäß auf die ZURÜCK-Taste reagiert. Sie können diese Einstellung für unternehmenseigene, einzeln genutzte Android-Geräte konfigurieren. Wechseln Sie im Azure-Portal zu Intune und anschließend zur Gerätekonfiguration, um die Einstellung **Virtuelle Startschaltfläche** zu aktivieren oder zu deaktivieren. Wählen Sie ein aktuelles Gerätekonfigurationsprofil aus, oder erstellen Sie ein neues Profil, um die zugehörigen Kioskeinstellungen zu bearbeiten.
Informationen zu den Kioskeinstellungen finden Sie unter [Einstellungen für Geräteeinschränkungen für Android Enterprise](device-restrictions-android-for-work.md).

## <a name="week-of-november-12-2018"></a>Woche vom 12. November 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Unterstützung für die Netzwerkzugriffssteuerung (Network Access Control, NAC) für Citrix SSO für iOS<!-- 3259404 -->

Citrix hat ein Update für Citrix Gateway veröffentlicht, um die Netzwerkzugriffssteuerung (Network Access Control, NAC) für Citrix SSO für iOS in Intune zu ermöglichen. Sie können eine Geräte-ID in einem VPN-Profil in Intune einschließen und dieses Profil dann mithilfe von Push an Ihre iOS-Geräte übertragen. Sie müssen das neueste Update für Citrix Gateway installieren, um diese Funktion nutzen zu können.

Der Artikel [Konfigurieren von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune](vpn-settings-ios.md#base-vpn-settings) enthält weitere Informationen zur Verwendung der NAC sowie einige zusätzliche Anforderungen. 

## <a name="week-of-november-5-2018"></a>Woche vom 5. November 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Unterstützung für iOS 12 OAuth in iOS-E-Mail-Profilen <!--2155106 -->

Die iOS-E-Mail-Profile in Intune unterstützen nun Open Authorization (OAuth) für iOS 12. Wenn Sie dieses Feature verwenden möchten, erstellen Sie ein neues Profil (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **E-Mail** (Profiltyp)), oder aktualisieren Sie ein vorhandenes iOS-E-Mail-Profil. Wenn Sie OAuth in einem Profil aktivieren, das bereits für Benutzer bereitgestellt wurde, werden die Benutzer zur erneuten Authentifizierung und zum Erneuten Herunterladen ihrer E-Mails aufgefordert.

Unter [Einstellungen für E-Mail-Profile für iOS-Geräte](email-settings-ios.md) finden Sie weitere Informationen zur Verwendung von OAuth für E-Mail-Profile.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Autopilot-Unterstützung für in Azure Active Directory Hybrid eingebundene Geräte (Vorschau)<!-- 1048100-->
Sie können ab sofort in Azure Active Directory Hybrid eingebundene Geräte mithilfe von Autopilot einrichten. Geräte müssen mit dem Netzwerk Ihres Unternehmens verbunden sein, um das Hybrid-Autopilot-Feature nutzen zu können. Weitere Informationen finden Sie unter [Bereitstellen von in Azure AD Hybrid eingebundenen Geräten mit Intune und Windows Autopilot](windows-autopilot-hybrid.md).
Dieses Feature wird in den nächsten Tagen für Benutzer eingeführt. Daher können Sie diese Schritte möglicherweise erst ausführen, wenn es für Ihr Konto eingeführt wurde.

## <a name="week-of-october-29-2018"></a>Woche vom 29. Oktober 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Anfordern der nicht biometrischen PIN nach angegebenem Timeout <!-- 1506985 -->
Durch die erzwungene Verwendung einer nicht biometrischen PIN nach einem vom Administrator festgelegten Zeitraum wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, Verwaltung mobiler Anwendungen) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen. Weitere Informationen zu den Zugriffseinstellungen finden Sie unter [iOS-Einstellungen](app-protection-policy-settings-ios.md#access-settings) und [Android-Einstellungen](app-protection-policy-settings-android.md#access-settings).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Intune-APP-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten <!-- 2244713 -->
Sie können die Steuerung der Intune-App-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten von der Angabe der Identität des registrierten Benutzers (auch als Benutzerprinzipalname (UPN) bekannt) trennen. Administratoren, die IntuneMAMUPN nicht verwenden, werden keine Verhaltensänderung feststellen. Wenn diese Funktion verfügbar ist, sollten Administratoren, die mit IntuneMAMUPN das Datenübertragungsverhalten auf registrierten Geräten steuern, die neuen Einstellungen überprüfen und ihre APP-Einstellungen nach Bedarf aktualisieren.

#### <a name="windows-10-win32-apps----2617325---"></a>Win32-Apps unter Windows 10<!-- 2617325 -->
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

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Entfernen eines E-Mail-Profils von einem Gerät, auch wenn nur ein E-Mail-Profil vorhanden ist <!-- 1818139 -->
Zuvor konnte ein E-Mail-Profil nicht von einem Gerät entfernt werden, *wenn* es das einzige E-Mail-Profil war. Dies wurde mit dem vorliegenden Update geändert. Nun können Sie ein E-Mail-Profil entfernen, auch wenn es das einzige E-Mail-Profil auf dem Gerät ist. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell-Skripts und AAD <!-- 2309469 -->
PowerShell-Skripts in Intune können auf AAD-Gerätesicherheitsgruppen ausgerichtet werden.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Neue Standardeinstellung „Erforderlicher Kennworttyp“ für Android, Android Enterprise<!-- 2649963 -->
Wenn Sie eine neue Konformitätsrichtlinie erstellen (**Intune** > **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** oder **Android Enterprise** für Plattform > Systemsicherheit), ändert sich der Standardwert für **Erforderlicher Kennworttyp**:

Von: Standardeinstellung für das Gerät – In: Mindestens numerisch

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

### <a name="android-device-owner-mode-support---3188762--"></a>Unterstützung für den Modus für Android-Geräteeigentümer <!--3188762-->
Für die Samsung Knox Mobile-Registrierung unterstützt Intune jetzt die Registrierung von Geräten im Verwaltungsmodus für Android-Geräteeigentümer. Benutzer mit einer WLAN- oder Mobilfunknetzverbindung können die Registrierung mit nur wenigen Tippbewegungen ausführen, wenn sie ihre Geräte zum ersten Mal einschalten. Weitere Informationen finden Sie unter [Automatisches Registrieren von Android-Geräten mit Samsung Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Geräteverwaltung

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Gruppieren von mit Windows Autopilot registrierten Geräten nach Korrelator-ID <!-- 2075110 -->
Intune unterstützt nun die Gruppierung von Windows-Geräten nach einer Korrelator-ID, wenn sie mit [Autopilot für bestehende Geräte](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) über den Configuration Manager registriert werden. Die Korrelator-ID ist ein Parameter der Autopilot-Konfigurationsdatei. Intune legt das [Azure AD-Geräteattribut „enrollmentProfileName“](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) automatisch auf „OfflineAutopilotprofile-<correlator ID>“ fest. Dadurch können beliebige dynamische Azure AD-Gruppen basierend auf der Korrelator-ID über das Attribut „enrollmentprofileName“ für Offlineregistrierungen von Autopilot erstellt werden. Weitere Informationen finden Sie unter [Windows Autopilot für vorhandene Geräte](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

### <a name="intune-app-protection-policies----2984657---"></a>Intune-App-Schutzrichtlinien<!-- 2984657 -->
Mithilfe von Intune-App-Schutzrichtlinien können Sie verschiedene Einstellungen zum Schutz von Daten für mit Intune geschützte Apps konfigurieren, zum Beispiel Microsoft Outlook und Microsoft Word. Aussehen und Verhalten dieser Einstellungen wurden sowohl für [iOS](app-protection-policy-settings-ios.md) als auch für [Android](app-protection-policy-settings-android.md) geändert, um das Auffinden individueller Einstellungen zu erleichtern. Es gibt drei Kategorien von Richtlinieneinstellungen:
- **Datenverschiebung**: Diese Gruppe umfasst Steuerelemente zum Verhindern von Datenverlust, wie z.B. Einschränkungen für Ausschneiden, Kopieren, Einfügen und „Speichern unter“. Diese Einstellungen bestimmen, wie Benutzer mit Daten in den Apps interagieren können.
- **Zugriffsanforderungen**: Diese Gruppe enthält die PIN-Optionen pro App. Sie bestimmen, wie der Endbenutzer in einem Arbeitskontext auf die Apps zugreifen kann.  
- **Bedingter Start**: Diese Gruppe enthält Einstellungen wie z.B. die mindestens erforderliche Betriebssystemversion, Einstellungen zur Erkennung von Jailbreak und entfernten Nutzungsbeschränkungen und die Offlinetoleranzperiode.  
  
Die Funktionalität der Einstellungen ändert sich nicht, aber es wird einfacher sein, sie bei der Richtlinienerstellung zu finden.

### <a name="intune-apps"></a>Intune-Apps

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune-Unterstützung für eine maximale Paketgröße von 8 GB für LOB-Anwendungen <!-- 1727158 -->
Intune erhöht die maximale Paketgröße auf 8 GB für LOB-Anwendungen. Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Hinzufügen eines benutzerdefinierten Markenbildes für die Unternehmensportal-App <!-- 1916266 -->
Als Microsoft Intune-Administrator können Sie ein benutzerdefiniertes Markenbild hochladen, das als Hintergrundbild auf der Profilseite des Benutzers in der iOS-Unternehmensportal-App angezeigt wird. Weitere Informationen zum Konfigurieren der Unternehmensportal-App finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune behält die lokalisierte Sprache für Office bei, wenn Office auf den Computern der Endbenutzer aktualisiert wird <!-- 2971030 -->
Wenn Intune Office auf den Computern Ihrer Endbenutzer installiert, erhalten sie automatisch dieselben Sprachpakete wie bei früheren MSI-Office-Installationen. Weitere Informationen finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Neue Benutzeroberfläche für Intune-Support im Portal für die Microsoft 365-Geräteverwaltung <!-- 3076965 -->
Im [Portal für die Microsoft 365-Geräteverwaltung]( http://devicemanagement.microsoft.com) wird eine neue Benutzeroberfläche für „Hilfe und Support“ in Intune eingeführt. Über die neue Benutzeroberfläche können Sie Ihr Problem in eigenen Worten beschreiben und erhalten Einblicke in die Problembehandlung sowie webbasierte Anleitungen zur Selbsthilfe. Diese Lösungen werden über einen regelbasierten Algorithmus für maschinelles Lernen angeboten, der auf Benutzeranfragen basiert.  

Zusätzlich zur themenspezifischen Anleitung können Sie auch den neuen Workflow zur Fallerstellung nutzen, um einen Supportfall per E-Mail oder Telefon zu öffnen.  

Für Kunden, die am Rollout teilnehmen, ersetzt diese neue Benutzeroberfläche die aktuelle Ansicht für Hilfe und Support, die einen statischen Satz an vorab ausgewählten Optionen enthält. Diese basieren auf dem Bereich der Konsole, in dem Sie sich befinden, wenn Sie „Hilfe und Support“ öffnen.  

*Diese neue Benutzeroberfläche für Hilfe und Support steht derzeit ausgewählten Mandanten über das Portal für die Geräteverwaltung zur Verfügung. Die Teilnehmer für diese neue Benutzeroberfläche werden nach dem Zufallsprinzip aus den verfügbaren Intune-Mandanten ausgewählt. Neue Mandanten werden bei Erweiterung des Rollouts hinzukommen.*  

Weitere Informationen finden Sie in „Anfordern von Support für Microsoft Intune“ unter [Neue Benutzeroberfläche für Hilfe und Support](get-support.md#new-help-and-support-experience).  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Vorschauversion für das PowerShell-Modul für Intune verfügbar <!-- 951068 -->
Ein neues PowerShell-Modul, das über Microsoft Graph eine Unterstützung für die Intune-API bietet, ist nun als Vorschauversion auf [GitHub]( https://aka.ms/intunepowershell) verfügbar. Weitere Informationen zur Verwendung dieses Moduls finden Sie dort unter README. 


## <a name="week-of-october-15-2018"></a>Woche vom 15. Oktober 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>PIN-Eingabeaufforderung beim Ändern von Fingerabdrücken oder Gesichts-IDs auf einem iOS-Gerät <!-- 2637704  -->
Benutzer werden ab sofort zur Eingabe einer PIN aufgefordert, nachdem sie Änderungen an biometrischen Daten auf ihrem iOS-Gerät vorgenommen haben. Hierzu zählen Änderungen an registrierten Fingerabdrücken oder Gesichts-IDs. Die Zeitplanung für die Aufforderung hängt von der Konfiguration des Timeouts *Zugriffsanforderungen erneut prüfen nach (Minuten)* ab.  Wenn keine PIN festgelegt ist, wird der Benutzer aufgefordert, eine festzulegen. 
 
Dieses Feature ist nur für iOS verfügbar und erfordert, dass das Intune App SDK für iOS, Version 9.0.1 oder höher in betreffende Anwendungen integriert wird. Die Integration des SDK ist erforderlich, damit das Verhalten für die Zielanwendungen erzwungen werden kann. Diese Integration erfolgt kontinuierlich und ist abhängig von den jeweiligen Anwendungsteams. Zu den betreffenden Apps zählen z.B. WXP, Outlook, Managed Browser und Yammer.


## <a name="week-of-october-1-2018"></a>Woche vom 1. Oktober 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Zugriff auf wichtige Profileigenschaften über die Unternehmensportal-App <!-- 772203 -->
Endbenutzer können ab jetzt auf wichtige Eigenschaften und Aktionen über die Unternehmensportal-App zugreifen, z.B. die Kennwortzurücksetzung. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (Application Protection Policy, APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Benutzerkontozugriff von Intune-Apps auf verwalteten Android- und iOS-Geräten <!-- 1248496 -->
Wie der Microsoft Intune-Administrator können Sie steuern, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie können den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Konfigurationsrichtlinie für die Outlook-App für iOS und Android <!--1828527 -->
Ab sofort können Sie für lokale Benutzer, die die grundlegende Authentifizierung mit dem ActiveSync-Protokoll nutzen, eine Konfigurationsrichtlinie für die Outlook-App für iOS und Android erstellen. Zusätzliche Konfigurationseinstellungen werden hinzugefügt, sobald sie für Outlook für iOS und Android aktiviert werden.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Dateierweiterung branchenspezifischer Windows-Apps (LOB-Apps) <!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps umfassen jetzt *.msi*, *.appx*, *.appxbundle*, *.msix* und *.msixbundle*. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Client-Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Windows 10-App-Bereitstellung mit Intune <!-- 2309001 -->
Basierend auf der bestehenden Unterstützung für Branchenanwendungen (LOB) und Microsoft Store for Business-Apps können Administratoren mit Intune die meisten der vorhandenen Anwendungen ihres Unternehmens für Endbenutzer auf Windows 10-Geräten bereitstellen. Administratoren können Anwendungen für Windows 10-Benutzer in einer Vielzahl von Formaten wie MSI, Setup.exe oder MSP hinzufügen, installieren und deinstallieren. Intune wertet vor dem Herunterladen und Installieren, dem Benachrichtigen von Endbenutzern über den Status oder Neustartanforderungen die Anforderungsregeln über das Info-Center von Windows 10 aus. Diese Funktionalität wird Unternehmen, die daran interessiert sind, diesen Workload auf Intune und die Cloud zu verlagern, effektiv entlasten. Dieses Feature befindet sich derzeit in der öffentlichen Vorschauversion und wir erwarten, dass es in den nächsten Monaten um bedeutende neue Funktionen erweitert wird. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Endbenutzergeräte- und App-Inhaltsmenü <!-- 2771453 -->
Endbenutzer können nun das Kontextmenü für Geräte und Apps verwenden, um häufig verwendete Aktionen auszulösen, z.B. das Umbenennen eines Geräts oder die Überprüfung der Konformität. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Tastenkombinationen für die Windows-Unternehmensportal-App <!-- 2771518 -->
Endbenutzer können ab sofort mithilfe von Tastenkombinationen (Tastenkombinations-Editor) App- und Geräteaktionen in der Windows-Unternehmensportal-App auslösen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Erstellen von DNS-Suffixen in VPN-Konfigurationsprofilen auf Geräten mit Windows 10<!-- 1333668 -->
Beim Erstellen eines VPN-Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** Plattform > **VPN**-Profiltyp) geben Sie DNS-Einstellungen ein. Mit diesem Update können Sie auch mehrere **DNS-Suffixe** in Intune eingeben. Wenn Sie DNS-Suffixe verwenden, können Sie nach einer Netzwerkressource mithilfe ihres Kurznamens anstelle des vollqualifizierten Domänennamens (Fully Qualified Domain Name, FQDN) suchen. Mit diesem Update können Sie auch die Reihenfolge der DNS-Suffixe in Intune ändern.
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md#dns-settings) sind die aktuellen DNS-Einstellungen aufgeführt.
Gilt für: Windows 10-Geräte

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Unterstützung für Always On-VPN für Android-Enterprisearbeitsprofile <!-- 1333705 -->
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

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Windows 10 und höher: Verbesserungen des Kioskprofils im Azure-Portal <!-- 2748224 -->
Dieses Update umfasst die folgenden Verbesserungen am Windows 10-Kiosk-Gerätekonfigurationsprofil (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** für Plattform > **Kioskvorschau** für Profiltyp): 
- Derzeit können Sie mehrere Kioskprofile auf demselben Gerät erstellen. Ab diesem Update unterstützt Intune nur ein Kioskprofil pro Gerät. Wenn Sie noch mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen benutzerdefinierten URI verwenden.
- In einem **Multi-App-Kioskprofil** können Sie die Anwendungskachelgröße und Reihenfolge für das **Startmenülayout** im Raster der Anwendung auswählen. Wenn Sie eine umfassendere Anpassung bevorzugen, können Sie weiterhin eine XML-Datei hochladen.
- Die Kioskbrowsereinstellungen werden in die **Kiosk**-Einstellungen verschoben. Derzeit haben die **Kioskwebbrowser**-Einstellungen ihre eigene Kategorie im Azure-Portal.
Gilt für: Windows 10 und höher




### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Anwenden des Autopilot-Profils auf Win 10-Geräte, die noch nicht für Autopilot registriert sind <!-- 1558983 -->
Sie können Autopilot-Profile auf registrierte Win 10-Geräte anwenden, die noch nicht für Autopilot registriert sind. Wählen Sie im Autopilot-Profil die Option **Alle Zielgeräte in Autopilot-Geräte konvertieren** aus, um Nicht-Autopilot-Geräte automatisch mit dem Autopilot-Bereitstellungsdienst zu registrieren. Die Verarbeitung der Registrierung kann 48 Stunden dauern. Wenn die Registrierung des Geräts aufgehoben und es zurückgesetzt ist, stellt Autopilot es bereit.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Erstellen und Zuweisen mehrerer Registrierungsstatus-Seitenprofile für Azure AD-Gruppen <!-- 2526564 -->
Sie haben jetzt folgende Möglichkeit: [Erstellen und Zuweisen](windows-enrollment-status.md) mehrerer Registrierungsstatus-Seitenprofile für Azure ADD-Gruppen.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migration vom Programm zur Geräteregistrierung zum Apple Business Manager in Intune <!--2748613-->
Der Apple Business Manager (ABM) ist mit Intune konform, und Sie können ein Upgrade für Ihr Konto vom Programm zur Geräteregistrierung (Device Enrollment Program, DEP) zum ABM durchführen. Der Prozess in Intune ist identisch. Um ein Upgrade für Ihr Apple-Konto vom DEP zum ABM durchzuführen, rufen Sie [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817) auf.

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Registerkarten zu Warnungen und zum Registrierungsstatus auf der Übersichtsseite der Geräteregistrierung <!--2748656-->
Warnungs- und Registrierungsfehler werden jetzt auf separaten Registerkarten auf der Übersichtsseite für die Geräteregistrierung angezeigt.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Einschränken von Apps und Blockieren des Zugriffs auf Unternehmensressourcen auf Android-Geräten <!-- 2451462  -->  
In **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** > **Systemsicherheit** gibt es eine neue Einstellung unter dem Abschnitt *Gerätesicherheit* namens **Eingeschränkte Apps**. Die Einstellung **Eingeschränkte Apps** verwendet eine Konformitätsrichtlinie, um den Zugriff auf Unternehmensressourcen zu blockieren, wenn bestimmte Apps auf dem Gerät erstellt werden. Das Gerät wird so lange als nicht kompatibel betrachtet, bis die eingeschränkten Apps von diesem Gerät entfernt werden.
Gilt für: 
- Android




## <a name="week-of-september-24-2018"></a>Die Woche vom 24. September 2018

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Admin Center für die Microsoft 365-Geräteverwaltung <!-- 3078424 -->
Microsoft 365 verspricht unkomplizierte Verwaltung. Im Laufe der Zeit wurden die Microsoft 365-Back-End-Dienste integriert, um End-to-End-Szenarios wie den bedingten Zugriff in Intune und Azure AD zu ermöglichen. Im neuen [Microsoft 365-Admin Center](http://devicemanagement.microsoft.com) können Sie Verwaltungsvorgänge vereinen, vereinfachen und integrieren. Über diesen Arbeitsbereich für die Geräteverwaltung können Sie schnell auf alle Informationen und Aufgaben zur Geräte- und App-Verwaltung zugreifen, die für Ihre Organisation relevant sind. Dieser Bereich soll der primäre Arbeitsbereich für Computingteams von geschäftliche Endbenutzer werden.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Unterstützung für mehr Drittanbieterzertifizierungsstellen <!-- 3093107 -->
Mit dem Simple Certificate Enrollment-Protokoll (SCEP) können Sie jetzt neue Zertifikate auf mobilen Geräten mit Windows, iOS, Android und macOS ausstellen und vorhandene Zertifikate verlängern.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune wird iOS 10 und höher unterstützen <!-- 2454656 -->  
Die Intune-Registrierung, das Unternehmensportal und der verwaltete Browser unterstützen jetzt nur noch iOS-Geräte mit iOS 10 und höher. Um nach Geräten oder Benutzern zu suchen, die in Ihrem Unternehmen betroffen sind, wechseln Sie zu Intune im Azure-Portal > **Geräte** > **Alle Geräte**. Filtern Sie nach Betriebssystem und klicken Sie dann auf **Spalten**, um Details zur Betriebssystemversion anzuzeigen. Fordern Sie diese Benutzer auf, ihre Geräte auf eine unterstützte Betriebssystemversion zu aktualisieren.  

Wenn Sie über eines der unten aufgelisteten Geräte verfügen oder eines der unten aufgelisteten Geräte registrieren möchten, sollten Sie beachten, dass diese nur iOS 9 und früher unterstützen.  Wenn Sie mit diesen Geräten weiter auf das Intune-Unternehmensportal zugreifen möchten, müssen Sie für diese Geräte ein Upgrade auf Geräte mit Unterstützung für iOS 10 oder höher durchführen:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (3. Generation) 
* iPad Mini (1. Generation)  

## <a name="week-of-september-17-2018"></a>Die Woche vom 17. September 2018

### <a name="app-management"></a>App-Verwaltung

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Doppelte Kacheln zum Status des App-Schutzes wurden entfernt <!-- 3083391 -->
Die Kacheln **Benutzerstatus für iOS** und **Benutzerstatus für Android** waren sowohl auf der Seite **Client-Apps (Übersicht)** als auch auf der Seite **Client-Apps > Status des App-Schutzes** vorhanden. Die Statuskacheln wurden von der Seite **Client-Apps (Übersicht)** entfernt, um das doppelte Vorhandensein zu vermeiden. 

## <a name="week-of-august-27-2018"></a>Woche vom 27. August 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Pakettunnelunterstützung für Pro-App-VPN-Profile für iOS für die benutzerdefinierten und Pulse Secure-Verbindungstypen <!-- 1520957 -->
Wenn Sie Pro-App-VPN-Profile für iOS verwenden, können Sie das Tunneln entweder auf App-Ebene (app-proxy) oder auf Paketebene (packet-tunnel) nutzen. Diese Optionen stehen mit den folgenden Verbindungstypen zur Verfügung:
- Benutzerdefiniertes VPN
- Pulse Secure: Wenn Sie sich nicht sicher sind, welcher Wert benutzt werden soll, sehen Sie sich die Dokumentation Ihres VPN-Anbieters an.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Verzögerung, wenn iOS-Softwareupdates auf dem Gerät angezeigt werden <!-- 1949583 -->
Sie können in Intune unter **Softwareupdates** > **Update policies for iOS** (Updaterichtlinien für iOS) die Tage und Uhrzeiten konfigurieren, an denen die Geräte keine Updates installieren sollen. In einem zukünftigen Update können Sie einen Zeitraum von 1 bis 90 Tagen einstellen, in dem ein Softwareupdate auf dem Gerät angezeigt wird. 
Unter [Configure iOS update policies in Microsoft Intune (Konfigurieren von iOS-Updaterichtlinien in Microsoft Intune)](software-updates-ios.md) sind die aktuellen Einstellungen aufgeführt.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus-Version <!-- 2213968 -->
Wenn Sie Ihren Windows 10-Geräten Office 365 ProPlus-Apps über Intune hinzufügen, können Sie die Office-Version auswählen. Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Apps** > **App hinzufügen**. Wählen Sie dann in der **Typ**-Dropdownliste die Option **Office 365 ProPlus-Suite (Windows 10)** aus. Klicken Sie auf **Einstellungen der App-Suite**, um das entsprechende Blatt anzuzeigen. Legen Sie den **Updatekanal** auf einen Wert fest, z.B. **Monatlich**. Entfernen Sie optional andere Office-Versionen (msi) von den Endbenutzergeräten, indem Sie auf **Yes** (Ja) klicken. Wählen Sie **Specific** (Spezifisch) aus, um eine bestimmte Office-Version für den ausgewählten Kanal oder die Endbenutzergeräte zu installieren. Zu diesem Zeitpunkt können Sie die **spezifische Version** von Office auswählen, die verwendet werden soll. Die verfügbaren Versionen werden im Laufe der Zeit geändert. Wenn Sie eine neue Bereitstellung erstellen, können deshalb die verfügbaren Versionen aktueller sein, und bestimmte ältere Versionen sind möglicherweise nicht mehr verfügbar. Für aktuelle Bereitstellungen sind weiterhin die älteren Versionen verfügbar, jedoch wird die Liste mit den Versionen nicht ständig pro Kanal aktualisiert. Weitere Informationen finden Sie unter [Übersicht über die Updatekanäle für Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Unterstützung für das Registrieren von DNS-Einstellungen für Windows 10-VPN <!-- 2282852 -->
Mit diesem Update können Sie VPN-Profile für Windows 10 konfigurieren, um die IP-Adressen dynamisch zu registrieren, die der VPN-Schnittstelle mit internem DNS zugewiesen sind, ohne benutzerdefinierte Profile verwenden zu müssen.
Informationen zu den aktuell verfügbaren VPN-Profileinstellungen finden Sie unter [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Im Dateinamen des Installationsprogramm für das macOS-Unternehmensportal ist nun die Versionsnummer des Installationsprogramms enthalten<!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Automatische App-Updates unter iOS<!-- 2729759 -->
Für iOS-Version 11.0 und höher können nun automatische App-Updates für Apps ausgeführt werden, die für Geräte und Benutzer lizenziert sind.




### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello ist für Benutzer und Geräte konzipiert <!-- 1106609 -->
Wenn Sie eine [Windows Hello for Business](windows-hello.md)-Richtlinie erstellen, gilt diese für alle Benutzer innerhalb der Organisation (mandantenweit). Mit diesem Update kann die Richtlinie mithilfe einer Gerätekonfigurationsrichtlinie (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Identity Protection** > **Windows Hello for Business**) auch auf bestimmte Benutzer oder Geräte angewendet werden.
In Intune im Azure-Portal sind die Windows Hello-Konfiguration und die zugehörigen Einstellungen jetzt jeweils unter **Geräteregistrierung** und **Gerätekonfiguration** verfügbar. Die **Geräteregistrierung** ist für die gesamte Organisation (mandantenweit) konzipiert und unterstützt Windows AutoPilot (OOBE). Die **Gerätekonfiguration** ist für Geräte und Benutzer konzipiert, die eine Richtlinie verwenden, die während des Check-In angewendet wird.
Diese Funktion gilt für:  
- Windows 10 und höher
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler ist eine verfügbare Verbindung für VPN-Profile unter iOS <!-- 1769858 -->
Wenn Sie ein VPN-Gerätekonfigurationsprofil für iOS erstellen (unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS**, wechseln Sie zu Plattform und dann zum Profiltyp **VPN**), sind mehrere Verbindungstypen vorhanden, einschließlich Cisco, Citrix usw. Dieses Update wird Zscaler als Verbindungstyp hinzugefügt. 
Unter [VPN settings for devices running iOS (VPN-Einstellungen für Geräte unter iOS)](vpn-settings-ios.md) sind die verfügbaren Verbindungstypen aufgeführt.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>FIPS-Modus für Unternehmens-WLAN-Profile für Windows 10 <!-- 1879077 -->
Sie können nun im Azure-Portal für Intune den FIPS-Modus (Federal Information Processing Standards) für Unternehmens-WLAN-Profile für Windows 10 aktivieren. Achten Sie darauf, dass der FIPS-Modus in Ihrer WLAN-Infrastruktur aktiviert ist, wenn Sie ihn in Ihren WLAN-Profilen aktiviert haben.
Im Artikel [WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune](wi-fi-settings-windows.md) erfahren Sie, wie Sie ein WLAN-Profil erstellen können.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Steuern des S Modus für Geräte unter Windows 10 und höher – Public Preview <!-- 1958649 -->
Mit diesem Funktionsupdate können Sie ein Gerätekonfigurationsprofil erstellen, das den S Modus auf einem Windows 10-Gerät deaktiviert oder den Benutzer davon abhält, den S Modus eines Geräts zu deaktivieren. Dieses Feature ist in Intune verfügbar. Navigieren Sie zu **Gerätekonfiguration** > **Profile** >  **Windows 10 und höher** > **Edition upgrade and mode switch** (Editionsupgrade und Moduswechsel).
Auf der Seite [Willkommen bei Windows 10 im S Modus](https://www.microsoft.com/windows/s-mode) finden Sie weitere Informationen zum S Modus.
Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Das automatisch dem Konfigurationsprofil zugewiesene Windows Defender ATP-Konfigurationspaket <!-- 2144658 -->
Wenn Sie [Advanced Threat Protection verwenden und Geräte in Intune onboarden](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile), mussten Sie zuvor ein Konfigurationspaket herunterladen und es Ihrem Konfigurationsprofil hinzufügen. Mit diesem Update ruft Intune das Paket automatisch aus dem Windows Defender Security Center ab und fügt es Ihrem Profil hinzu.
Gilt für Windows 10 und höher.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Benutzer müssen während der Geräteeinrichtung eine Verbindung herstellen <!--2311457-->
Sie können nun Geräteprofile so einrichten, dass das Gerät eine Verbindung zu einem Netzwerk herstellen muss, bevor es während der Einrichtung von Windows 10 mit dem Prozess nach der Seite „Netzwerk“ fortfährt. Solange sich diese Funktion in der Vorschau befindet, ist für die Verwendung dieser Einstellung der Windows-Insider-Build 1809 oder höher erforderlich.
Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Einschränken von Apps und Blockieren des Zugriffs auf Unternehmensressourcen auf iOS- und Android Enterprise-Geräten <!-- 2451462 -->
Unter **Gerätekompatibilität** > **Richtlinien** > **Richtlinie erstellen** > **iOS** > **Systemsicherheit** ist eine neue Einstellung verfügbar: **Restricted applications** (Eingeschränkte Anwendungen). Diese neue Einstellung verwendet eine Konformitätsrichtlinie, um den Zugriff auf Unternehmensressourcen zu blockieren, wenn bestimmte Apps auf dem Gerät erstellt werden. Das Gerät wird so lange als nicht kompatibel betrachtet, bis die eingeschränkten Apps von diesem Gerät entfernt werden.
Gilt für: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Updates für die Unterstützung für modernes VPN für iOS <!-- 2459928, 1819876, and 2650856 -->
Dieses Update unterstützt die folgenden iOS-VPN-Clients: 
- F5 Access (Version 3.0.1 und höher)
- Citrix SSO
- Palo Alto Networks GlobalProtect (Version 5.0 und höher). Ebenso in diesem Update:
- Vorhandener **F5 Access**-Verbindungstyp wird in **F5 Access Legacy** für iOS umbenannt.
- Vorhandener **Palo Alto Networks GlobalProtect**-Verbindungstyp wird in **Palo Alto Networks GlobalProtect (legacy)** für iOS umbenannt.
Vorhandene Profile mit diesen Verbindungstypen funktionieren weiterhin mit ihren jeweiligen Legacy-VPN-Clients. Wenn Sie Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN oder Palo Alto Networks GlobalProtect-Version 4.1 oder eine ältere Version davon mit iOS verwenden, sollten Sie zu den neuen Apps wechseln. Führen Sie diesen Wechsel so früh wie möglich aus, um sicherzustellen, dass der VPN-Zugriff für iOS-Geräte zugänglich ist, sobald diese ein Update auf iOS 12 durchführen.
Weitere Informationen zu iOS 12 und VPN-Profilen finden Sie im [Blog des Supportteams für Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportieren von klassischen Azure-Portal-Konformitätsrichtlinien zur Neuerstellung dieser Richtlinien im Azure-Portal für Intune<!-- 2469637 -->
Konformitätsrichtlinien, die im klassischen Azure-Portal erstellt wurden, werden als veraltet markiert. Sie können vorhandene Konformitätsrichtlinien überprüfen und löschen, aber nicht aktualisieren. Wenn Sie Konformitätsrichtlinien zum aktuellen Azure-Portal für Intune migrieren müssen, können Sie die Richtlinien als durch Trennzeichen getrennte Datei (*CSV*-Datei) exportieren. Verwenden Sie anschließend die Informationen in der Datei, um die Richtlinien im Azure-Portal für Intune neu zu erstellen.

> [!IMPORTANT]
> Sobald das klassische Azure-Portal eingestellt wird, haben Sie keinen Zugriff mehr auf Ihre Konformitätsrichtlinien und können diese nicht mehr einsehen. Exportieren Sie Ihre Richtlinien deshalb auf jeden Fall, und erstellen Sie sie im Azure-Portal neu, bevor das klassische Azure-Portal eingestellt wird.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile: neuer Mobile Threat Defense-Partner <!-- 22662717 -->
Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Better Mobile vorgenommen werden, einer Multi Threat Defense-Lösung, die in Microsoft Intune integriert werden kann.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Sperren des Unternehmensportals im Einzelanwendungsmodus, bis sich Benutzer anmelden <!--1067692 --> 
Sie haben nun die Möglichkeit, das Unternehmensportal im Einzelanwendungsmodus auszuführen, wenn Sie einen Benutzer über das Unternehmensportal statt über den Setup-Assistenten während der DEP-Registrierung authentifizieren. Durch diese Option wird das Gerät sofort nach dem Abschluss des Setup-Assistenten gesperrt, sodass sich ein Benutzer anmelden muss, um auf das Gerät zuzugreifen. Durch diese Methode wird sichergestellt, dass das Gerät den Onboardingprozess abschließt und nicht in einem verwaisten Zustand ohne verknüpften Benutzer verbleibt.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Zuweisen eines Benutzer- und Anzeigenamens zu einem Autopilot-Gerät <!--1346521 -->
Sie können jetzt [einen Benutzer zu einem einzelnen Autopilot-Gerät zuweisen](enrollment-autopilot.md). Administratoren können Anzeigenamen auch vergeben, um den Benutzer zu begrüßen, wenn dieser sein Gerät mit AutoPilot einrichtet.
Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Verwendung von VPP-Gerätelizenzen, zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung <!-- 1608345 -->
Sie können jetzt Gerätelizenzen des Volume Purchase Program (VPP) verwenden, um das Unternehmensportal während der Registrierungsvorgänge des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) vorab bereitzustellen. Geben Sie dazu bei der [Erstellung oder Bearbeitung eines Registrierungsprofils](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) das VPP-Token an, das Sie zum Installieren des Unternehmensportals verwenden möchten. Stellen Sie sicher, dass Ihr Token nicht abläuft, und dass Sie über genügend Lizenzen für die Unternehmensportal-App verfügen. In Fällen, in denen das Token abläuft oder über keine Lizenzen mehr verfügt, überträgt Intune stattdessen das App Store-Unternehmensportal mithilfe von Push (dafür ist die Eingabe eine Apple-ID erforderlich).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Erforderliche Bestätigung zur Löschung von VPP-Token, die für die Vorabbereitstellung des Unternehmensportals verwendet werden <!-- 2237634 -->
Für die Löschung eines VPP-Tokens (Volume Purchase Program) ist jetzt eine Bestätigung notwendig, falls das Token zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwendet wird.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Blockieren von Registrierungen persönlicher Windows-Geräte <!-- 1849498 -->
Sie können die Registrierung [persönlicher Windows-Geräte](enrollment-restrictions-set.md#set-device-type-restrictions) mit der [mobilen Geräteverwaltung](windows-enroll.md) in Intune blockieren. Geräte, die mit dem [Intune-PC-Agent](manage-windows-pcs-with-microsoft-intune.md) registriert sind, können nicht über dieses Feature blockiert werden. Dieses Feature wird in den nächsten Wochen eingeführt, sodass es nicht sofort in der Benutzeroberfläche zu finden ist.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Angeben von Computernamensmustern in einem Autopilot-Profil <!--1849855-->
Sie können eine [Vorlage für einen Computernamen angeben](enrollment-autopilot.md#create-an-autopilot-deployment-profile), um den [Computernamen](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) während der Autopilot-Registrierung zu generieren und festzulegen. Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Ausblenden der Kontoänderungsoptionen für Windows Autopilot-Profile auf der Anmeldeseite und der Domänenfehlerseite des Unternehmens <!--1901669 -->
Es gibt [neue Windows Autopilot-Profiloptionen](enrollment-autopilot.md#create-an-autopilot-deployment-profile), mit denen Administratoren Kontoänderungsoptionen auf der Anmeldeseite und der Domänenfehlerseite des Unternehmens ausblenden können. Für das Ausblenden dieser Optionen muss das Unternehmensbranding in Azure Active Directory konfiguriert sein. Gilt für: den aktuellen [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-Build (während der Vorschauversion).



### <a name="device-management"></a>Geräteverwaltung

#### <a name="delete-jamf-devices----2653306--"></a>Löschen von JAMF-Geräten <!-- 2653306-->
Sie können Geräte löschen, die mit JAMF verwaltet werden, indem Sie zu **Geräte** navigieren, das JAMF-Gerät auswählen und auf **Löschen** klicken.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Änderung der Terminologie in „Außer Betrieb nehmen“ und „Zurücksetzen“ <!-- 2175759 -->
Um Konsistenz mit der Graph-API herzustellen, wurden auf der Benutzeroberfläche und in der Dokumentation von Intune folgende Begriffe geändert:
- **Unternehmensdaten entfernen** heißt nun „Außer Betrieb nehmen“.
- **Auf Werkseinstellungen zurücksetzen** wird zu **Zurücksetzen**.

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Bestätigungsdialog vor dem Löschen des MDM-Push-Zertifikats durch den Administrator <!-- 297909500-->
Beim Versuch, ein Apple-MDM-Push-Zertifikat zu löschen, wird in einem Bestätigungsdialogfeld die Anzahl der zugehörigen iOS- und macOS-Geräte angezeigt. Wenn das Zertifikat gelöscht ist, müssen diese Geräte erneut registriert werden.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Zusätzliche Sicherheitseinstellungen für Windows Installer <!-- 2282430 -->
Sie können Benutzern erlauben, App-Installationen zu steuern. Wenn diese Option aktiviert ist, werden Installationen, die normalerweise wegen Sicherheitsverstößen unterbrochen werden würden, weiterhin ausgeführt. Sie können festlegen, dass Windows Installer bei der Installation eines beliebigen Programms auf einem System erhöhte Berechtigungen verwendet. Zusätzlich können Sie festlegen, dass Windows Information Protection-Elemente (WIP) indiziert und die zugehörigen Metadaten an einem nicht verschlüsselten Speicherort gespeichert werden. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente nicht indiziert und sie werden nicht in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Diese Funktionalität für diese Optionen ist standardmäßig deaktiviert. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968 -->
Die Unternehmensportalwebsite wurde auf der Grundlage von Kundenfeedback um neue Features ergänzt. Sie werden eine erhebliche Verbesserung der vorhandenen Funktionen und Benutzerfreundlichkeit Ihrer Geräte feststellen können. Bestimmte Bereiche der Website – &ndash;z.B. Gerätedetails, Feedback und Support sowie die Geräteübersicht&ndash; – wurden mit einem neuen, modernen und dynamischen Design ausgestattet. Weiterhin sind enthalten:

- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- Benutzerfreundlichere Sprache, weniger technischer Jargon
- Möglichkeit zur Freigabe direkter Links für Apps
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer  

Die [Dokumentation zur Intune-Unternehmensportalwebsite](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) wurde entsprechend dieser Änderungen aktualisiert. Ein Beispiel für die App-Verbesserungen finden Sie unter [Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Verbesserte Erkennung von Jailbreaks in Konformitätsberichten <!-- 2198738 -->
Die Einstellungen für eine verbesserte Erkennung von Jailbreaks werden nun in allen Konformitätsberichten in der Administratorkonsole angezeigt.

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-policies---1081974---"></a>Bereichsmarkierungen für Richtlinien <!--1081974 -->
Sie können [Bereichsmarkierungen erstellen](scope-tags.md), um den Zugriff auf Intune-Ressourcen einzuschränken. Fügen Sie einer Rollenzuweisung eine Bereichsmarkierung hinzu, und fügen Sie diese anschließend einem Konfigurationsprofil hinzu. Die Rolle hat nur Zugriff auf Ressourcen mit Konfigurationsprofilen, die über übereinstimmende Bereichsmarkierungen (oder keine Bereichsmarkierung) verfügen.

## <a name="week-of-august-14-2018"></a>Woche vom 14. August 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-Unterstützung für das Programm zur Geräteregistrierung von Apple<!-- 747651 -->
Intune unterstützt jetzt die Registrierung von macOS-Geräten über das Apple-Programm zur Geräteregistrierung. Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Woche vom 23. Juli 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Unterstützung von branchenspezifischen Apps für macOS <!-- 1895847 -->
Mit Microsoft Intune können Sie branchenspezifische macOS-Apps als **Required** (Erforderlich) oder **Available with enrollment** (Mit Registrierung verfügbar) bereitstellen. Sie können Endbenutzern Apps als **Available** (Verfügbar) über das Unternehmensportal für macOS oder über die [Website des Unternehmensportals](https://portal.manage.microsoft.com) bereitstellen.

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Unterstützung von integrierten, im Kioskmodus ausführbaren iOS-Apps <!-- 2051098 -->
Zusätzlich zu Store-Apps und verwalteten Apps können Sie nun auf einem iOS-Gerät eine integrierte App (beispielsweise Safari) auswählen, die sich im Kioskmodus ausführen lässt.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Bearbeiten von Office 365 Pro Plus-App-Bereitstellungen <!-- 2150145 -->
Als Microsoft Intune-Administrator haben Sie mehr Möglichkeiten, Ihre Office 365 Pro Plus-App-Bereitstellungen zu bearbeiten. Darüber hinaus müssen Sie Ihre Bereitstellungen nicht mehr löschen, um Eigenschaften der Suite zu ändern. Wählen Sie im Azure-Portal die Option **Microsoft Intune** > **Client-Apps** > **Apps** aus. Wählen Sie aus der Liste der Apps Ihre Office 365 Pro Plus-Suite aus.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Aktuelles Intune App SDK für Android jetzt verfügbar <!-- 2744271-->

Zur Unterstützung der Android P-Version ist eine aktualisierte Version des Intune App SDK für Android verfügbar. Wenn Sie App-Entwickler sind und das Intune SDK für Android verwenden, müssen Sie die aktualisierte Version des Intune App SDK installieren, um sicherzustellen, dass die Intune-Funktionen in Ihren Android-Apps auch auf Android P-Geräten wie erwartet ausgeführt werden. Diese Version des Intune App SDK stellt ein integriertes Plug-In bereit, das die SDK-Updates ausführt. Sie müssen keinerlei integrierten Code neu schreiben. Weitere Details finden Sie unter [Intune SDK für Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Wenn Sie das alte Kennzeichenformat für Intune verwenden, empfehlen wir die Verwendung des Aktenkoffersymbols. Informationen zum Branding finden Sie in [diesem GitHub-Repository](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Erstellen von Konformitätsrichtlinien für macOS-Geräte über Firewalleinstellungen <!-- 1497640 -->
Beim Erstellen einer neuen macOS-Konformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: macOS** > **Systemsicherheit**) sind einige neue **Firewall**-Einstellungen verfügbar: 

- **Firewall:** Hier konfigurieren Sie, wie eingehende Verbindungen in Ihrer Umgebung behandelt werden.
- **Eingehende Verbindungen:** Mit dieser Einstellung können Sie eingehende Verbindungen für grundlegende Internetdienste wie DHCP, Bonjour und IPSec zulassen und alle anderen eingehenden Verbindungen **blockieren**. Alle Freigabedienste werden durch diese Einstellung blockiert.
- **Geschützter Modus:** Durch die **Aktivierung** dieser Einstellung hindern Sie das Gerät daran, auf Suchanforderungen zu antworten. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps.

Gilt für: macOS 10.12 und höher

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Neues WLAN-Gerätekonfigurationsprofil für Windows 10 und höher <!-- 1879077 -->
Aktuell können Sie WLAN-Profile mithilfe von XML-Dateien importieren und exportieren. Durch dieses Update können Sie ein WLAN-Gerätekonfigurationsprofil genau wie für andere Plattformen auch direkt in Intune erstellen.

Um ein Profil zu erstellen, öffnen Sie **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **WLAN**. 

Gilt für Windows 10 und höher.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>„Kiosk – Veraltet“ ist ausgegraut und kann nicht verändert werden <!-- 2149998 -->
Das [Kiosk-Feature](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Geräteeinschränkungen**) ist veraltet und wurde durch [Kiosk-Einstellungen für Windows 10 und höher](kiosk-settings.md) ersetzt. Durch dieses Update wird das Feature **Kiosk - Obsolete** (Kiosk – veraltet) ausgegraut, und die Benutzeroberfläche kann nicht verändert oder aktualisiert werden. 

Informationen zum Aktivieren des Kioskmodus finden Sie unter [Kioskeinstellungen für Windows 10 und höher in Intune](kiosk-settings.md).

Gilt für Windows 10 und höher, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>APIs für die Verwendung von Zertifizierungsstellen von Drittanbietern <!-- 2184013 -->
Mit diesem Update wird eine Java-API eingeführt, mit der sich Drittanbieter-Zertifizierungsstellen in Intune und SCEP integrieren lassen. Benutzer können so das SCEP-Zertifikat einem Profil hinzufügen und es über MDM auf Geräte anwenden.

Derzeit unterstützt Intune [SCEP-Anforderungen über Active Directory-Zertifikatdienste](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Umschaltfläche zum Anzeigen oder Ausblenden der Schaltfläche „Sitzung beenden“ auf einem Kioskbrowser <!-- 2455253 -->
Sie können nun konfigurieren, ob Kioskbrowser die Schaltfläche „Sitzung beenden“ anzeigen. Sie finden das Steuerelement unter **Gerätekonfiguration** > **Kiosk (Vorschauversion)** > **Kioskwebbrowser**. Wenn die Schaltfläche aktiviert ist und ein Benutzer darauf klickt, fordert die App eine Bestätigung zum Beenden der Sitzung an. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten und navigiert zurück zur Standard-URL.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Erstellen eines eSIM-Mobilfunkkonfigurationsprofils <!-- 2564077 -->
Unter **Gerätekonfiguration** können Sie ein eSIM-Mobilfunkprofil erstellen. Sie können eine Datei importieren, die Mobilfunk-Aktivierungscodes enthält, die von Ihrem Mobilfunkanbieter bereitgestellt werden. Diese Profile können daraufhin für Ihre mit eSIM-LTE aktivierten Windows 10-Geräte bereitgestellt werden, z.B. für das Surface Pro LTE und andere eSIM-fähigen Geräte.

Überprüfen Sie, ob Ihre [Geräte eSIM-Profile unterstützen](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gilt für Windows 10 und höher. 




### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Automatisches Markieren von Android-Geräten als „Geschäftlich“ über Samsung Knox Mobile Enrollment <!-- 2404851 -->
In der Standardeinstellung werden Android-Geräte, die über Samsung Knox Mobile Enrollment registriert sind, nun unter **Gerätebesitz** als **Geschäftlich** markiert. Sie müssen also Unternehmensgeräte vor der Registrierung bei Knox Mobile Enrollment nicht manuell über IMEI oder Seriennummern identifizieren.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massenlöschung von Geräten auf dem Blatt „Geräte“ <!-- 1793693 -->

Sie können nun mehrere Geräte gleichzeitig über das Blatt „Geräte“ löschen. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie die Geräte aus, die Sie löschen möchten, und klicken Sie auf **Löschen**. Es wird eine Warnung für die Geräte ausgegeben, die nicht gelöscht werden können.

## <a name="week-of-july-16-2018"></a>Woche vom 16. Juli 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Weitere Synchronisierungsoptionen in der Unternehmensportal-App für Windows  
Mit der Unternehmensportal-App für Windows können Sie nun direkt über die Windows-Taskleiste und das Startmenü eine Synchronisierung starten. Dieses Feature ist besonders hilfreich, wenn Sie nur Geräte synchronisieren und auf Unternehmensressourcen zugreifen müssen. Klicken Sie mit der rechten Maustaste auf das Unternehmensportalsymbol, das an die Taskleiste oder das Startmenü angeheftet ist, um das neue Feature zu verwenden. Klicken Sie in den Menüoptionen (auch als Sprungliste bezeichnet) auf **Dieses Gerät synchronisieren**. Die Unternehmensportal-App wird geöffnet und zeigt die Seite **Einstellungen** an. Außerdem wird die Synchronisierung gestartet. Einen Überblick über dieses neue Feature erhalten Sie unter [Updates der Benutzeroberfläche](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Geänderte Durchsuchen-Funktion in der Unternehmensportal-App für Windows  

Beim Durchsuchen von oder Suchen nach Apps in der Unternehmensportal-App für Windows können Sie zwischen der Ansicht **Kacheln** und der neu hinzugefügten Ansicht **Details** wechseln. In der neuen Ansicht werden Anwendungsdetails wie Namen, Herausgeber, Veröffentlichungsdatum und Installationsstatus angezeigt.  

Auf der Seite **Apps** können Sie sich in der Ansicht **Installiert** Details zu abgeschlossenen und laufenden App-Installationen anzeigen lassen. Unter [Updates der Benutzeroberfläche](whats-new-app-ui.md) können Sie sich einen Eindruck von der neuen Ansicht verschaffen.  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Verbesserte Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager  
Wenn ein Geräteregistrierungs-Manager (DEM) sich bei der Unternehmensportal-App für Windows anmeldet, listet die App nun nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserung wird die Anzahl der Timeouts verringert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte anzuzeigen.  


## <a name="week-of-july-9-2018"></a>Woche vom 9. Juli 2018

### <a name="app-management"></a>App-Verwaltung

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockieren des App-Zugriffs basierend auf nicht genehmigten Geräteherstellern und Modellen <!-- 1425689 ! -->
Der Intune-IT-Administrator kann über Intune-App-Schutzrichtlinien die Umsetzung einer festgelegten Liste von Android-Herstellern und/oder iOS-Modellen erzwingen. Der IT-Administrator kann eine durch Semikolon getrennte Liste von Herstellern für Android-Richtlinien und Gerätemodelle für iOS-Richtlinien bereitstellen. Intune-App-Schutzrichtlinien gelten nur für Android und iOS. Für diese festgelegte Liste können zwei verschiedene Aktionen ausgeführt werden:
- Blockieren des App-Zugriffs auf Geräten, die nicht angegeben sind.
- Selektives Zurücksetzen von Unternehmensdaten auf Geräten, die nicht angegeben sind. 

Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Anforderungen der Richtlinie nicht erfüllt sind. Anhand von Einstellungen werden Benutzer entweder blockiert oder Unternehmensdaten innerhalb der App selektiv zurückgesetzt. Für dieses Feature ist auf iOS-Geräten die Beteiligung von Anwendungen erforderlich (wie z.B. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK für dieses Feature für die Zielanwendungen zu erzwingen. Diese Integration erfolgt fortlaufend und ist von den jeweiligen Anwendungsteams abhängig. Unter Android ist für dieses Feature das neueste Unternehmensportal erforderlich. 

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen aus, die auf dem Blatt „Intune“ für Anwendungsschutzrichtlinien angegeben sind. Dies hängt ausschließlich von dem Wert ab, den das Gerät meldet. Daher sollte der IT-Administrator sicherstellen, dass das beabsichtigte Verhalten korrekt ist. Dazu kann diese Einstellung basierend auf einer Vielzahl von Geräteherstellern und Modellen für eine kleine Benutzergruppe getestet werden. Wählen Sie in Microsoft Intune **Client-Apps** > **App-Schutzrichtlinien** aus, um App-Schutzrichtlinien anzuzeigen und hinzuzufügen. Weiter Informationen zu App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md) und [Selektives Löschen von Daten mithilfe von Zugriffsaktionen für App-Schutzrichtlinien in Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Zugriff auf das Vorabreleasebuild der macOS-Unternehmensportal-App <!-- 1734766 -->
Sie können sich mithilfe von Microsoft AutoUpdate registrieren, um nach einem Beitritt zum Insider-Programm frühzeitig Builds zu erhalten. Durch eine Registrierung können Sie das aktualisierte Unternehmensportal verwenden, bevor sie Ihren Endbenutzern zur Verfügung steht. Weitere Informationen finden Sie im [Microsoft Intune-Blog](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Woche vom 2. Juli 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Überwachen des Konfigurationsstatus von iOS-Apps auf allen Geräten <!-- 880037 -->
Als Microsoft Intune-Administrator können Sie auf jedem verwalteten Gerät den Konfigurationsstatus von iOS-Apps überwachen. Klicken Sie im Azure-Portal unter **Microsoft Intune** auf **Geräte** > **Alle Geräte**. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, für das ein Blatt angezeigt werden soll. Klicken Sie auf dem Geräteblatt auf **App-Konfiguration**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Zugriff auf Aktionen für App-Schutzrichtlinien <!-- 1483510 -->
Sie können App-Schutzrichtlinien so konfigurieren, dass nicht kompatible Geräte explizit zurückgesetzt, blockiert oder gewarnt werden. Mit der Aktion *Zurücksetzen* werden Ihre Unternehmensdaten von einem Gerät entfernt. Im Falle eines Zurücksetzens wird der Gerätebenutzer über den Grund für das Zurücksetzen und Schritte zur Wiederherstellung benachrichtigt. Für einige Einstellungen, wie z. B. die Mindestversion des Betriebssystems, können Sie mehrere Aktionen anwenden, z. B. das Blockieren und Zurücksetzen. Beachten Sie, dass diese Aktionen ausgelöst werden, wenn die App gestartet wird.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Zurücksetzen ausgewählter App-Daten einer Organisation <!-- 1507030 -->
Wenn die in den APP-Zugriffseinstellungen festgelegten Bedingungen nicht erfüllt sind, können Administratoren durch eine neue Aktion ausgewählte Organisationsdaten zurücksetzen.  Dieses Feature hilft Administratoren dabei, vertrauliche Organisationsdaten mithilfe festgelegter Kriterien automatisch zu schützen und aus Anwendungen zu entfernen.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Widerrufen einer Lizenz für iOS-Apps, die über VPP erworben wurden <!-- 1777384 -->
Als Microsoft Intune-Administrator haben Sie die Möglichkeit, alle Lizenzen für eine bestimmte iOS-App zu widerrufen, die über das Volume Purchase Program (VPP) erworben wurde. Sie können Benutzer benachrichtigen, wenn ihnen eine App-Benutzerlizenz entzogen wurde. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Die Anzahl der widerrufenen Lizenzen wird innerhalb der Intune-**App**-Workload im Knoten **Lizenzierte Apps** angezeigt. Weitere Informationen zu iOS-VPP-Apps finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Updates für nicht konforme Meldungen in der Unternehmensportal-App <!-- 1832222 -->
Die Meldung, die Benutzern angezeigt wird, wenn ein Gerät nicht konform ist, wurde überarbeitet. Die Meldungen behalten ihre ursprünglichen Bedeutungen bei, wurden jedoch mit benutzerfreundlicherer Sprache und weniger Fachbegriffen aktualisiert. Auch Links zur Dokumentation und zu Wartungsschritten wurden auf den neuesten Stand gebracht.
Die folgenden Texte (vorher und nachher) sind ein Beispiel für die Verbesserungen an den angezeigten Meldungen:
- **Vorher:** *Dieses Gerät hat nicht innerhalb des von Ihrem IT-Administrator festgelegten Zeitraums eine Verbindung mit dem Intune-Dienst hergestellt. Um dieses Problem zu beheben, öffnen Sie die Unternehmensportal-App auf Ihrem Gerät, und klicken Sie auf die Schaltfläche „Konformität überprüfen“.*
- **Nachher:** *Your device has not checked in with your organization in a while. To reestablish a connection, open the Company Portal app on your device and tap Check Settings for your device. (Ihr Gerät wurde länger nicht mehr bei Ihrer Organisation eingecheckt. Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät, und tippen Sie für Ihr Gerät auf „Einstellungen überprüfen“, um die Verbindung wiederherzustellen.)*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Widerrufen einer iOS-VPP-App-Lizenz <!-- 1863797 -->
Als Administrator haben Sie die Möglichkeit, eine iOS-VPP-App-Lizenz zu widerrufen, die einem Benutzer oder Gerät zugewiesen ist. Dasselbe erreichen Sie mit der Deinstallation einer iOS-VPP-App. Bevor Sie die App deinstallieren, müssen der Benutzer oder das Gerät aus der Gruppe entfernt werden, die von der App als Ziel verwendet wird. Wenn Sie den Benutzer oder das Gerät aus der Gruppe entfernen, verhindern Sie, dass die App erneut installiert wird. Sobald diese Schritte durchgeführt wurden, können Sie die App-Lizenz einem anderen Benutzer oder Gerät zuweisen. Weitere Informationen zu iOS-VPP-App-Lizenzen, finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Auswählen von Gerätekategorien durch den Zugriff auf die Einstellungen für Geschäfts-, Schul- oder Unikonten <!-- 1058963 eenotready --> 
Wenn Sie die [Gerätegruppenzuordnung](https://docs.microsoft.com/intune/device-group-mapping) aktiviert haben, werden Benutzer unter Windows 10 aufgefordert, eine Gerätekategorie auszuwählen, nachdem sie sich unter **Einstellungen** > **Konten** > **Auf Geschäfts-, Schul- oder Unikonto zugreifen** mit der Schaltfläche **Verbinden** angemeldet haben. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Verwenden von „sAMAccountName“ als Kontobenutzername für E-Mail-Profile <!-- 1500307 -->
Sie können das lokal vorhandene Attribut **sAMAccountName** als Kontobenutzername für Android-, iOS- und Windows 10-E-Mail-Profile verwenden. Mit den Attributen `domain` oder `ntdomain` können Sie in Azure Active Directory (Azure AD) außerdem die Domain abrufen. Alternativ können Sie auch eine benutzerdefinierte statische Domäne eingeben.

Zur Nutzung dieses Features müssen Sie das `sAMAccountName`-Attribut Ihrer lokalen Active Directory-Umgebung mit Azure AD synchronisieren.

Gilt für: [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 und höher](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Anzeigen von in Konflikt stehenden Gerätekonfigurationsprofilen <!-- 1556983 -->
Unter **Gerätekonfiguration** wird eine Liste der vorhandenen Profile angezeigt. Mit diesem Update wird eine neue Spalte hinzugefügt, die Details zu Profilen enthält, die in Konflikt stehen. Sie können eine in Konflikt stehende Zeile anklicken, um die Einstellung und das Profil anzuzeigen, bei denen der Konflikt vorhanden ist. 

Weitere Informationen zum [Verwalten von Konfigurationsprofilen](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Neue Status für Geräte in der Gerätekonfiguration <!-- 2308882 -->
Wählen Sie unter **Gerätekonformität** > **Richtlinien** eine Richtlinie aus. Dort wurden unter **Übersicht** folgende neue Status hinzugefügt:
- Erfolgreich
- Fehler
- Konflikt
- Ausstehend
- Nicht anwendbar. Außerdem wird eine Grafik angezeigt, in der die Anzahl der Geräte für andere Plattformen zu sehen ist. Beim Aufruf eines iOS-Profils wird beispielsweise auf der neuen Kachel die Anzahl der Nicht-iOS-Geräte angezeigt, die diesem Profil ebenfalls zugewiesen sind. Weitere Informationen finden Sie im Artikel zu [Gerätekonformitätsrichtlinien](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Unterstützung von Drittanbieter-Antivirenlösungen in Gerätekonformitätsrichtlinien <!-- 2325484 -->
Beim Erstellen einer Gerätekonformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: Windows 10 und höher** > **Einstellungen** > **Systemsicherheit**) sind neue Optionen für **[Gerätesicherheit](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** verfügbar: 
- **Antivirus:** Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim Windows-Sicherheitscenter registriert sind. 
- **Antispyware:** Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antispyware-Lösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim Windows Security Center registriert sind. 

Gilt für: Windows 10 und höher 

### <a name="device-enrollment"></a>Geräteregistrierung

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Geräte ohne die Spalte „Profiles“ (Profile) in der Liste der Registrierungsprogrammtoken <!-- 1853904 -->
In der Liste der Registrierungprogrammtoken gibt es eine neue Spalte, in der die Anzahl der Geräte ohne zugewiesenes Profil angezeigt werden. So können Administratoren diesen Geräten leichter Profile zuweisen, bevor sie sie Benutzern zuweisen. Navigieren Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken**, um die neue Spalte anzuzeigen.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Google-Namensänderungen für Android for Work und Play for Work <!--842873 -->
In Intune wurde die Android for Work-Terminologie aktualisiert, um die Änderungen von Google-Markennamen widerzuspiegeln. Die Benennungen „Android for Work“ und „Play for Work“ werden nicht mehr verwendet. Die Terminologie wurde je nach Kontext angepasst:
- „Android Enterprise“ bezieht sich auf den allgemeinen modernen Android-Verwaltungsstapel.
- „Arbeitsprofil“ oder „Profilbesitzer“ bezieht sich auf BYOD-Geräte, die mit Arbeitsprofilen verwaltet werden.
- „Managed Google Play“ bezieht sich auf den App Store von Google.

#### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Gerätebereinigung) aus.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>COSU-Unterstützung (corporate-owned, single use, Unternehmensgeräte für spezifische Anwendungsfälle) für Android-Geräte <!-- 1630973 -->

Intune unterstützt jetzt kioskartige, stringent verwaltete Android-Geräte, deren Einsatzbereich stark eingeschränkt ist. Dadurch können Administratoren festlegen, dass auf einem Gerät nur eine oder einige wenige Apps und Aktionen von Benutzern verwendet werden dürfen. Navigieren Sie in Intune zu **Geräteregistrierung** > **Android-Registrierung** > **Kiosk und Taskgeräteregistrierungen**, um einen Android-Kiosk einzurichten. Weitere Informationen finden Sie unter [Set up enrollment of Android enterprise kiosk devices (Einrichten der Registrierung von Android-Kioskgeräte des Unternehmens)](android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Duplikatprüfung auf Zeilenbasis beim Hochladen unternehmensspezifischer Gerätebezeichner <!-- 2203794-->
Beim Hochladen von Unternehmens-IDs stellt Intune jetzt eine Liste mit mehrfach vorhandenen IDs bereit und bietet Ihnen die Möglichkeit, die vorhandenen Informationen zu ersetzen oder beizubehalten. Der Bericht wird angezeigt, wenn nach dem Klicken auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Bezeichner hinzufügen** Duplikate vorhanden sind. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Manuelles Hinzufügen von Unternehmensgerätebezeichnern <!-- 2203803 -->
Sie können Unternehmensgeräte-IDs jetzt manuell hinzufügen. Klicken Sie auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen**. 

## <a name="week-of-june-25-2018"></a>Woche vom 25. Juni 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo: neuer Mobile Threat Defense-Partner <!-- 1169249 -->

Sie können den Zugriff mobiler Geräte auf Unternehmensressourcen mit bedingtem Zugriff basierend auf Risikobewertungen steuern, die von Pradeo vorgenommen werden, einer Mobile Threat Defense-Lösung, die mit Microsoft Intune zusammenarbeitet.

## <a name="week-of-june-18-2018"></a>Woche vom 18. Juni 2018

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Unterstützung des Microsoft Edge-Browsers für mobile Geräte für die App-Schutzrichtlinien von Intune <!-- 1817882 -->

Microsoft Edge für mobile Geräte unterstützt nun die App-Schutzrichtlinien, die in Intune definiert sind.

## <a name="week-of-june-11-2018"></a>Woche vom 11. Juni 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Verwenden des FIPS-Modus mit dem NDES-Certificate Connector <!-- 1333688 -->
Wenn Sie den NDES-Certificate Connector auf einem Computer mit aktiviertem FIPS-Modus (Federal Information Processing Standard) installieren, funktionierte das Ausstellen und Widerrufen von Zertifikaten nicht wie erwartet. Mit diesem Update ist die Unterstützung für FIPS im NDES-Certificate Connector enthalten. 

Dieses Update enthält ebenfalls Folgendes:

- Der NDES-Certificate Connector erfordert .NET Framework 4.5. Dieses Framework ist automatisch in Windows Server 2016 und Windows Server 2012 R2 enthalten. Zuvor war .NET Framework 3.5 die mindestens erforderliche Version.
- Die Unterstützung für TLS 1.2 ist im NDES-Certificate Connector enthalten. Wenn der Server, auf dem NDES-Certificate Connector installiert ist, TLS 1.2 unterstützt, wird TLS 1.2 verwendet. Wenn der Server TLS 1.2 nicht unterstützt, wird TLS 1.1 verwendet. Derzeit wird TLS 1.1 für die Authentifizierung zwischen den Geräten und dem Server verwendet.

Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von SCEP-Zertifikaten](certificates-scep-configure.md) und [Konfigurieren und Verwenden von PKCS-Zertifikaten](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Woche vom 4. Juni 2018

### <a name="app-management"></a>App-Verwaltung

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Abrufen der zugeordneten App-Benutzermodell-ID (AUMID) für Apps im Microsoft Store für Unternehmen im Kioskmodus <!-- 1560077 ! -->
Intune kann jetzt die Modell-IDs der Anwendungsbenutzer (AUMIDs) für Apps im Microsoft Store für Unternehmen abrufen, um eine verbesserte Konfiguration des Kioskprofils bereitzustellen.

Weitere Informationen zu Apps im Microsoft Store für Unternehmen finden Sie unter [Verwalten von Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Neue Seite für das Branding des Unternehmensportals <!-- 1916370 -->
Die Seite für das Branding des Unternehmensportals hat ein neues Layout, neue Meldungen und neue QuickInfos.


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Unterstützung für VPN-Profile für Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
Mit diesem Update können Sie Palo Alto Networks GlobalProtect als VPN-Verbindungstyp für VPN-Profile in Intune auswählen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Profiltyp** > **VPN**). Für dieses Release werden die folgenden Plattformen unterstützt: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1403702 -->
Sie können jetzt für Windows 10-Geräte zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte konfigurieren. Zusätzliche Einstellungen sind bei Microsoft-Netzwerkclients, Microsoft-Netzwerkservern, bei der Netzwerkzugriff und -sicherheit und bei der interaktiven Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Aktivieren des Kioskmodus auf Windows 10-Geräten <!-- 1560072 ! -->
Auf Windows 10-Geräten können Sie ein Konfigurationsprofil erstellen und den Kioskmodus aktivieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** > **Geräteeinschränkungen** > **Kiosk**). Bei diesem Update wurde die Einstellung **Kiosk (Vorschau)** in **Kiosk (veraltet)** umbenannt. **Kiosk (veraltet)** wird nicht mehr empfohlen, ist jedoch bis zum Juli-Update weiterhin funktionsfähig. **Kiosk (veraltet)** wird durch den neuen **Kiosk**-Profiltyp ersetzt (**Profil erstellen** > **Windows 10**  >  **Kiosk (Vorschau)**), der die Einstellungen zum Konfigurieren von Kiosks unter Windows 10 RS4 und höher enthält.

Gilt für Windows 10 und höher.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Benutzerdiagramm des Geräteprofils wieder vorhanden <!-- 2160133 -->
Während der Verbesserung der numerischen Werte, die im Diagramm des Geräteprofils dargestellt werden (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **(Übersicht)** ), wurde das Benutzerdiagramm vorübergehend entfernt.

Bei diesem Update ist das Benutzerdiagramm wieder enthalten und wird im Azure-Portal angezeigt.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Unterstützung für die Registrierung mit Windows Autopilot ohne Benutzerauthentifizierung <!-- 1165118 -->
Intune unterstützt jetzt die Registrierung mit Windows Autopilot ohne Benutzerauthentifizierung. Dies ist eine neue Option im Windows Autopilot-Bereitstellungsprofil („Autopilot Deployment mode“ (Autopilot-Bereitstellungsmodus) kann auf „Self-Deploying“ (Selbstbereitstellung) festgelegt werden).  Auf dem Gerät muss Windows 10 Insider Preview Build 17672 oder höher ausgeführt werden, außerdem muss ein TPM 2.0-Chip eingebaut sein, um diese Art der Registrierung erfolgreich abzuschließen. Da keine Benutzerauthentifizierung erforderlich ist, sollten Sie diese Option nur Geräte zuweisen, zu denen Sie physisch Zugang haben.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Neue Einstellung für Sprache/Region beim Konfigurieren von OOBE für AutoPilot <!-- 1821766 -->
Es steht eine neue Konfigurationseinstellung zur Verfügung, mit der die Sprache und Region für Autopilot-Profile während der Out-of-Box-Experience festgelegt werden kann. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen** > **Bereitstellungsmodus** = **Selbstbereitstellung** > **Standardwerte konfiguriert**, um die neuen Einstellungen anzuzeigen.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Neue Einstellung zum Konfigurieren der Gerätetastatur <!-- 1821768 -->
Es steht eine neue Einstellung zur Verfügung, mit der die Tastatur für AutoPilot-Profile während der Out-of-Box-Experience konfiguriert werden kann. Klicken Sie auf **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** > **Profil erstellen** > **Bereitstellungsmodus** = **Selbstbereitstellung** > **Standardwerte konfiguriert**, um die neuen Einstellungen anzuzeigen.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-Profile können bald Gruppenziele verwenden <!-- 1877935 -->
Autopilot-Bereitstellungsprofile können Azure AD-Gruppen zugewiesen werden, die Autopilot-Geräte enthalten.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="set-compliance-by-device-location----851881----"></a>Festlegen der Kompatibilität nach Gerätestandort <!-- 851881 ! -->
In einigen Situationen empfiehlt es sich, den Zugriff auf Unternehmensressourcen auf einen bestimmten Standort zu beschränken, der durch eine Netzwerkverbindung definiert ist. Sie können jetzt eine Kompatibilitätsrichtlinie (**Gerätekompatibilität** > **Standorte**) basierend auf der IP-Adresse des Geräts erstellen. Wird das Gerät außerhalb des IP-Bereichs bewegt, kann damit nicht auf Unternehmensressourcen zugegriffen werden.

Gilt für Android-Geräte 6.0 und höher mit der aktualisierten Unternehmensportal-App

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 AutoPilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Navigieren Sie zu **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Plattform** = **Windows 10 oder höher** > **Profiltyp** = **Geräteeinschränkungen** > **Konfigurieren** > **Windows-Blickpunkt** > **Endbenutzerfeatures**, um dieses Feature anzuzeigen. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Deinstallieren der letzten Softwareupdates von Windows 10 <!-- 1732948 -->
Wenn Sie Probleme mit Unterbrechungen auf Ihren Windows 10-Computern feststellen, können Sie das neueste Featureupdate bzw. Qualitätsupdate deinstallieren (einen Rollback ausführen). Die Deinstallation eines Feature- oder Qualitätsupdates ist für den Wartungskanal nur möglich, wenn das Gerät eingeschaltet ist. Durch die Deinstallation wird eine Richtlinie ausgelöst, die das vorherige Update auf Ihren Windows 10-Computern wiederherstellt. Sie können insbesondere für Featureupdates den Zeitraum, in dem eine Deinstallation für die neueste Version durchgeführt werden kann, auf 2–60 Tage einschränken. Um die Deinstallationsoptionen für das Softwareupdate festzulegen, wählen Sie im Azure-Portal auf dem Blatt **Microsoft Intune** die Option **Softwareupdates** aus. Klicken Sie auf dem Blatt **Softwareupdates** auf **Windows 10-Updateringe**. Sie können dann die Option **Deinstallieren** im Bereich **Übersicht** auswählen.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Durchsuchen aller Geräte nach IMEI und Seriennummer <!-- 1793685 -->
Sie können jetzt auf dem Blatt „Alle Geräte“ nach IMEI und Seriennummern suchen (E-Mail, UPN, Gerätename und Verwaltungsname sind weiterhin verfügbar). Klicken Sie in Intune auf **Geräte** > **Alle Geräte**, und geben Sie dann ein Suchwort in das Suchfeld ein.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Feld für Verwaltungsname kann bearbeitet werden <!-- 1875989 -->
Sie können das Feld für den Verwaltungsnamen auf dem Blatt **Eigenschaften** eines Geräts bearbeiten. Zum Bearbeiten dieses Felds wählen Sie **Geräte** > **Alle Geräte** > Gerät auswählen > **Eigenschaften** aus. Sie können das Feld für den Verwaltungsnamen zur eindeutigen Identifizierung eines Geräts verwenden.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Neue Filter für „Alle Geräte“: Gerätekategorie <!-- 1878520 -->
Sie können jetzt die Liste **Alle Geräte** nach Gerätekategorie filtern. Klicken Sie dafür auf **Geräte** > **Alle Geräte** > **Filter** > **Gerätekategorie**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Verwenden von TeamViewer zur Bildschirmübertragung zwischen iOS- und macOS-Geräten <!-- 1985547 -->
Administratoren können jetzt eine Verbindung mit [TeamViewer](device-profile-android-teamviewer.md) herstellen und eine Bildschirmübertragungssitzung mit iOS- und macOS-Geräten starten. iPhone, iPad und macOS-Benutzer können ihre Bildschirme live an andere Desktops oder mobile Geräte übertragen. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Unterstützen von mehreren Exchange-Connectors <!-- 2070451 -->
Sie sind nicht mehr auf einen Microsoft Intune Exchange Connector pro Mandant beschränkt. Intune unterstützt mehrere Exchange Connectors, sodass Sie Intune mithilfe von mehreren lokalen Exchange-Organisationen für bedingten Zugriff einrichten können.

Mit einem lokalen Exchange-Connector von Intune können Sie den Zugriff von Geräten auf Ihre lokalen Exchange-Postfächer verwalten. Dies ist abhängig davon, ob ein Gerät bei Intune registriert ist, und ob es den Gerätekompatibilitätsrichtlinien von Intune entspricht. Um einen Connector einzurichten, müssen Sie den lokalen Exchange-Connector von Intune aus dem Azure-Portal herunterladen und ihn auf einem Server in Ihrer Exchange-Organisation installieren. Klicken Sie im Microsoft Intune-Dashboard auf **Lokaler Zugriff** und dann unter **Setup** auf **Exchange ActiveSync-Connector**. Laden Sie den lokalen Exchange-Connector herunter, und installieren Sie ihn auf einem Server in Ihrer Exchange-Organisation. Da Sie nun nicht länger auf einen Exchange-Connector pro Mandant beschränkt werden, wenn Sie weitere Exchange-Organisationen haben, können Sie anhand des gleichen Durchgangs einen Connector für jede weitere Exchange-Organisation herunterladen und installieren.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Neues Gerätehardwaredetail: CCID <!-- 2156657 -->
Für jedes Gerät sind jetzt auch die CCID-Informationen (Chip Card Interface Device) verfügbar. Klicken Sie auf **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Hardware**, und sehen Sie sich die **Netzwerkdetails**> an, um diese anzuzeigen.

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Zuweisen aller Benutzer und aller Geräte als Bereichsgruppen <!-- 2196803 -->
Sie können alle Benutzer, alle Geräte sowie alle Benutzer und alle Geräte in Bereichsgruppen zuweisen. Klicken Sie hierzu auf **Intune-Rollen** > **Alle Rollen** > **Policy and profile manage** (Richtlinien- und Profil-Manager) > **Zuweisungen**, wählen Sie eine Zuweisung aus, und klicken Sie dann auf **Bereich (Gruppen)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>UDID-Informationen für iOS- und macOS-Geräte <!-- 2219806 -->
Navigieren Sie zu **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Hardware**, um die UDID (eindeutiger Gerätebezeichner) für iOS- und macOS-Geräte anzuzeigen. Die UDID ist nur für Unternehmensgeräte verfügbar (wie unter **Geräte** > **Ale Geräte**, Gerät auswählen, **Eigenschaften** > **Gerätebesitz** festgelegt).

### <a name="intune-apps"></a>Intune-Apps

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Verbesserte Problembehandlung für App-Installation <!-- 928990 -->
Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Wir versenden eine öffentliche Vorschau unserer Features zur App-Problembehandlung. Unter jedem einzelnen Gerät wird ein neuer Knoten mit der Bezeichnung **Verwaltete Apps** angezeigt. Hier sind die Apps aufgelistet, die über Intune MDM übermittelt wurden. Innerhalb des Knotens wird eine Liste mit App-Installationsstatus angezeigt. Bei Auswahl einer einzelnen App wird die Problembehandlungsansicht für diese bestimmte App angezeigt. In der Problembehandlungsansicht sehen Sie den End-to-End-Lebenszyklus der App, z. B. wann die App erstellt, geändert, festgelegt und an ein Gerät übermittelt wurde. Darüber hinaus wird bei einer nicht erfolgreichen App-Installation der Fehlercode und eine hilfreiche Nachricht zur Ursache des Fehlers angezeigt. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune-App-Schutzrichtlinien und Microsoft Edge <!-- 1818968 -->
Der Browser Microsoft Edge für Mobilgeräte (iOS und Android) unterstützt nun Microsoft Intune-App-Schutzrichtlinien. Benutzer von iOS- und Android-Geräten, die sich mit ihren Azure AD-Unternehmenskonten bei der Edge-Anwendung anmelden, werden von Intune geschützt. Auf iOS-Geräten lässt die Richtlinie **Require managed browser for web content** (Managed Browser für Webinhalt erforderlich) zu, dass Benutzer Links in Microsoft Edge öffnen können, wenn der Browser verwaltet wird.

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
Microsoft Intune stellt eine Funktion zur Installation von macOS-LOB-Apps aus dem Azure-Portal bereit. Sie können eine macOS-LOB-App zu Intune hinzufügen, nachdem sie von dem in GitHub verfügbaren Tool vorab verarbeitet wurde. Wählen Sie im Azure-Portal auf dem Blatt **Intune** die Option **Client-Apps** aus. Wählen Sie auf dem Blatt **Client-Apps** die Option **Apps** > **Hinzufügen** aus. Wählen Sie auf dem Blatt **App hinzufügen** die Option **Branchen-App** aus. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Integrierte App-Zuweisung im Android Enterprise-Arbeitsprofil für die Gruppen „Alle Benutzer“ und „Alle Geräte“ <!-- 1813073 -->
Sie können die integrierten Gruppen **Alle Benutzer** und **Alle Geräte** für die App-Zuweisung zum Android Enterprise-Arbeitsprofil nutzen. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune installiert benötigte Apps, die von Benutzern deinstalliert werden. <!-- 1947010 -->
Wenn ein Endbenutzer eine benötigte App deinstalliert, installiert Intune die App automatisch innerhalb von 24 Stunden neu, anstatt auf die Beendigung des siebentägigen Neuauswertungszyklus zu warten.

### <a name="device-configuration"></a>Gerätekonfiguration

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Geräteprofildiagramm und Statusliste zeigen alle Geräte in einer Gruppe <!-- 1449153 -->
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

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Anzeigen der Anrufer-ID im persönlichen Profil – Android Enterprise-Arbeitsprofil <!--1098984 -->
Wenn Sie ein persönliches Profil auf einem Gerät verwenden, sehen Endbenutzer möglicherweise nicht die Anrufer-ID-Details eines Arbeitskontakts. 

Seit diesem Update gibt es eine neue Einstellung unter **Android Enterprise** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
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
  - **Sicherer Start mit direktem Speicherzugriff (Direct Memory Access, DMA)**: Aktiviert VBS mit Schutzmaßnahmen wie sicherem Start und direktem Speicherzugriff. Für die DMA-Schutzfunktion ist Hardwaresupport erforderlich. Außerdem ist sie nur auf ordnungsgemäß konfigurierten Geräten aktiviert. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Verwenden eines benutzerdefinierten Antragstellernames auf dem SCEP-Zertifikat <!-- 2064190 -->
Sie können den allgemeinen Namen **OnPremisesSamAccountName** für einen benutzerdefinierten Antragsteller auf einem SCEP-Zertifikatprofil verwenden. Sie können z. B. `CN={OnPremisesSamAccountName})` verwenden.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Blockieren von Kamera und Bildschirmaufnahmen in Android Enterprise-Arbeitsprofilen <!-- 1098977 -->
Es werden zwei neue Eigenschaften zum Blockieren beim Konfigurieren der Geräteeinschränkungen für Android-Geräte hinzugefügt: 
- Kamera: Der Zugriff auf alle Kameras auf dem Gerät wird blockiert.
- Bildschirmaufnahme: Die Bildschirmaufnahme wird blockiert,. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen.

Gilt für Android Enterprise-Arbeitsprofile.


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Neue Schritte für die Registrierung für Benutzer auf Geräten mit macOS High Sierra 10.13.2 und höher <!--1734567 -->
Mit macOS high Sierra 10.13.2 wurde das Konzept der „vom Benutzer genehmigten“ MDM-Registrierung eingeführt. Intune kann mithilfe genehmigter Registrierungen einige sicherheitsrelevante Einstellungen verwalten. Weitere Informationen finden Sie in der Dokumentation zur Apple-Unterstützung: https://support.apple.com/HT208019.

Geräte, die mithilfe des macOS-Unternehmensportals registriert wurden, werden so lange als „nicht vom Benutzer genehmigt“ angesehen, bis der Endbenutzer sie in den Systemeinstellungen manuell genehmigt. Dafür werden Benutzer im macOS-Unternehmensportal unter macOS 10.13.2 und höher nun direkt aufgefordert, ihre Registrierung am Ende des Registrierungsprozesses manuell zu genehmigen. Die Intune-Administratorkonsole meldet, ob ein registriertes Gerät vom Benutzer genehmigt wurde.



### <a name="device-management"></a>Geräteverwaltung

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (ATP) und Intune sind vollständig integriert <!-- 1629303 -->

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

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune wird an Fluent Design System in der Unternehmensportal-App für Windows 10 angepasst <!-- 1195010 -->
Die Intune-Unternehmensportal-App für Windows 10 wurde mit der [Navigationsansicht von Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics) aktualisiert. An der Seite der App befindet sich eine statische, vertikale Liste aller Seiten der obersten Ebene. Klicken Sie auf einen beliebigen Link, um Seiten schnell anzuzeigen und zwischen ihnen zu wechseln. Dies ist das erste von mehreren Updates, die wir Ihnen im Rahmen unserer fortlaufenden Bestrebungen präsentieren werden, die Intune-Benutzeroberfläche zu optimieren. Wenn Sie sehen möchten, wie die aktualisierte Benutzeroberfläche aussieht, wechseln Sie zur Seite [Updates der Benutzeroberfläche für Benutzer-Apps in Intune](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Woche vom 16. April 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Verwenden des Cisco AnyConnect-Clients für iOS <!-- 1333708 -->

Wenn Sie ein neues VPN-Profil für iOS erstellen, stehen Ihnen jetzt zwei Optionen zur Verfügung: **Cisco AnyConnect** und **Cisco Legacy AnyConnect**. Die Cisco AnyConnect-Profile unterstützen 4.0.7x und neuere Versionen. Bereits existierende iOS Cisco AnyConnect VPN-Profile werden als **Cisco Legacy AnyConnect** bezeichnet und auch weiterhin mit Cisco AnyConnect 4.0.5x und älteren Versionen funktionieren.

> [!NOTE]
> Diese Änderung gilt nur für iOS. Es wird weiterhin nur eine Option von Cisco AnyConnect für Android- und macOS-Plattformen sowie Android Enterprise-Arbeitsprofile geben.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Jamf-registrierte macOS-Geräte können jetzt bei Intune registriert werden <!-- 2370684 -->

Die Versionen 1.3 und 1.4 des macOS-Unternehmensportals konnten nicht erfolgreich Jamf-Geräte bei Intune registrieren. Version 1.4.2 des macOS-Portals behebt dieses Problem.


## <a name="week-of-april-9-2018"></a>Woche vom 9. April 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Aktualisierter Hilfebereich der Unternehmensportal-App für Android <!-- 1631531 -->

Wir haben den Hilfebereich der Unternehmensportal-App für Android aktualisiert, sodass er den Best Practices der Android-Plattform entspricht. Wenn Benutzer jetzt ein Problem in der App haben, können sie auf **Menü** > **Hilfe** tippen und Folgendes tun:
- Diagnoseprotokolle an Microsoft senden
- E-Mail, die das Problem beschreibt, und die Incident-ID an einen Supportmitarbeiter des Unternehmens senden  

Unter [Senden von Protokollen an den Support Ihres Unternehmens per E-Mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android) und [Senden von Protokollen an Unternehmensportalentwickler für Android-Geräte](/intune-user-help/send-logs-to-microsoft-android) können Sie den aktualisierten Hilfebereich kennenlernen.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Neues Diagramm zum Trend von fehlgeschlagenen Registrierungen und Tabelle mit Gründen für das Fehlschlagen <!-- 1471783 -->

Auf der Seite „Enrollment Overview“ (Registrierungsübersicht) können Sie sich den Trend bei fehlgeschlagenen Registrierungen und die fünf häufigsten Gründe für das Fehlschlagen anzeigen lassen. Wenn Sie auf das Diagramm oder die Tabelle klicken, können Sie sich im Detail Informationen zu den Fehlern ansehen und erhalten Ratschläge zur Fehlerbehebung und zur Wartung.

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

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Schützen der lokalen Exchange-Daten mithilfe von Intune-App-Schutzrichtlinien und dem bedingten Zugriff <!-- 1056954 -->
Sie können jetzt lokale Exchange-Daten mit Outlook Mobile mithilfe von Intune App-Schutzrichtlinien (App Policy Protection, APP) und dem bedingten Zugriff (Conditional Access, CA) schützen. Um eine App-Schutzrichtlinie im Azure-Portal hinzuzufügen oder zu ändern, wählen Sie die Option **Microsoft Intune** > **Client-Apps** > **App-Schutzrichtlinien** aus. Bevor Sie dieses Feature verwenden, sollten Sie sicherstellen, dass Sie die [Anforderungen für Outlook für iOS und Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx) erfüllen.

## <a name="notices"></a>Benachrichtigungen

### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>Änderungsplan: Connector zum Herstellen der Verbindung von Exchange Online mit Intune wird in Intune nicht verfügbar sein <!-- 3105122 -->
Um Ihre Erfahrung mit Exchange Online und bedingtem Zugriff zu vereinfachen, werden wir den „Dienst-zu-Dienst“-Connector zum Herstellen der Verbindung von Exchange Online mit Intune deaktivieren. Diese Änderung beginnt mit dem Dienstupdate vom Dezember und wird mit dem Dienstupdate vom Februar 2019 abgeschlossen.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Sie erhalten diese Nachricht, da Sie unseren Unterlagen zufolge die „Dienst-zu-Dienst“-Connectorfunktionalität in Ihrer Umgebung verwenden. Der „Dienst-zu-Dienst“-Connector unterstützt die Intune-Verwaltung von Exchange Active Sync Only-Geräten für Exchange Online und nicht die lokale Infrastruktur. Dieser Connector scheint aufgrund der Art, wie er in der Konsole angezeigt wird, für bedingten Zugriff (Conditional Access, CA) erforderlich zu sein, ist es in der Praxis jedoch nicht. Mit dem Dezember-Update des Intune-Diensts werden wir die Schaltfläche zum Einrichten neuer Connector deaktivieren, damit dies in der Konsole eindeutig ist. Anschließend werden im Februar 2019 alle vorhandenen Connector zum Herstellen der Verbindung von Exchange Online mit Intune deaktiviert.

Wenn Sie diese Connector in Ihrer Umgebung verwenden, können Sie nach dem Deaktivieren der Connector im Februar keine Exchange Active Sync Only-Geräte in Intune mehr überwachen oder zurücksetzen. Während dieser Änderung werden keine Auswirkungen für Ihre Endbenutzer erwartet.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?

Wenn Sie den „Dienst-zu-Dienst“-Connector eingerichtet haben und über Exchange Active Sync Only-Geräte verfügen, wechseln Sie zu anderen Methoden zum Verwalten Ihrer Geräte. Hierzu stehen Ihnen folgende Optionen zur Verfügung:

- Registrieren von Geräten in der mobilen Geräteverwaltung (Mobile Device Management, MDM)
- Verwenden von App-Schutzrichtlinien zum Verwalten Ihrer Geräte
- Verwenden Sie Exchange-Steuerelemente wie hier in der Dokumentation beschrieben. 

#### <a name="additional-information"></a>Weitere Informationen
[Konfigurieren des Exchange-Dienstconnectors für Intune und Exchange Online](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Geplante Änderung: Verbesserung der Leistung von Intune for Education <!--1750215-->
Intune for Education wird aktualisiert, um die Geschwindigkeit und Zuverlässigkeit beim Zuweisen von Einstellungen zu Benutzern oder Geräten zu verbessern. Im Rahmen dieser Änderung werden die Richtlinien- oder Einstellungszuweisungen gegen Ende November in neue Gruppen verschoben.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?

Als Intune for Education-Kunde stehen Ihnen die beiden dynamischen Azure Active Directory-Gruppen „Alle Benutzer“ und „Alle Geräte“ zur Verfügung. Durch dieses Update werden die Azure AD-Gruppen „Alle Benutzer“ und „Alle Geräte“ nicht mehr in der Intune for Education-Konsole angezeigt. Sie werden jedoch weiterhin in der Intune-Konsole in Azure angezeigt und in „All Users (Obsolete, do not use)“ (Alle Benutzer (Veraltet, nicht verwenden)) und „All Devices (Obsolete, do not use)“ (Alle Geräte (Veraltet, nicht verwenden)) umbenannt.

Wenn die Updates veröffentlicht werden, müssen Sie keine Azure AD-Gruppen mehr verwenden, um Apps und Einstellungen in Intune zuzuweisen. Die Einstellungszuweisungen werden in neue Gruppen in der Intune for Education-Konsole verschoben, die wie zuvor als „Alle Benutzer“ und „Alle Geräte“ angezeigt werden. Diese Änderungen werden über das Back-End durchgeführt, Sie werden also keinen Unterschied in der Intune for Education-Konsole bemerken. Es gibt keine Auswirkungen auf die Endbenutzer oder die registrierten Geräte. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Sie müssen nichts tun, während wir Ihre Richtlinienzuweisungen verschieben. Wenn Sie derzeit Richtlinien über die Intune for Education-Konsole zuweisen, können Sie damit fortfahren.

Wenn Sie derzeit über Intune in Azure Richtlinien zu den zuvor erwähnten Azure AD-Gruppen zuweisen, weisen Sie diese ab jetzt den Gruppen „Alle Benutzer“ und „Alle Geräte“ in der Intune for Education-Konsole zu. Wenn die Azure AD-Gruppen mit dem Zusatz „Obsolete“ (Veraltet) in der Konsole angezeigt werden, sollten Sie keine Richtlinien mehr über Azure AD zuweisen. Wenn Sie die umbenannten Gruppen derzeit nicht für andere Zwecke verwenden, sollten Sie diese löschen.


### <a name="plan-for-change-intune-will-move-to-support-macos-1012-and-higher-in-december---2970975--"></a>Geplante Änderung: Ab Dezember unterstützt Intune macOS 10.12 und höher <!--2970975--> 

Apple hat gerade macOS 10.14 veröffentlicht. Dementsprechend wird Intune ab Dezember 2018 macOS 10.12 und höher unterstützen. 

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?

Ab Dezember können sich Endbenutzer mit Geräten, die macOS 10.11 oder früher verwenden, nicht mehr über das Unternehmensportal für Intune registrieren. Sie müssen ihre Geräte auf macOS 10.12 oder höher und die Unternehmensportal-App auf die aktuellste Version upgraden, um weiterhin Support zu erhalten und die neuesten Features nutzen zu können. 

MacOS-Versionen 10.12 und höher werden aktuell auf folgenden Geräten unterstützt: 
- MacBook (Ende 2009 oder später) 
- iMac (Ende 2009 oder später)
- MacBook Air (Ende 2010 oder später)  
- MacBook Pro (Ende 2010 oder später) 
- Mac Mini (Ende 2010 oder später) 
- Mac Pro (Ende 2010 oder später) 

Nach Dezember können Benutzer mit Geräten, die nicht oben aufgeführt sind, nicht mehr auf die aktuellste Version der Unternehmensportal-Apps für macOS zugreifen. Bereits registrierte Geräte mit nicht unterstützten Versionen vor macOS 10.12 werden weiterhin verwaltet und in der Intune-Verwaltungskonsole aufgeführt.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?

- Fordern Sie Ihre Endbenutzer dazu auf, Ihr Gerät vor Dezember 2018 auf eine unterstützte Betriebssystemversion upzugraden. 
- Sehen Sie sich die Intune-Berichte in der Intune-Konsole an, um zu erfahren, welche Geräte oder Benutzer davon möglicherweise betroffen sind. Navigieren Sie zu „Geräte“ > „Alle Geräte“, und filtern Sie nach Betriebssystem. Sie können weitere Spalten hinzufügen, um besser bestimmen zu können, welche Benutzer Ihrer Organisation Geräte mit macOS 10.11 verwenden. 
- Wenn Sie die hybride Verwaltung mobiler Geräte verwenden, navigieren Sie in der Configuration Manager-Konsole zu „Assets und Konformität“ > „Geräte in der Configuration Manager-Konsole“, klicken Sie mit der rechten Maustaste auf die Spalten, um die Spalten „Betriebssystem“ und „Clientversion“ hinzuzufügen, und sortieren Sie nach Betriebssystem. Beachten Sie, dass die hybride Verwaltung mobiler Geräte inzwischen veraltet ist. Sie sollten daher so bald wie möglich zu Intune in Azure wechseln. 
 
#### <a name="additional-information"></a>Weitere Informationen
Weitere Informationen finden Sie unter [Registrieren Ihres macOS-Geräts bei Intune mit der Unternehmensportal-App](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp).
 

### <a name="plan-for-change-new-intune-support-experience-for-premier-customers"></a>Änderungsplanung: Neue Intune-Supportbenutzererfahrung für Premier-Kunden 
Als Microsoft Premier-Kunde können Sie derzeit das Microsoft Premier Online-Portal (MPO) (premier.microsoft.com) und Intune in Azure (portal.azure.com) nutzen, um Supportanfragen für Intune zu erstellen. Ab dem 3. Dezember 2018 können Sie Supportanfragen nur in Intune unter Azure erstellen, um die Premier-Supportbenutzererfahrung auszuweiten.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Nach dem 3. Dezember können Sie keine Supportanfragen mehr im MPO-Portal erstellen.  Wenn Sie es trotzdem versuchen, sehen Sie eine Eingabeaufforderung, die Sie nicht ablehnen können, um Sie zu Intune unter Azure umzuleiten. Hier können Sie eine Supportanfrage erstellen, die an den Microsoft-Support für Intune weitergeleitet wird, um Ihr Problem bald zu diagnostizieren und zu lösen. Im MPO-Portal erstellte Support-Anfragen können nicht im Azure-Portal angezeigt werden, darum sollten Sie keine Supportanfragen mehr im MPO-Portal erstellen.  

Wenn Sie die Hybridverwaltung mobiler Geräte (Hybrid Mobile Device Management, Hybrid MDM) oder Co-Verwaltung verwenden, können Sie weiterhin im MPO-Portal Supportanfragen für Configuration Manager erstellen, aber verwenden Sie zum Erstellen von Supportanfragen für Intune das Azure-Portal. Zur Erinnerung: Die hybride Verwaltung mobiler Geräte ist veraltet, und Sie sollten planen, so bald wie möglich zu Intune in Azure zu wechseln. Weitere Informationen finden Sie unter [Wechsel von der hybriden mobilen Geräteverwaltung zu Intune in Azure](https://aka.ms/hybrid_notification).

Beachten Sie, dass nur Benutzer mit den Rollen „Globaler Administrator“, „Intune-Dienstadministrator“ und „Dienstunterstützungsadministrator“ im Azure-Portal Supporttickets erstellen können.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
- Verwenden Sie nicht mehr MPO, sondern stattdessen Intune unter Azure zum Erstellen und Verwalten aller Intune-Supportanfragen.  
- Benachrichtigen Sie bei Bedarf Ihren Helpdesk, und aktualisieren Sie die Dokumentation.
- Wenn Benutzer ohne die Rollen „Globaler Administrator“ oder „Intune-Dienstadministrator“ derzeit Supportanfragen in MPO erstellen, weisen Sie ihnen die Rolle „Dienstunterstützungsadministrator“ in Azure Active Directory zu, damit sie weiterhin Supporttickets im Azure-Portal erstellen können.
- Klicken Sie auf „Weitere Informationen“, um weitere Informationen und nützliche Links zu nutzen.

#### <a name="additional-information"></a>Weitere Informationen
Weitere Informationen finden Sie im folgenden [Blogbeitrag des Microsoft Intune-Supportteams](https://aka.ms/IntuneSupport_MPO_to_Azure).


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Maßnahme erforderlich: Bitte aktualisieren Sie Ihre Android-Gerätebeschränkungen oder die Kennworteinstellungen für die Konformitätsrichtlinie in Intune
Intune wird für Geräte mit Android 4.4 und höher den Kennworttyp „Gerätestandard“ entfernen. Aufgrund von unterschiedlichen Android-Plattformen und Gerätestandards wird diese Richtlinie häufig von dem Gerät als optional behandelt. Wir entfernen in einem der nächsten Releases diese Einstellung von der Benutzeroberfläche, um Unklarheiten dazu zu beseitigen, wann diese Einstellung für Android erzwungen wird. 
#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
- Wenn Sie ein Kennwort für die Geräte erforderlich machen möchten, wird empfohlen, dass Sie anstelle des „Gerätestandards“ Ihre Android-Plattformprofile bearbeiten, um den erforderlichen Kennworttypen deutlich hervorzuheben.
- Wenn Sie möchten, dass der Endbenutzer entscheidet, ob er ein Kennwort erstellen möchte, klicken Sie auf die Schaltfläche „Nicht konfiguriert“. Wenn wir diese Einstellung von der Benutzeroberfläche entfernen, sie aber immer noch festgelegt ist, werden Sie aufgefordert, einen anderen Wert als den „Gerätestandard“ auszuwählen, wenn Sie das nächste Mal das Profil bearbeiten.
Wie sollte ich mich für die Änderung vorbereiten?
Prüfen Sie die Kennworteinstellungen für die Einschränkungen und Konformitätsrichtlinien für Android- und Android Enterprise-Geräte. Diese sind unter „System security for Compliance policies“ (Systemsicherheit für Konformitätsrichtlinien) und entweder unter „Gerätekennwort“ oder unter „Work profile settings for Device restrictions“ (Arbeitsprofileinstellungen für Geräteeinschränkungen) aufgeführt. Unter „zusätzliche Informationen“ finden Sie einen Link zu weiteren Informationen und Screenshots zur Konfiguration dieser Einstellungen.
#### <a name="additional-information"></a>Zusätzliche Informationen
https://aka.ms/PasswordSettings 

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple erfordert Updates für die Transportsicherheit für Anwendungen <!--748318-->
Apple hat angekündigt, dass bestimmte Anforderungen für die Transportsicherheit für Anwendungen (Application Transport Security, ATS) erzwungen werden. ATS wird verwendet, um eine strengere Sicherheit in allen App-Kommunikationen über HTTPS zu erzwingen. Diese Änderung wirkt sich auf Intune-Kunden aus, die die iOS-Unternehmensportal-App verwenden. Die aktuellen Informationen finden Sie auf dem [Intune-Support-Blog](https://aka.ms/compportalats).

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Geplante Änderung: Umstellung von Intune auf TLS 1.2
Ab dem 31. Oktober 2018 unterstützt Intune die Version 1.2 des Transport Layer Security-Protokolls (TLS), um die beste Verschlüsselung bereitzustellen und den Dienst standardmäßig sicherer zu gestalten und auf andere Microsoft-Dienste wie Microsoft Office 365 auszurichten. Für Office wurde diese Änderung in MC128929 bekannt gegeben.

Ab dem 31. Oktober 2018 unterstützt auch das Unternehmensportal TLS 1.2

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Ab dem 31. Oktober 2018 unterstützt Intune die Versionen 1.0 oder 1.1 des TLS-Protokolls nicht mehr. Alle Client-Server- und Browser-Server-Kombinationen sollten TLS 1.2 verwenden, um eine problemlose Verbindung mit Intune zu gewährleisten. Beachten Sie, dass diese Änderung sich auf Endbenutzergeräte auswirkt, die TLS 1.2 nicht verwenden können und nicht mehr von Intune unterstützt werden, aber weiterhin Richtlinien über Intune erhalten. Dazu zählen Geräte, auf denen Android 4.3 oder früher ausgeführt wird. Eine Liste der betroffenen Geräte und Browser finden Sie im Folgenden unter „Weitere Informationen“.

Wenn ab dem 31. Oktober 2018 Probleme in Zusammenhang mit der Verwendung einer älteren Version von TLS auftreten, müssen Sie auf TLS 1.2 aktualisieren oder sich ein Gerät zulegen, das TLS 1.2 unterstützt, um diese zu lösen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Es wird empfohlen, Abhängigkeiten von TLS 1.0 und 1.1 proaktiv aus Ihren Umgebungen zu entfernen und TLS 1.0 und 1.1 nach Möglichkeit auf Betriebssystemebene zu deaktivieren. Beginnen Sie schon heute mit der Planung der Migration zu TLS 1.2. Im Blogbeitrag unten finden Sie eine Liste der Geräte, die derzeit nicht von Intune unterstützt werden, aber weiterhin Richtlinien erhalten, und bei denen keine Kommunikation mithilfe von TLS 1.2 möglich ist. Sie müssen diese Endbenutzer möglicherweise darüber benachrichtigen, dass sie den Zugriff auf Unternehmensressourcen verlieren.

**Weitere Informationen:** [Umstellung von Intune auf TLS 1.2 für die Verschlüsselung](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)



## <a name="see-also"></a>Siehe auch
* [Microsoft Intune-Blog](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roadmap für die Cloudplattform](https://www.microsoft.com/cloud-platform/roadmap)
* [What‘s new in the Intune App UI (Neues auf der Intune-App-Benutzeroberfläche)](whats-new-app-ui.md)
* [Neuerungen in den vorherigen Monaten](whats-new-archive.md)
