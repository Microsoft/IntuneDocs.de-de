---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ee62213c9ef23302de7fa7342569e1903514699
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341348"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Juli 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Beachten Sie auch Folgendes:

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


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Angepasste Benachrichtigungen für Benutzer und Gruppen    <!-- 16766574   -->
In Kürze können Sie benutzerdefinierte Ad-hoc-Pushbenachrichtigungen aus der Unternehmensportal Anwendung an Benutzer auf IOS-und Android-Geräten senden, die Sie mit InTune verwalten. Diese benutzerdefinierten Benachrichtigungen sind nicht an bestimmte InTune-Features gebunden und können für beliebige Zwecke verwendet werden, einschließlich allgemeiner Benachrichtigungen, die an einige oder alle Mitarbeiter gesendet werden sollen.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit InTune-App-Schutzrichtlinien (app) auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

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

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Erweiterte Einstellungen für Windows Defender-Firewall   <!--  1311949     -->
Dies ist eine öffentliche Vorschauversion, und Sie können in Kürze Intune verwenden, um die benutzerdefinierten Firewallregeln auf Clients für Windows Defender zu verwalten.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Neuer Konfigurations-Designer beim Erstellen eines oemconfig-Profils für Android Enterprise <!-- 3712769  -->
In InTune können Sie ein Geräte Konfigurations Profil erstellen, das eine oemconfig-App verwendet (Gerätekonfiguration > Profile > Profil > Android Enterprise for Platform > oemconfig als Profiltyp). Wenn Sie dies tun, öffnet sich ein JSON-Editor mit einer Vorlage und Werten, die Sie ändern können. Dieses Update umfasst einen Konfigurations-Designer mit verbesserter Benutzer Darstellung, der in der APP eingebettete Details anzeigt, einschließlich Titeln, Beschreibungen und mehr. Der JSON-Editor ist weiterhin verfügbar und zeigt alle Änderungen an, die Sie im Konfigurations-Designer vornehmen.

Informationen zu den aktuellen Einstellungen finden Sie unter [verwenden und Verwalten von Android-Unternehmens Geräten mit oemconfig](android-oem-configuration-overview.md).

Gilt für: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung

### <a name="improve-device-location---3855417---"></a>Geräte Standort verbessern<!-- 3855417 -->
Mithilfe der Aktion **Gerät suchen** können Sie die exakten Koordinaten eines Geräts vergrößern. Weitere Informationen zum Auffinden verlorener IOS-Geräte [finden Sie untersuchen verlorener IOS-Geräte](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurieren der automatischen Geräte Bereinigung auf bis zu 30 Tage <!--4231059  -->
Nach der letzten Anmeldung können Sie den Grenzwert für die automatische Bereinigung von Geräten auf 30 Tage festlegen (anstelle des aktuellen Limits von 90 Tagen). Wechseln Sie hierzu zu **InTune** > -**Geräte** > **Einrichten** > **Geräte Bereinigungs Regeln**.


<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="import-and-export-security-baselines------3408610------------"></a>Importieren und Exportieren von Sicherheitsbaselines    <!--3408610          -->  
Wir fügen die Funktion zum Exportieren und Importieren von Sicherheitsbaselines hinzu, damit Sie Ihre Anpassungen mit Ihnen durchführen und Sie in InTune-Umgebungen freigeben können.



<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


