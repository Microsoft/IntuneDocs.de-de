---
title: Verwalten von Android Enterprise-Arbeitsprofilgeräten in Microsoft Intune
titleSuffix: ''
description: Microsoft Intune verwaltet Android Enterprise-Arbeitsprofilgeräte, um zusätzliche Verwaltungsfunktionen und zusätzlichen Datenschutz zu bieten, wenn Benutzer ihre privaten Android-Geräte für die Arbeit verwenden.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2cc3c960-1fdd-47ca-a693-420d47b403de
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a5c980b3f9ababaf94aa7b279e533679ed74b0e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503363"
---
# <a name="manage-android-work-profile-devices-with-intune"></a>Verwalten von Android-Arbeitsprofilgeräten mit Intune

Android Enterprise bietet mehrere Registrierungsoptionen, die Benutzer mit den aktuellsten und sichersten Features versorgen. Mit einer Registrierung für ein Android Enterprise-Arbeitsprofil stehen eine Reihe von Features und Diensten bereit, die Ihre privaten Apps und Daten von Ihren Geschäfts-Apps und -daten trennen. Außerdem stehen zusätzliche Verwaltungsfunktionen und zusätzlicher Datenschutz zur Verfügung, wenn Benutzer ihre privaten Android-Geräte für die Arbeit verwenden. 

## <a name="supported-devices"></a>Unterstützte Geräte

Die Verwaltungsfunktionen von Android Enterprise sind abhängig von Features, die Teil der aktuelleren Android-Betriebssysteme sind. Für Geräte, die Android Enterprise nicht unterstützen, bleibt die konventionelle Android-Verwaltung verfügbar. Weitere Informationen finden Sie im Artikel zu den [Android Enterprise-Anforderungen](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

## <a name="onboarding"></a>Onboarding

Vor dem Registrieren von Android-Arbeitsprofilgeräten müssen Sie einige Onboardingschritte abschließen. Durch diese Schritte wird eine Verbindung zwischen Ihrem Intune-Mandanten und Managed Google Play hergestellt. Weitere Informationen finden Sie unter [Enable enrollment of Android work profile devices (Aktivieren der Registrierung für Android-Arbeitsprofilgeräte)](android-work-profile-enroll.md).

## <a name="work-profile-management"></a>Arbeitsprofilverwaltung

Wenn Sie ein Android Enterprise-Arbeitsprofilgerät mit Intune verwalten, verwalten Sie nicht das gesamte Gerät. Das Verwalten von Funktionen wirkt sich nur auf das Arbeitsprofil aus, das während der Registrierung auf dem Gerät erstellt wurde. Alle Apps, die dem Gerät mit Intune bereitgestellt werden, werden auf dem Arbeitsprofil installiert. App-Symbole im Arbeitsprofil unterscheiden sich von den Symbolen privater Apps auf dem Gerät. Alle Android-Apps und Daten außerhalb des Android Enterprise-Bereichs des Geräts bleiben privat und unter der Kontrolle des Endbenutzers. Benutzer können im privaten Bereich alle Apps installieren, die sie installieren möchten. Administratoren können Apps und Aktionen im Arbeitsprofil verwalten und überwachen.

Intune bietet eine Vielzahl integrierter allgemeiner Einstellungen, die Sie auf Android-Arbeitsprofilgeräten konfigurieren können. Weitere Informationen finden Sie unter [Hinzufügen einer Gerätekonformitätsrichtlinie für Android for Work-Geräte in Intune](../protect/compliance-policy-create-android-for-work.md).

## <a name="app-publishing-and-distribution"></a>Veröffentlichung und Verteilung von Apps

Managed Google Play ist integraler Bestandteil der App-Verteilung und -Verwaltung von Android Enterprise. Alle für Android Enterprise-Arbeitsprofilgeräte im Arbeitsprofil bereitgestellten Apps stammen vom Managed Google Play-Dienst. Zum Verwalten und Bereitstellen von Apps im Play Store melden Sie sich auf der Google Play-Website mit den Administratoranmeldeinformationen für die Google-Verwaltung Ihres Unternehmens an. Sie können Apps für die Android Enterprise-Bereitstellung genehmigen, damit sie in den Arbeitsprofilen der Geräte angezeigt werden. Diese Apps werden dann mit der Intune-Konsole synchronisiert, wo sie mithilfe von Intune verwaltet und bereitgestellt werden können. Von Ihrer Organisation entwickelte branchenspezifische Apps (Line of Business, LOB) müssen mithilfe der Veröffentlichungskonsole für Android-Apps von Google für Managed Google Play veröffentlicht werden. Branchenspezifische Apps müssen in der Veröffentlichungskonsole für Android-Apps für den Zugriff auf Ihre Organisation konfiguriert werden.

Die Installation von Apps kann ohne Eingreifen des Benutzers, und ohne dass der Benutzer **Installation aus unbekannten Quellen** zulassen muss, erfolgen. Zum Suchen nach und Installieren optionaler oder verfügbarer Apps können die Benutzer den Play for Work Store auf ihren Geräten durchsuchen. Weitere Informationen finden Sie unter [Zuweisen von Apps zu Android Enterprise-Arbeitsprofilgeräten mit Intune](../apps/apps-add-android-for-work.md).

## <a name="app-configuration"></a>App-Konfiguration

Android Enterprise bietet die Infrastruktur für die Bereitstellung von App-Konfigurationswerten für Apps, die diese unterstützen. Durch Angabe von Konfigurationswerten für Arbeits-Apps stellen Sie sicher, dass sie ordnungsgemäß eingerichtet sind, wenn der Benutzer die App zum ersten Mal starten. Unterstützung für App-Konfiguration erfordert, dass App-Entwickler ihre Android-Apps speziell für verwaltete Konfigurationswerte erstellen. Wenn dies der Fall, können Sie diese Konfigurationseinstellungen mit Intune angeben und anwenden. Weitere Informationen finden Sie unter [Add app configuration policies for managed Android devices (Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte)](../apps/app-configuration-policies-use-android.md).

## <a name="email-configuration"></a>E-Mail-Konfiguration

Android Enterprise stellt keine Standard-E-Mail-App bzw. kein natives E-Mail-Profil-Objekt bereit, wie es bei iOS der Fall ist. E-Mail-Konfigurationen können stattdessen durch Anwenden von App-Konfigurationseinstellungen auf E-Mail-Apps eingestellt werden, die diese unterstützen. Gmail und Nine Work sind zwei Exchange ActiveSync-Client-Apps (EAS) im Play Store, die die Konfiguration mit der Android Enterprise-App-Konfiguration unterstützen.

Intune bietet Konfigurationsvorlagen für Gmail- und Nine Work-Apps, wenn diese als Work-Apps verwaltet werden. Andere E-Mail-Apps, die App-Konfigurationsprofile unterstützen, können mit Konfigurationsrichtlinien für mobile Apps konfiguriert werden.

Wenn Sie bedingten Exchange ActiveSync-Zugriff für Geräte mit Android Enterprise-Arbeitsprofil verwenden, sollten Sie entweder die Gmail- oder die Nine Work-E-Mail-App in Erwägung ziehen. Die Microsoft Outlook for Android-App oder jede andere E-Mail-App, die moderne Authentifizierung über ADAL verwendet, wird ebenfalls unterstützt. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Einstellungen in Microsoft Intune](../configuration/email-settings-configure.md).

## <a name="app-protection-policies"></a>App-Schutzrichtlinien

Angewendete App-Schutzrichtlinien werden im Arbeitsprofil und im persönlichen Profil vollständig unterstützt. Unter https://play.google.com/apps/publish können Sie branchenspezifische Apps in der Veröffentlichungskonsole für Android-Apps veröffentlichen. Diese Konsole enthält eine Option, mit der Sie Apps für Ihr Unternehmen als privat kennzeichnen können. Weitere Informationen finden Sie unter [Add a device compliance policy for Android Enterprise work profile devices in Intune (Hinzufügen einer Gerätekonformitätsrichtlinie für Android Enterprise-Arbeitsprofilgeräte in Intune)](../protect/compliance-policy-create-android-for-work.md). Allgemeine Informationen zu App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)

## <a name="vpn-profiles"></a>VPN-Profile

VPN-Unterstützung entspricht Android VPN-Profilen. Für die Android Enterprise-Verwaltung sind prinzipiell die gleichen VPN-Anbieter und grundlegenden Konfigurationsoptionen verfügbar. Es gibt die folgenden zwei Unterschiede:

- **Arbeitsprofilbezogenes VPN**: VPN-Verbindungen sind auf die Apps beschränkt, die für das Arbeitsprofil bereitgestellt werden. Nur von Android Enterprise verwaltete Apps können die VPN-Verbindung verwenden. Persönliche Apps auf dem Gerät können eine verwaltete VPN-Verbindung nicht verwenden. Weitere Informationen finden Sie im Artikel zu den [Android Enterprise-VPN-Einstellungen](../configuration/vpn-settings-android-enterprise.md).

- **App-spezifisches VPN:** Sie können ein App-spezifisches VPN in Intune konfigurieren, wenn der VPN-Anbieter Folgendes unterstützt:
  - die Konfiguration für App-spezifische VPN
  - die Möglichkeit, ein App-bezogenes VPN über das Android Enterprise-App-Konfigurationsprofil zu konfigurieren
  Weitere Informationen finden Sie unter [Verwenden eines benutzerdefinierten Microsoft Intune-Profils zum Erstellen eines VPN-Profils pro App für Android-Geräte](../configuration/android-pulse-secure-per-app-vpn.md).

## <a name="certificate-profiles"></a>Zertifikatprofile

Die gleichen Zertifikatprofil-Konfigurationsoptionen, die für die Android-Verwaltung zur Verfügung stehen, sind auf Android Enterprise-Arbeitsprofilgeräten verfügbar. Android Enterprise bietet verbesserte Zertifikatverwaltungs-APIs. Verbesserte Zertifikatsverwaltung bietet die folgenden Funktionen:

- Gewährleistung, dass die Zertifikatbereitstellung im Hintergrund und nahtlos für den Benutzer erfolgt.
- Gewährleistung, dass die bereitgestellten Zertifikate entfernt werden, wenn ein Gerät von Intune zurückgezogen und das Arbeitsprofil entfernt wird.
- Bietet verbesserte Nachrichten, die Benutzer darüber informieren, dass das Zertifikat bereitgestellt und von ihrer IT-Abteilung über ihren Verwaltungsdienst konfiguriert wurde.

Weitere Informationen finden Sie unter [Konfigurieren eines Zertifikatprofils für Ihre Geräte in Microsoft Intune](../protect/certificates-configure.md).

## <a name="wi-fi-profiles"></a>WLAN-Profile

Von Android Enterprise verwaltete WLAN-Profile werden entfernt, wenn das Gerät von Intune zurückgezogen und das Arbeitsprofil gelöscht wird. Weitere Informationen finden Sie unter [So konfigurieren Sie WLAN-Einstellungen in Microsoft Intune](../configuration/wi-fi-settings-configure.md).

## <a name="next-steps"></a>Nächste Schritte
- [Registrieren von Android-Geräten](android-enroll.md)
- [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](../apps/apps-add-android-for-work.md)
