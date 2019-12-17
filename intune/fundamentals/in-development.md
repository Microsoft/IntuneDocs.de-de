---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74540741"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Dezember 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich zu den Informationen auf dieser Seite:

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office-Nachrichtencenter veröffentlichen.
- Wenn eine Funktion in die Produktionsumgebung wechselt, egal ob es sich um eine Vorschauversion handelt oder allgemein verfügbar ist, wird die Funktionsbeschreibung von dieser Seite zu den [Neuerungen](whats-new.md)verschoben.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitpläne.

> [!NOTE]
> Diese Seite spiegelt unsere aktuellen Erwartungen an die Intune-Funktionen in einer zukünftigen Version wider. Termine und einzelne Features können sich ändern. Auf dieser Seite werden nicht alle Features in der Entwicklung beschrieben.

**RSS-Feed**: Bleiben Sie auf dem Laufenden, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>App-Verwaltung

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>Benutzer lizenzierte IOS-VPP-apps<!-- 5619268 idready -->
Bei der Benutzerregistrierung für IOS-Geräte werden Endbenutzer nicht mehr mit Geräte lizenzierten VPP-Anwendungen angezeigt, die als verfügbar bereitgestellt werden. Endbenutzer sehen jedoch weiterhin alle Benutzer lizenzierten VPP-apps innerhalb der Unternehmensportal. Weitere Informationen zu VPP-Apps finden Sie unter [Verwalten von iOS- und macOS-Apps, die über das Apple Volume Purchase Program mit Microsoft Intune erworben wurden](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Abrufen des persönlichen Wiederherstellungs Schlüssels von mit macOS-verschlüsselten macOS-Geräten<!-- 4851745 idready -->
Endbenutzer können Ihren persönlichen Wiederherstellungs Schlüssel ("flevault Key") mithilfe der IOS-Unternehmensportal-App abrufen. Das Gerät, das über den persönlichen Wiederherstellungs Schlüssel verfügt, muss bei InTune registriert und über InTune mit "flevault" verschlüsselt werden. Mithilfe der IOS-Unternehmensportal-App kann ein Endbenutzer die Safari-Webansicht öffnen und Ihren persönlichen Wiederherstellungs Schlüssel abrufen. Wählen Sie in InTune die Option **Geräte** > *das verschlüsselte und registrierte macOS-Gerät* , > den **Wiederherstellungs Schlüssel zu erhalten**. Weitere Informationen zu "flevault" finden Sie unter " [flevault Encryption for macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos)".

### <a name="microsoft-app-icons-update--4677605--"></a>Microsoft App-Symbole aktualisieren<!--4677605-->
Die Symbole, die für Microsoft-apps im Bereich App-Zielsetzung für App-Schutzrichtlinien und App-Konfigurationsrichtlinien verwendet werden, werden aktualisiert.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>S/MIME-Unterstützung für Microsoft Outlook Mobile<!-- 2669398  -->
InTune unterstützt die Bereitstellung von S/MIME-Signatur-und Verschlüsselungs Zertifikaten, die mit Outlook Mobile unter IOS und Android verwendet werden können. Weitere Informationen finden Sie unter [e-Mail-Einstellungen für IOS-Geräte](~/configuration/email-settings-ios.md) und [e-Mail-Einstellungen für Android-Geräte](~/configuration/email-settings-android.md)

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Unterstützung für benutzerdefinierte Einstellungen für macOS-Anwendungen<!-- 4736278  -->
InTune unterstützt benutzerdefinierte Einstellungen, mit denen Sie einer vorhandenen Einstellungs Liste (plist-Datei) bestimmte Schlüssel und Werte hinzufügen können, um macOS-apps und das Gerät zu konfigurieren. Nicht alle apps unterstützen verwaltete Einstellungen, und in einigen Fällen können nur bestimmte Einstellungen verwaltet werden. Die Einstellungen werden nur über den Geräte Kanal bereitgestellt. Sie sollten nur Eigenschaften Listen Dateien oder XML-Dateien hochladen, die auf Geräte Kanaleinstellungen abzielen.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Anzeigen von Benachrichtigungen für die Unternehmensportal-app unter Windows<!-- 1808082  -->
Wir werden die Unternehmensportal-App auf Windows-Geräten aktualisieren, um Benutzern Popup Benachrichtigungen anzuzeigen, auch wenn die Anwendung geschlossen wird. Das Update zeigt nur dann Benachrichtigungen für verfügbare apps an, wenn der Installationsstatus "abgeschlossen" oder "Fehler" lautet. Die Unternehmensportal-APP zeigt keine Benachrichtigungen für erforderliche Anwendungen an.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Anzeigen der Installationsstatus Meldungen für die Unternehmensportal-App<!-- 2514416  -->
Die Unternehmensportal-APP zeigt den Endbenutzern zusätzliche APP-Installationsstatus Meldungen an. Die folgenden Bedingungen gelten für neue Win32-Abhängigkeits Features:
- Die App konnte nicht installiert werden. Vom Administrator definierte Abhängigkeiten wurden nicht erfüllt.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten<!-- 2576686 -->
Mit der InTune-App auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen über App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Blockieren der Konfiguration von Zertifikat Anmelde Informationen im verwalteten Keystore für Android-Gerätebesitzer Geräte durch Benutzer<!-- 3311998 idready -->
Auf Geräten mit Android-Unternehmens Geräte Besitzern gibt es eine neue Einstellung, die verhindert, dass Benutzer ihre Zertifikat Anmelde Informationen im verwalteten Keystore konfigurieren (**Geräte Konfigurations** > **profile** > **Profil** > **Android Enterprise** für die Plattform > **Gerätebesitzer) > Geräte Einschränkungen** für den Profiltyp > **Benutzer + Konten**).

Die aktuellen Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Android-Unternehmens Gerätebesitzer, einschließlich dedizierter und vollständig verwalteter Geräte

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Netzwerkgeräte-Konfigurations Profile für macOS-Geräte<!-- 3508686 idready -->
Bei macOS-Geräten enthält ein zukünftiges Update ein neues Geräte Konfigurations Profil, das verdrahtete Netzwerke konfiguriert (**Geräte Konfigurations** > **profile** > **Profil** > **macOS** für Plattform > **Kabelnetzwerk** für Profiltyp erstellen). Verwenden Sie dieses Feature zum Erstellen von 802.1 x-Profilen zum Verwalten von verkabelten Netzwerken und zum Bereitstellen dieser Kabel Netzwerke auf Ihren macOS-Geräten.

Gilt für:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Hinzufügen automatischer Proxy Einstellungen zu WLAN-Profilen für Android Enterprise-Arbeitsprofile<!-- 4490822 idready -->
Auf Geräten mit Android-Unternehmens Arbeits Profilen können Sie WLAN-Profile erstellen. Wenn Sie den Typ "Wi-Fi Enterprise" auswählen, können Sie auch den EAP-Typ (Extensible Authentication Protocol), der in Ihrem WLAN-Netzwerk verwendet wird, eingeben.

Wenn Sie in einem zukünftigen Update den Enterprise-Typ auswählen, können Sie die automatischen Proxy Einstellungen, einschließlich einer Proxy Server-URL, wie z. b. `proxy.contoso.com`, eingeben.

Die aktuellen WLAN-Einstellungen, die Sie konfigurieren können, finden Sie unter [Hinzufügen von WLAN-Einstellungen für Geräte mit Android Enterprise und Android Kiosk in Microsoft InTune](../configuration/wi-fi-settings-android-enterprise.md).

Gilt für:
- Android Enterprise-Arbeitsprofil

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>Aktivieren der Netzwerk Zugriffs Steuerung (NAC) mit dem Cisco AnyConnect-VPN auf IOS-Geräten<!-- 4860111 idready -->
Auf IOS-Geräten können Sie ein VPN-Profil erstellen und unterschiedliche Verbindungstypen verwenden, einschließlich Cisco AnyConnect (**Geräte Konfigurations** > **profile** > **Profil** > **IOS** für Platform > **VPN** für den Profiltyp > **Cisco AnyConnect** für Verbindungstyp). 

In einem zukünftigen Update können Sie die Netzwerk Zugriffs Steuerung (NAC) mit Cisco AnyConnect aktivieren. Zur Nutzung dieses Features ist Folgendes erforderlich:

1. Befolgen Sie die [Schritte unter](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html) **Konfigurieren von Microsoft InTune als MDM-Server** , um die Cisco Identity Services Engine (ISE) in Azure zu konfigurieren.
2. Wählen Sie im InTune-Geräte Konfigurations Profil die Einstellung **Netzwerk Access Control aktivieren (NAC)** aus.

Weitere Informationen zu den verfügbaren VPN-Einstellungen finden Sie unter [Konfigurieren von VPN-Einstellungen auf IOS-Geräten](../configuration/vpn-settings-ios.md).

Gilt für:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Aktualisierte Single Sign-on für apps und Websites auf Ios-, ipados-und macOS-Geräten<!-- 4999578 idready -->
InTune fügt weitere Single Sign-on Einstellungen für IOS-, ipados-und macOS-Geräte hinzu. Derzeit können Sie SSO-App-Erweiterungen für Anmelde Informationen und die integrierte Kerberos-Erweiterung von Apple in InTune konfigurieren. In einem zukünftigen Update können Sie Umleitungs-SSO-App-Erweiterungen konfigurieren, die von Ihrer Organisation oder von Ihrem Identitäts Anbieter geschrieben wurden. 

Verwenden Sie diese Einstellungen, um eine nahtlose Single Sign-on Umgebung für apps und Websites zu konfigurieren, die moderne Authentifizierungsmethoden verwenden, z. b. OAuth und saml2. 

Wenn Sie die SSO-App-Erweiterungs Einstellungen anzeigen möchten, die Sie konfigurieren können, wechseln Sie zu [SSO unter IOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) und [SSO unter macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Gilt für:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Verwendung genehmigter Tastaturen auf Android erforderlich<!--4761794 IDready -->
Sie können eine Liste der genehmigten Tastaturen für die Verwendung in verwalteten Android-Apps angeben. In der verwalteten APP wird der Benutzer aufgefordert, zu einem der genehmigten Tastaturen zu wechseln, die bereits auf dem Gerät installiert sind, oder Sie werden ggf. an den Google Play Store umgeleitet, um eines der genehmigten Tastaturen herunterzuladen und einzurichten. Der Benutzer kann nur Textfelder in einer verwalteten App bearbeiten, wenn die aktive Tastatur eine der genehmigten Tastaturen ist.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Verwenden von PKCS-Zertifikaten mit WLAN-Profilen auf Geräten mit Windows 10 und höher<!-- 3246388  -->
Derzeit können Sie Windows-WLAN-Profile mit SCEP-Zertifikaten (**Gerätekonfiguration** > **profile** > **Profil erstellen** > **Windows 10 und** höher für die Plattform > **Wi-Fi** für den Profiltyp > **Enterprise** > **EAP-Typ**) authentifizieren. Sie können PKCS-Zertifikate mit Ihren Windows Wi-Fi-Profilen verwenden. Diese Funktion ermöglicht Benutzern das Authentifizieren von WLAN-Profilen mithilfe neuer oder vorhandener PKCS-Zertifikat Profile in Ihrem Mandanten. 

Weitere Informationen zu WLAN-Profilen finden [Sie unter Hinzufügen von WLAN-Einstellungen für Windows 10-und spätere Geräte in InTune](../configuration/wi-fi-settings-windows.md).

Gilt für:
- Windows 10 und höher

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Neue ExchangeActiveSync-Einstellungen beim Erstellen eines E-Mail-Gerätekonfigurationsprofils auf iOS-Geräten<!-- 4892824  --> 
Sie können auf iOS- und iPadOS-Geräten die E-Mail-Konnektivität in einem Gerätekonfigurationsprofil konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS** für Plattform > **E-Mail** für den Profiltyp). 

Es sind neue ExchangeActiveSync-Einstellungen verfügbar, einschließlich:
- Wählen Sie die zu synchronisierenden Dienste (oder die Synchronisierung blockieren) aus, z. b. e-Mail, Kalender und Kontakte.
- Erlauben Sie Benutzern, die Synchronisierungseinstellungen für diese Dienste auf ihren Geräten zu ändern (oder blockieren Sie sie). 

Informationen zu den aktuellen Einstellungen finden Sie unter [e-Mail-Profileinstellungen für IOS-Geräte in InTune](../configuration/email-settings-ios.md).

Gilt für:
- iOS 13.0 und neuer
- iOS 13.0 und höher

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Verhindern, dass Benutzer Android Enterprise-Gerätebesitzern und dedizierten Geräten persönliche Google-Konten hinzufügen<!-- 5353228  -->
Sie werden Benutzer daran hindern können, persönliche Google-Konten für Android Enterprise-Gerätebesitzer und auf dedizierten Geräten zu erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Nur Gerätebesitzer > Geräteeinschränkungen** für Profiltyp > **Benutzer- und Konteneinstellungen**).

Sie finden die aktuellen konfigurierbaren Einstellungen unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Android Enterprise-Gerätebesitzer
- Dedizierte Android Enterprise-Geräte

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>Entfernung der serverseitigen Protokollierung für die Einstellung der Siri-Befehle im iOS-Profil zur Geräteeinschränkung<!-- 5468501  -->
Auf IOS-Geräten können Sie ein Geräte Einschränkungs Profil erstellen, das die serverseitige Protokollierung für Siri-Befehle konfiguriert (**Geräte Konfigurations** > **profile** > **Erstellen eines Profils** > **IOS/ipados** für Platt Form > **Geräte Einschränkungen** für den Profiltyp > **integrierte apps**). Die Einstellung **Server seitige Protokollierung für Siri-Befehle** wird entfernt.

Diese Einstellung wird aus der InTune-Verwaltungskonsole entfernt. Diese Einstellung hat keine Auswirkung auf das Gerät, auch wenn vorhandene Richtlinien, bei denen diese Einstellung konfiguriert ist, die Einstellung weiterhin anzeigen. Wenn Sie die Einstellung aus vorhandenen Richtlinien entfernen möchten, klicken Sie auf die Richtlinie, nehmen Sie eine kleine Bearbeitung vor, speichern Sie Sie, und die Richtlinie wird aktualisiert.

Sie finden die konfigurierbaren Einstellungen unter [iOS- und iPadOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Überwachung und Problembehandlung

### <a name="centralized-audit-logs--5603185-5697164--"></a>Zentrale Überwachungs Protokolle<!--5603185, 5697164-->
Bei einer neuen zentralisierten Überwachungs Protokoll-Überprüfung werden Überwachungs Protokolle für alle Kategorien in eine Seite erfasst. Sie können die Protokolle filtern, um die gesuchten Daten zu erhalten. Um die Überwachungs Protokolle anzuzeigen, wechseln Sie zu Mandanten **Verwaltung** > Überwachungs **Protokolle**. Weitere Informationen finden Sie unter [Bevorstehende Änderungen an Überwachungsprotokollen in InTune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>Sicherheit

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Verwenden von PKCS-Zertifikat Profilen zum Bereitstellen von Geräten mit Zertifikaten<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
Sie können ein PKCS-Zertifikat Profil verwenden, um Zertifikate für Geräte auszustellen, um die aktuelle Unterstützung von benutzerbasierten Zertifikaten zu erhöhen. Geräte basierte Zertifikate werden auf Android-, IOS-und Windows-Plattformen unterstützt und können für WLAN-und VPN-Profile verwendet werden.

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuerungen in Microsoft Intune](whats-new.md).


