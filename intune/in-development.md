---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c2b9429bf5b50ac5e416c4a7b356627e9cc9fb1
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560104"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: August 2019

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich:

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office-Nachrichtencenter veröffentlichen.
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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit InTune-App-Schutzrichtlinien (app) auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile <!-- 3041956  -->
Mit diesem Feature können Sie den App-Installationsstatus und die installierte Version verwalteter Google Play-Apps für verfügbare App-Installationen auf Android Arbeitsprofilgeräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Unterstützung für IKEv2-VPN-Profile für iOS <!-- 1943438 -->
Sie können VPN-Profile für den nativen VPN-Client für iOS mithilfe des IKEv2-Protokolls erstellen. IKEv2 ist ein neuer Verbindungstyp unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **VPN** (Profiltyp) > **Einstellungen**.

Mit diesen VPN-Profilen wird der native VPN-Client konfiguriert. Es werden keine VPN-Client-Apps installiert oder an verwaltete Geräte gepusht. Für dieses Feature müssen Geräte in Intune registriert sein (MDM-Registrierung).

Die derzeit konfigurierbaren VPN-Einstellungen finden Sie unter [Configure VPN settings on iOS devices in Microsoft Intune (Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune)](vpn-settings-ios.md).

Gilt für: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Geräteregistrierung

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Passen Sie für IOS-Geräte den Datenschutz Bildschirm des Anmeldungsprozesses des Unternehmensportal <!-- 4394993  -->
Mithilfe von markdown können Sie den Datenschutz Bildschirm des Unternehmensportal anpassen, den Endbenutzern während der IOS-Registrierung angezeigt werden. Insbesondere können Sie die Liste der Dinge anpassen, die Ihre Organisation nicht auf dem Gerät sehen oder ausführen kann.

<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="import-and-export-security-baselines------3408610------------"></a>Importieren und Exportieren von Sicherheitsbaselines    <!--3408610          -->  
Wir fügen die Funktion zum Exportieren und Importieren von Sicherheitsbaselines hinzu. Mit diesem Feature können Sie Ihre Anpassungen mit Ihnen durchführen und Sie in InTune-Umgebungen freigeben.

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).




