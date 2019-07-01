---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 633bf52084ad261f768cb4e59aaf4ce0ab5cd5bc
ms.sourcegitcommit: 46f4d3d160e18aeab9de7477eedc8351fbb78c85
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2019
ms.locfileid: "67468726"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Juli 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich:

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office 365-Nachrichtencenter veröffentlichen.
- Wenn ein Feature in die Produktion überführt wird, entweder als Vorschau- oder allgemein verfügbare Version, wird die Featurebeschreibung von dieser Seite auf die Seite [Neuerungen in Microsoft Intune](whats-new.md) verschoben.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitrahmen.

> [!Note]
> Diese Punkte spiegeln die aktuellen Erwartungen von Microsoft an die Möglichkeiten mit Intune in einer künftigen Version wider. Termine und einzelne Features können sich ändern. Nicht für alle Elemente in der Entwicklung gibt es auf dieser Seite eine Featurebeschreibung.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>App-Verwaltung

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gerätebenutzer können alle verwalteten Anwendungen anzeigen, die sie installiert bzw. zu installieren versucht haben <!-- 2352913 -->
Im Unternehmensportal für Windows werden alle verwalteten (sowohl erforderlichen als auch verfügbaren) Apps aufgelistet, die auf dem Gerät eines Benutzers installiert sind. Benutzer können versuchte und ausstehende App-Installationen sowie deren aktuellen Status einsehen. Wenn Ihr Unternehmen keine erforderlichen oder verfügbaren Anwendungen zur Verfügung stellt, erhalten die Benutzer die Meldung, dass keine Unternehmensanwendungen installiert wurden. Benutzer können ihre Apps auch nach Installationsstatus sortieren oder filtern.

### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Benutzerdefinierte Benachrichtigungen für Benutzer und Gruppen    <!-- 16766574   -->
Sie werden bald zum Senden von benutzerdefinierten Ad-hoc-Push-Benachrichtigungen aus der Unternehmensportal-Anwendung für Benutzer von IOS- und Android-Geräte, die Sie mit Intune verwalten können. Diese benutzerdefinierte Benachrichtigungen sind auf bestimmte Intune-Features nicht gebunden und kann verwendet werden, für einen bestimmten Zweck, die Sie benötigen, einschließlich der allgemeinen Benachrichtigungen, die Sie für einige senden möchten oder alle Ihre Mitarbeiter.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren der Inhalt der app-Benachrichtigung für Organisationskonten <!-- 2576686 -->
Intune app-Schutzrichtlinien (APP) auf Android- und iOS-Geräten können zu Steuerelementinhalt für app-Benachrichtigung für Organisations-Konten Sie. Dieses Feature erfordert die Unterstützung von Anwendungen und möglicherweise nicht verfügbar für alle Anwendungen der APP aktiviert. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile <!-- 3041956  -->
Mit diesem Feature können Sie den App-Installationsstatus und die installierte Version verwalteter Google Play-Apps auf Android Enterprise-Geräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Unterstützung für IKEv2-VPN-Profile für iOS <!-- 1943438 -->
Sie können VPN-Profile für den nativen VPN-Client für iOS mithilfe des IKEv2-Protokolls erstellen. IKEv2 ist ein neuer Verbindungstyp unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **VPN** (Profiltyp) > **Einstellungen**.

Mit diesen VPN-Profilen wird der native VPN-Client konfiguriert. Es werden keine VPN-Client-Apps installiert oder an verwaltete Geräte gepusht. Für dieses Feature müssen Geräte in Intune registriert sein (MDM-Registrierung).

Die derzeit konfigurierbaren VPN-Einstellungen finden Sie unter [Configure VPN settings on iOS devices in Microsoft Intune (Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune)](vpn-settings-ios.md).

Gilt für: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Verwenden von „Anwendbarkeitsregeln“ beim Erstellen von Windows 10-Gerätekonfigurationsprofilen <!-- 2549910 -->
Sie können Windows 10-Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** als Plattform). Sie können eine **Anwendbarkeitsregel** so erstellen, dass das Profil nur für eine bestimmte Edition oder Version gilt. Sie können beispielsweise ein Profil erstellen, das einige BitLocker-Einstellungen aktiviert. Sobald Sie das Profil hinzugefügt haben, aktivieren Sie eine Anwendbarkeitsregel, damit das Profil nur für Geräte mit Windows 10 Enterprise gilt.

Gilt für: 
- Windows 10 und höher

### <a name="administrative-templates-for-group-policy---------3510695---"></a>Administrative Vorlagen für Gruppenrichtlinien     <!--  3510695 -->
Es werden administrative Vorlagen veröffentlicht, mit denen Sie Intune zum Konfigurieren ausgewählter Gruppenrichtlinieneinstellungen für Windows-Computer verwenden können, um die Sicherheit von Geräten in der Cloud zu verbessern.  Diese Vorlagen nutzen den Richtlinien-CSP (Konfigurationsdienstanbieter), um bis zu 2500 zusätzliche Einstellungen von Office, Windows und OneDrive bereitzustellen.

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>Verwalten Sie FileVault für macOS   <!--  3858502 + 1210104   -->
Sie müssen ein gerätekonfigurationsprofil für Intune Endpoint Protection zu verwenden, um die Verschlüsselung mit Schlüsseln FileVault für MacOS-Geräte verwalten können. Dies schließt hinterlegter von der Anzeige und Rotation der Verschlüsselungsschlüssel, der Ihren unternehmensgeräten. Benutzer werden in der Lage, diese Schlüssel über die Unternehmensportal-Website abzurufen.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Erweiterte Einstellungen für Windows Defender-Firewall   <!--  1311949     -->
Dies ist eine öffentliche Vorschauversion, und Sie können in Kürze Intune verwenden, um die benutzerdefinierten Firewallregeln auf Clients für Windows Defender zu verwalten.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Neues Konfigurations-Designer beim Erstellen einer OEMConfig-Profils für Android Enterprise <!-- 3712769  -->
In Intune können Sie erstellen ein gerätekonfigurationsprofil, die eine app OEMConfig verwendet (Gerätekonfiguration > Profile > Profil erstellen > Android Enterprise für die Plattform > OEMConfig für Profiltyp). Wenn Sie dies tun, wird ein JSON-Editor geöffnet, mit einer Vorlage und die Werte für die Sie ändern. Dieses Update enthält eine Konfigurations-Designer mit der eine verbesserte Benutzeroberfläche, die eingebettet werden, in der app, einschließlich Titel, Beschreibungen und weitere Details angezeigt. Im JSON-Editor ist weiterhin verfügbar, und zeigt alle Änderungen, dass Sie den Konfigurations-Designer durchführen.

Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [verwenden und Verwalten von Android Enterprise-Geräte mit OEMConfig](android-oem-configuration-overview.md).

Gilt für: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung

### <a name="improve-device-location---3855417---"></a>Gerätestandort verbessern<!-- 3855417 -->
Sie werden die genauen Koordinaten eines Geräts mit Vergrößern der **Gerät suchen** Aktion. Weitere Informationen zum Suchen von verlorenen iOS-Geräten finden Sie unter [Auffinden von verlorenen iOS-Geräten](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurieren der automatischen geräteverwaltung Cleanup-Zeitlimit auf 30 Tage <!--4231059  -->
Sie werden können das automatische Device Cleanup Zeitlimit so kurz wie 30 Tage (anstatt die aktuelle Grenze von 90 Tagen) nach der letzten Anmeldung festgelegt. Wechseln Sie zu diesem Zweck auf **Intune** > **Geräte** > **Setup** > **bereinigen Sie Geräteregeln**.


<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="import-and-export-security-baselines------3408610------------"></a>-Import/export-Sicherheitsbaselines    <!--3408610          -->  
Fügen wir die Funktion zum Exportieren und importieren Sicherheitsbaselines, damit Sie Ihre Anpassungen mit Ihnen nutzen und zwischen Intune-Umgebungen freigeben können.



<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


