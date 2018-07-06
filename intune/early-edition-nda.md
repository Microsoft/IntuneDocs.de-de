---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0500194f5afaba11f37b84bbdf606e6167632a71
ms.sourcegitcommit: afa2e84d5cadf5542ecabc26e61dc71919992a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340177"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Die Early Edition für Microsoft Intune: Juli 2018

> [!Note]
> Benachrichtigung zum Geheimhaltungsvertrag: Die folgenden Änderungen befinden sich in der Entwicklung für Intune. Die Freigabe dieser Informationen erfolgt im Geheimhaltungsvertrag (GHV) auf einer sehr begrenzten Basis. Posten Sie keine der folgenden Informationen in den sozialen Medien oder auf öffentlichen Websites wie Twitter, UserVoice, Reddit usw. 

Die **Early Edition** enthält eine Liste der Features, die im Rahmen des Geheimhaltungsvertrags freigegeben und in späteren Versionen von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Verfassen Sie außerhalb Ihres Unternehmens keinen Tweet oder Post auf UserVoice o.Ä. über diese Informationen. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Zurücksetzen von Gerätekennungen über die Unternehmensportal-App für Windows 10 <!-- 2101282 --> 
Ihre Mitarbeiter können schon bald die PIN bzw. die Kennung ihres Geräts direkt über die Unternehmensportal-App für Windows 10 zurücksetzen. Diese Funktion ist dann jeweils auf remoten und lokal verwalteten Intune-Geräten verfügbar, die Zurücksetzungen der Kennung unterstützen. Je nach Gerätetyp entfernt eine Anforderung, die für ein Remotegerät gestellt wird, entweder die aktuelle Kennung des Geräts oder erstellt eine temporäre Kennung. Benutzer, die eine Zurücksetzung für ein lokales Gerät anfordern, werden an die App „Einstellungen“ des Geräts weitergeleitet.

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Verwenden von S/MIME zum Verschlüsseln und Signieren von mehreren Geräten eines Benutzers <!-- 1333642 -->
In einem zukünftigen Update ist eine S/MIME-E-Mail-Verschlüsselung enthalten, die ein neu importiertes Zertifikatprofil verwendet (Navigieren Sie zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie die Plattform aus und dann den Profiltyp **Importiertes PKCS-Zertifikat**). In Intune können Sie Zertifikate im PFX-Format importieren. Intune kann dann genau diese Zertifikate an mehrere Geräte übergeben, die durch einen einzelnen Benutzer registriert wurden. Außerdem enthalten:

- Das native iOS-E-Mail-Profil unterstützt die Aktivierung der S/MIME-Verschlüsselung mithilfe importierter Zertifikate im PFX-Format.
- Die native E-Mail-App auf Windows Phone 10-Geräten verwendet automatisch das S/MIME-Zertifikat.
- Die privaten Zertifikate können über mehrere Plattformen übermittelt werden. Jedoch unterstützen nicht alle E-Mail-Apps S/MIME.
- Auf anderen Plattformen müssen Sie möglicherweise die E-Mail so konfigurieren, dass Sie S/MIME zulässt.  
- E-Mail-Apps, die die S/MIME-Verschlüsselung unterstützen, behandeln das Abrufen von Zertifikaten für die S/MIME-E-Mail-Verschlüsselung womöglich in einer Art und Weise, die von MDM nicht unterstützt werden kann, z.B. durch Lesen über den Zertifikatspeicher des Verlegers.

Unterstützt unter: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Verwendung von VPP-Gerätelizenzen, zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung <!-- 1608345 -->
Sie können Gerätelizenzen des Volume Purchase Program (VPP) verwenden, um das Unternehmensportal während der Registrierungsvorgänge des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) vorab bereitzustellen. Geben Sie dazu bei der Erstellung oder Bearbeitung eines Registrierungsprofils das VPP-Token an, das Sie zum Installieren des Unternehmensportals verwenden möchten. Stellen Sie sicher, dass Ihr Token nicht abläuft, und dass Sie über genügend Lizenzen für die Unternehmensportal-App verfügen. In Fällen, in denen das Token abläuft oder über keine Lizenzen mehr verfügt, überträgt Intune stattdessen das App Store-Unternehmensportal mithilfe von Push (dafür ist die Eingabe eine Apple-ID erforderlich).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massenlöschung von Geräten auf dem Blatt „Geräte“ <!-- 1793693 -->
Sie können mehrere Geräte gleichzeitig über das Blatt „Geräte“ löschen. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie die Geräte aus, die Sie löschen möchten, und klicken Sie auf **Löschen**. Es wird eine Warnung für die Geräte ausgegeben, die nicht gelöscht werden können.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Neues WLAN-Gerätekonfigurationsprofil für Windows 10 und höher <!-- 1879077 -->
Aktuell können Sie WLAN-Profile mithilfe von XML-Dateien importieren und exportieren. Sie können ein WLAN-Gerätekonfigurationsprofil genau wie für andere Plattformen auch direkt in Intune erstellen.

Um ein Profil zu erstellen, öffnen Sie **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **WLAN**. 

Gilt für Windows 10 und höher.

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Umbenennung der Dateierweiterung branchenspezifischer Windows-Apps (LOB-Apps) <!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps werden von *.appx.* und *.appxbundle* in *.msix* und *.msixbundle* umbenannt. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Mobile Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Das automatisch dem Konfigurationsprofil zugewiesene Windows Defender ATP-Konfigurationspaket <!-- 2144658 -->
Wenn Sie [Advanced Threat Protection verwenden und Geräte in Intune onboarden](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile), laden Sie derzeit ein Konfigurationspaket herunter und fügen es Ihrem Konfigurationsprofil hinzu. In einem zukünftigen Update ruft Intune das Paket automatisch aus dem Windows Defender Security Center ab und fügt es Ihrem Profil hinzu.

Gilt für Windows 10 und höher.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>„Kiosk – Veraltet“ ist ausgegraut und kann nicht verändert werden <!-- 2149998 -->
Das [Kiosk-Feature](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Geräteeinschränkungen**) wird als veraltet markiert und durch [Kiosk-Einstellungen für Windows 10 und höher](kiosk-settings.md) ersetzt. Das Feature **Kiosk – Veraltet** wird ausgegraut, und die Benutzeroberfläche kann nicht verändert oder aktualisiert werden. 

Informationen zum Aktivieren des Kioskmodus finden Sie unter [Kioskeinstellungen für Windows 10 und höher in Intune](kiosk-settings.md).

Gilt für Windows 10 und höher, Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>APIs für die Verwendung von Zertifizierungsstellen von Drittanbietern <!-- 2184013 -->
Es wird eine Java-API eingeführt, mit der die Integration von Zertifizierungsstellen von Drittanbietern in Intune und SCEP möglich ist. Benutzer können so das SCEP-Zertifikat einem Profil hinzufügen und es über MDM auf Geräte anwenden.

Derzeit unterstützt Intune [SCEP-Anforderungen über Active Directory-Zertifikatdienste](certificates-scep-configure.md).

### <a name="check-for-sccm-compliance----2192052---"></a>Überprüfung auf SCCM-Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (SCCM) (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). SCCM sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle SCCM-Signale auffordern, „compliant“ (konform) zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. In SCCM hat diese Anforderung den Zustand „Installed“ (Installiert). Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und wenn die Lizenzen für das Unternehmensportal knapp werden.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Erforderliche Bestätigung zur Löschung von VPP-Token, die für die Vorabbereitstellung des Unternehmensportals verwendet werden <!-- 2237634 -->
Für die Löschung eines VPP-Tokens (Volume Purchase Program) ist eine Bestätigung notwendig, falls das Token zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwendet wird.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Automatisches Markieren von Android-Geräten als „corporate“ (geschäftlich) über Samsung Knox Mobile Enrollment <!-- 2404851 -->
In der Standardeinstellung werden Android-Geräte, die über Samsung Knox Mobile Enrollment registriert sind, unter **Gerätebesitz** als **geschäftlich** markiert. Sie müssen also Unternehmensgeräte nicht manuell über IMEI oder Seriennummern vor der Registrierung mit Knox Mobile Enrollment identifizieren.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Umschaltfläche zum Anzeigen oder Ausblenden der Schaltfläche „Sitzung beenden“ auf einem Kioskbrowser <!-- 2455253 -->
Sie können konfigurieren, ob Kioskbrowser die Schaltfläche „Sitzung beenden“ anzeigen oder nicht. Sie finden das Steuerelement unter **Gerätekonfiguration** > **Kiosk (Vorschauversion)** > **Kioskwebbrowser**. Wenn die Schaltfläche aktiviert ist und ein Benutzer darauf klickt, fordert die App eine Bestätigung zum Beenden der Sitzung an. Wenn dies bestätigt wird, löscht der Browser alle Browserdaten und navigiert zurück zur Standard-URL.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Erstellen eines eSIM-Mobilfunkkonfigurationsprofils <!-- 2564077 -->
Unter **Gerätekonfiguration** können Sie ein eSIM-Mobilfunkprofil erstellen. Sie können eine Datei importieren, die Mobilfunk-Aktivierungscodes enthält, die von Ihrem Mobilfunkanbieter bereitgestellt werden. Diese Profile können daraufhin für Ihre mit eSIM-LTE aktivierten Windows 10-Geräte bereitgestellt werden, z.B. für das Surface Pro LTE und andere eSIM-fähigen Geräte.

Überprüfen Sie, ob Ihre [Geräte eSIM-Profile unterstützen](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gilt für Windows 10 und höher. 




<!-- 1806 start -->

### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Anzeigen von in Konflikt stehenden Gerätekonfigurationsprofilen <!-- 1556983 -->
Unter **Gerätekonfiguration** wird eine Liste der vorhandenen Profile angezeigt. Mit diesem Update wird eine neue Spalte hinzugefügt, die Details zu Profilen enthält, die in Konflikt stehen. Sie können eine in Konflikt stehende Zeile anklicken, um die Einstellung und das Profil anzuzeigen, bei denen der Konflikt vorhanden ist. 

Weitere Informationen finden Sie unter [Gerätekonfigurierungsprofile](device-profiles.md).

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>COSU-Unterstützung (corporate-owned, single use, Unternehmensgeräte für spezifische Anwendungsfälle) für Android-Geräte <!-- 1630973 -->

Intune wird zukünftig kioskartige, stringent verwaltete Android-Geräte unterstützen, deren Einsatzbereich stark eingeschränkt ist. Dadurch können Administratoren festlegen, dass auf einem Gerät nur eine oder einige wenige Apps und Aktionen von Benutzern verwendet werden dürfen.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-Unterstützung für das Programm zur Geräteregistrierung von Apple<!-- 747651 -->

Intune wird zukünftig die Registrierung von macOS-Geräten über das Programm zur Geräteregistrierung (DEP) von Apple unterstützen. Gehen Sie hierzu folgendermaßen vor:

1. Weisen Sie unter deploy.apple.com einem MDM-Server die macOS-Seriennummern zu.
2. Importieren Sie die Seriennummern in Intune.
3. Erstellen Sie für das Registrierungsprogramm ein Profil, das auf macOS-Geräte abgestimmt ist.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Google-Namensänderungen für Android for Work und Play for Work <!--842873 -->
Intune wird zukünftig Android for Work-Terminologie aktualisieren, wenn sich Google-Markennamen ändern.  Die Benennungen „Android for Work“ und „Play for Work“ werden nicht mehr verwendet. Die Terminologie wird je nach Kontext angepasst:

- „Android Enterprise“ bezieht sich auf den allgemeinen modernen Android-Verwaltungsstapel.
- „Arbeitsprofil“ oder „Profilbesitzer“ bezieht sich auf BYOD-Geräte, die mit Arbeitsprofilen verwaltet werden.
- „Managed Google Play“ bezieht sich auf den App Store von Google.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Überwachen des Konfigurationsstatus von iOS-Apps auf allen Geräten <!-- 880037 eeready eestaged -->

Als Microsoft Intune-Administrator können Sie zukünftig auf jedem verwalteten Gerät den Konfigurationsstatus von iOS-Apps überwachen. Klicken Sie im Azure-Portal unter **Microsoft Intune** auf **Geräte** > **Alle Geräte**. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, für das ein Blatt angezeigt werden soll. Klicken Sie auf dem Geräteblatt auf **App-Konfiguration**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können zukünftig auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Erstellen von Konformitätsrichtlinien für macOS-Geräte über Firewalleinstellungen <!-- 1497640 -->
Beim Erstellen einer neuen macOS-Konformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: macOS** > **Systemsicherheit**) sind einige neue **Firewall**-Einstellungen verfügbar: 
- **Firewall:** Hier konfigurieren Sie, wie eingehende Verbindungen in Ihrer Umgebung behandelt werden.
- **Eingehende Verbindungen:** Mit dieser Einstellung können Sie eingehende Verbindungen für grundlegende Internetdienste wie DHCP, Bonjour und IPSec zulassen und alle anderen eingehenden Verbindungen **blockieren**. Alle Freigabedienste werden durch diese Einstellung blockiert.
- **Geschützter Modus:** Durch die **Aktivierung** dieser Einstellung hindern Sie das Gerät daran, auf Suchanforderungen zu antworten. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps.

Gilt für: macOS 10.12 und höher

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Verwenden von „sAMAccountName“ als Kontobenutzername für E-Mail-Profile <!-- 1500307 -->

Zukünftig können Sie das lokal vorhandene Attribut **sAMAccountName** als Kontobenutzername für Android-, iOS- und Windows 10-E-Mail-Profile verwenden. Mit den Attributen `domain` oder `ntdomain` können Sie in Azure Active Directory (Azure AD) außerdem die Domain abrufen. Alternativ können Sie auch eine benutzerdefinierte statische Domäne eingeben.

Zur Nutzung dieses Features müssen Sie das `sAMAccountName`-Attribut Ihrer lokalen Active Directory-Umgebung mit Azure AD synchronisieren.

Gilt für: Android, iOS, Windows 10 und höher

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts <!-- 1506985 -->

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, mobile Anwendungsverwaltung) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Zurücksetzen ausgewählter App-Daten einer Organisation <!-- 1507030 -->
Wenn die in den APP-Einstellungen festgelegten Bedingungen nicht erfüllt sind, können Administratoren zukünftig durch eine neue Aktion ausgewählte Organisationsdaten zurücksetzen.  Dieses Feature hilft Administratoren dabei, vertrauliche Organisationsdaten mithilfe festgelegter Kriterien automatisch zu schützen und aus Anwendungen zu entfernen.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Widerrufen einer Lizenz für iOS-Apps, die über VPP erworben wurden <!-- 1777384 -->
Als Microsoft Intune-Administrator haben Sie zukünftig die Möglichkeit, die Lizenz für eine bestimmte iOS-App zu widerrufen, die über das Volume Purchase Program (VPP) erworben wurde. Sie können Benutzer benachrichtigen, wenn ihnen eine App nicht mehr zugewiesen ist. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Die Anzahl der widerrufenen Lizenzen wird innerhalb der Intune-**App**-Workload im Knoten **Lizenzierte Apps** angezeigt. Weitere Informationen zu iOS-VPP-Apps finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Widerrufen einer iOS-VPP-App-Lizenz <!-- 1863797 -->
Als Administrator haben Sie zukünftig die Möglichkeit, eine iOS-VPP-App-Lizenz zu widerrufen, die einem Benutzer oder Gerät zugewiesen ist. Dasselbe erreichen Sie mit der Deinstallation einer iOS-VPP-App. Anschließend können Sie die App-Lizenz einem anderen Benutzer oder Gerät zuweisen. Weitere Informationen zu iOS-VPP-App-Lizenzen, finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

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

### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Updates für nicht konforme Meldungen in der Unternehmensportal-App <!-- 1832222 -->
Die Meldung, die Benutzern angezeigt wird, wenn ein Gerät nicht konform ist, wird überarbeitet. Die Meldungen behalten ihre ursprünglichen Bedeutungen bei, werden jedoch mit benutzerfreundlicherer Sprache und weniger Fachbegriffen aktualisiert. Die Links zu Dokumentationen und Wiederherstellungsschritten werden auf den neuesten Stand gebracht.  

Die folgenden Texte (vorher und nachher) sind ein Beispiel für die Verbesserungen an den angezeigten Meldungen:  

Vorher: *Dieses Gerät hat nicht innerhalb des von Ihrem IT-Administrator festgelegten Zeitraums eine Verbindung mit dem Intune-Dienst hergestellt. Um dieses Problem zu beheben, öffnen Sie die Unternehmensportal-App auf Ihrem Gerät, und klicken Sie auf die Schaltfläche „Konformität überprüfen“.*  

Nachher: *Your device has not checked in with your organization in a while. To reestablish a connection, open the Company Portal app on your device and tap Check Settings for your device*. (Ihr Gerät wurde länger nicht mehr bei Ihrer Organisation eingecheckt. Öffnen Sie die Unternehmensportal-App auf Ihrem Gerät, und tippen Sie für Ihr Gerät auf „Einstellungen überprüfen“, um die Verbindung wiederherzustellen.)  

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Bearbeiten von Office 365 Pro Plus-App-Bereitstellungen <!-- 2150145 -->
Als Microsoft Intune-Administrator haben Sie zukünftig mehr Möglichkeiten, Ihre Office 365 Pro Plus-App-Bereitstellungen zu bearbeiten. Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps**. Wählen Sie aus der Liste der Apps Ihre Office 365 Pro Plus-Suite aus.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Duplikatprüfung auf Zeilenbasis beim Hochladen unternehmensspezifischer Gerätebezeichner <!-- 2203794 -->
Beim Hochladen von Unternehmensbezeichnern stellt Intune eine Liste mit mehrfach vorhandenen Bezeichnern bereit und bietet Ihnen die Möglichkeit, die vorhandenen Informationen zu ersetzen oder beizubehalten. Der Bericht wird angezeigt, wenn nach dem Klicken auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Bezeichner hinzufügen** Duplikate vorhanden sind. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Manuelles Hinzufügen von Unternehmensgerätebezeichnern <!-- 2203803 -->
Zukünftig können Sie Unternehmensgerätebezeichner manuell hinzufügen. Klicken Sie auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen**.

### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Neue Status für Geräte in der Gerätekonfiguration <!-- 2308882 -->
Unter **Gerätekonformität** > **Richtlinien** > Richtlinie auswählen > **Übersicht** wurden folgende neue Status hinzugefügt:
- Erfolgreich
- Fehler
- Konflikt
- Ausstehend
- Nicht anwendbar

Nicht anwendbar. Außerdem wird eine Grafik angezeigt, in der die Anzahl der Geräte für andere Plattformen zu sehen ist. Beim Aufruf eines iOS-Profils wird beispielsweise auf der neuen Kachel die Anzahl der Nicht-iOS-Geräte angezeigt, die diesem Profil ebenfalls zugewiesen sind. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Unterstützung von Drittanbieter-Antivirenlösungen in Gerätekonformitätsrichtlinien <!-- 2325484 -->
Beim Erstellen einer Gerätekonformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: Windows 10 und höher** > **Einstellungen** > **Systemsicherheit**) sind neue Optionen für **Gerätesicherheit** verfügbar: 
- **Antivirus**: Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec) überprüfen, die beim Windows-Sicherheitscenter registriert sind. 
- **AntiSpyware**: Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Anti-Spyware-Lösungen (beispielsweise Symantec) überprüfen, die beim Windows Security Center registriert sind. 

Gilt für: Windows 10 und höher 

<!-- 1805 start -->

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Verbesserte Problembehandlung für App-Installation <!-- 928990 -->
Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Wir versenden eine öffentliche Vorschau unserer Features zur App-Problembehandlung. Unter jedem einzelnen Gerät wird ein neuer Knoten mit der Bezeichnung **Verwaltete Apps** angezeigt. Hier sind die Apps aufgelistet, die über Intune MDM übermittelt wurden. Innerhalb des Knotens wird eine Liste mit App-Installationsstatus angezeigt. Bei Auswahl einer einzelnen App wird die Problembehandlungsansicht für diese bestimmte App angezeigt. In der Problembehandlungsansicht sehen Sie den End-to-End-Lebenszyklus der App, z. B. wann die App erstellt, geändert, festgelegt und an ein Gerät übermittelt wurde. Darüber hinaus wird bei einer nicht erfolgreichen App-Installation der Fehlercode und eine hilfreiche Nachricht zur Ursache des Fehlers angezeigt.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts <!-- 1506985 --> 

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird zukünftig die Sicherheit von MAM-fähigen Apps durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockieren des App-Zugriffs basierend auf nicht genehmigten Geräteherstellern und Modellen <!-- 1425689 ! -->
Der Intune-IT-Administrator kann über Intune-App-Schutzrichtlinien die Umsetzung einer festgelegten Liste von Android-Herstellern und/oder iOS-Modellen erzwingen. Der IT-Administrator kann eine durch Semikolon getrennte Liste von Herstellern für Android-Richtlinien und Gerätemodelle für iOS-Richtlinien bereitstellen. Intune-App-Schutzrichtlinien gelten nur für Android und iOS. Für diese festgelegten Listen können zwei verschiedene Aktionen ausgeführt werden:
- Blockieren des App-Zugriffs auf Geräten, die nicht angegeben sind.
- Selektives Zurücksetzen von Unternehmensdaten auf Geräten, die nicht angegeben sind. 

Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Anforderungen der Richtlinie nicht erfüllt sind. Anhand von Einstellungen werden Benutzer entweder blockiert oder Unternehmensdaten innerhalb der App selektiv zurückgesetzt. Bei iOS-Geräten ist für dieses Feature die Beteiligung von Anwendungen erforderlich (d. h. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK zu integrieren und so die Mindestversionseinstellungen für die Zielanwendungen zu erzwingen. Diese Integration erfolgt fortlaufend und ist von den jeweiligen Anwendungsteams abhängig. Unter Android ist für dieses Feature das neueste Unternehmensportal erforderlich. 

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen aus, die auf dem Blatt „Intune“ für Anwendungsschutzrichtlinien angegeben sind. Dies hängt ausschließlich von dem Wert ab, den das Gerät meldet. Daher sollte der IT-Administrator sicherstellen, dass das beabsichtigte Verhalten korrekt ist. Dazu kann diese Einstellung basierend auf einer Vielzahl von Geräteherstellern und Modellen für eine kleine Benutzergruppe getestet werden. Wählen Sie in Microsoft Intune nacheinander **Mobile Apps** > **App-Schutzrichtlinien** aus, um App-Schutzrichtlinien anzuzeigen und hinzuzufügen. Weitere Informationen zu App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Zugriff auf Aktionen für App-Schutzrichtlinien <!-- 1483510 EEready -->
Sie werden bald in der Lage sein, App-Schutzrichtlinien so zu konfigurieren, das nicht kompatible Geräte explizit zurückgesetzt, blockiert oder gewarnt werden. Mit der neuesten Aktion *Zurücksetzen* werden Ihre Unternehmensdaten von einem Gerät entfernt. Im Falle eines Zurücksetzens wird der Gerätebenutzer über den Grund für das Zurücksetzen und Schritte zur Wiederherstellung benachrichtigt. Für einige Einstellungen, wie z. B. die Mindestversion des Betriebssystems, können Sie mehrere Aktionen anwenden, z. B. das Blockieren und Zurücksetzen. Diese Aktionen werden ausgelöst, wenn die App gestartet wird.

<!-- 1804 start -->

### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind zukünftig verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Geräteentfernung) aus.

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