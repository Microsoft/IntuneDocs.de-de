---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc5ea7076e77e5071724168fab58fa78f59601c4
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744300"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: Juni 2019

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
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- ***********************************************-->
### <a name="app-management"></a>App-Verwaltung

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gerätebenutzer können alle verwalteten Anwendungen anzeigen, die sie installiert bzw. zu installieren versucht haben <!-- 2352913 -->
Im Unternehmensportal für Windows werden alle verwalteten (sowohl erforderlichen als auch verfügbaren) Apps aufgelistet, die auf dem Gerät eines Benutzers installiert sind. Benutzer können versuchte und ausstehende App-Installationen sowie deren aktuellen Status einsehen. Wenn Ihr Unternehmen keine erforderlichen oder verfügbaren Anwendungen zur Verfügung stellt, erhalten die Benutzer die Meldung, dass keine Unternehmensanwendungen installiert wurden. Benutzer können ihre Apps auch nach Installationsstatus sortieren oder filtern.

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956---"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile <!-- 3041956 -->
Mit diesem Feature können Sie den App-Installationsstatus und die installierte Version verwalteter Google Play-Apps auf Android Enterprise-Geräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](apps-add-android-for-work.md#managed-google-play-app-type).

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Konfigurieren, welche Browser zu Unternehmensdaten verlinken dürfen <!-- 3145939 -->
Intune-App-Schutzrichtlinien für Android- und iOS-Geräte ermöglichen Ihnen die Übertragung von Unternehmensweblinks an einen spezifischen anderen Browser als Intune Managed Browser oder Microsoft Edge.  Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>Seite „Installierte Apps“ auf der Unternehmensportalwebsite  <!-- 4224326 -->
Die [Unternehmensportalwebsite](https://portal.manage.microsoft.com/) wird eine neue Seite umfassen, auf denen Benutzern alle Apps angezeigt werden, die auf ihren Geräten installiert sind. Diese Liste enthält sowohl die verfügbaren Apps als auch die vom Unternehmen vorgegebenen Apps. Auf dieser Seite können Benutzer den Installations- und Anforderungsstatus der Apps auf ihren Geräten sehen. Weitere Informationen über die Unternehmensportalwebsite finden Sie unter [Using the Intune Company Portal website (Verwenden der Intune-Unternehmensportalwebsite)](/intune-user-help/using-the-intune-company-portal-website.md) und [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>Aufrufen von Lesevorgängen der Graph-API über eine Anwendung ohne Benutzeranmeldeinformationen <!-- 4655885 -->
Anwendungen können Lesevorgänge der Intune-Graph-API mithilfe der App-Identität ohne Benutzeranmeldeinformationen aufrufen. Weitere Informationen finden Sie unter [Get access without a user (Zugriff ohne Benutzer)](https://docs.microsoft.com/graph/auth-v2-service).

<!-- ***********************************************-->
### <a name="device-configuration"></a>Gerätekonfiguration


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Unterstützung für IKEv2-VPN-Profile für iOS <!-- 1943438 -->
Sie können VPN-Profile für den nativen VPN-Client für iOS mithilfe des IKEv2-Protokolls erstellen. IKEv2 ist ein neuer Verbindungstyp unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **VPN** (Profiltyp) > **Einstellungen**.

Mit diesen VPN-Profilen wird der native VPN-Client konfiguriert. Es werden keine VPN-Client-Apps installiert oder an verwaltete Geräte gepusht. Für dieses Feature müssen Geräte in Intune registriert sein (MDM-Registrierung).

Die derzeit konfigurierbaren VPN-Einstellungen finden Sie unter [Configure VPN settings on iOS devices in Microsoft Intune (Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune)](vpn-settings-ios.md).

Gilt für: iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>Konfigurieren von Einstellungen für Kernelerweiterungen auf macOS-Geräten <!-- 20430240 -->
Sie können auf macOS-Geräten ein Gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** (Plattform)). Mit einem zukünftigen Update werden weitere Einstellungen hinzugefügt, die Sie zum Konfigurieren und Verwenden von Kernelerweiterungen auf Ihren Geräten verwenden können.

Gilt für: macOS 10.13.2 und höher

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Baseline-Unterstützung für Stichwortsuche  <!-- 3082036         -->
Wenn Sie ein Baselineprofil für Sicherheit erstellen oder bearbeiten, können Sie bald mithilfe der *Suche* die Einstellungen filtern, die in der Konsole angezeigt werden.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Verwenden von „Anwendbarkeitsregeln“ beim Erstellen von Windows 10-Gerätekonfigurationsprofilen <!-- 2549910 -->
Sie können Windows 10-Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** als Plattform). Sie können eine **Anwendbarkeitsregel** so erstellen, dass das Profil nur für eine bestimmte Edition oder Version gilt. Sie können beispielsweise ein Profil erstellen, das einige BitLocker-Einstellungen aktiviert. Sobald Sie das Profil hinzugefügt haben, aktivieren Sie eine Anwendbarkeitsregel, damit das Profil nur für Geräte mit Windows 10 Enterprise gilt.

Gilt für: 
- Windows 10 und höher

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>Weitere Konfigurationsoptionen für die Einstellung „Apps from the store only“ (Nur Apps aus dem Store) für Windows 10-Geräte <!-- 2697002  -->

Wenn Sie ein Geräteeinschränkungsprofil für Windows-Geräte erstellen, können Sie die Einstellung **Apps from the store only** (Nur Apps aus dem Store) verwenden, damit Benutzer nur Apps aus dem Microsoft Store installieren können (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Diese Einstellung wird in einem zukünftigen Update mit weiteren Optionen erweitert. 

Die aktuellen Einstellungen finden Sie unter [Windows 10 (and newer) device settings to allow or restrict features using Intune (Geräteeinstellungen für Windows 10 (und höher) zum Zulassen oder Einschränken von Features mit Intune)](device-restrictions-windows-10.md#app-store).

Gilt für: Windows 10 und höher

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Bereitstellen mehrerer Zebra Mobility Extensions-Geräteprofile für ein Gerät, für dieselbe Benutzergruppe oder dieselbe Gerätegruppe <!-- 4089955 -->
Sie können Zebra Mobility Extensions (MX) in einem Gerätekonfigurationsprofil in Intune verwenden, um Einstellungen anzupassen oder um Einstellungen hinzuzufügen, die nicht in Intune integriert sind. Derzeit können Sie ein Profil für ein einzelnes Gerät bereitstellen. In einem zukünftigen Update können Sie mehrere Profile bereitstellen:

- für dieselbe Benutzergruppe
- für dieselbe Gerätegruppe
- für ein einzelnes Gerät

Unter [Nutzen und Verwalten von Zebra-Geräten mithilfe von Zebra Mobility Extensions in Microsoft Intune](android-zebra-mx-overview.md) wird die Verwendung von MX in Intune veranschaulicht.

Gilt für: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Für einige Kioskeinstellungen auf iOS-Geräten wird „Blockieren“ anstelle von „Zulassen“ verwendet. <!-- 4404075  -->
Beim Erstellen eines Geräteeinschränkungsprofils für iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Kiosk**) legen Sie die **Automatische Sperre**, den **Ruftonschalter**, die **Automatische Ausrichtung**, die **Standbytaste** und die **Lautstärkeregler** fest. 

Diese Einstellungen werden derzeit mit **Zulassen** (blockiert das Feature) oder **Nicht konfiguriert** (lässt das Feature zu) konfiguriert. Diese Werte werden in einem zukünftigen Update in **Blockieren** (blockiert das Feature) und **Nicht konfiguriert** (lässt das Feature zu) geändert.

Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md). 

Gilt für: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>Verwenden von Face ID für die Kennwortauthentifizierung auf iOS-Geräten <!-- 4490704  -->
Wenn Sie ein Geräteeinschränkungsprofil für iOS-Geräte erstellen, können Sie einen Fingerabdruck als Kennwort verwenden. In einem zukünftigen Update ermöglichen die Fingerabdruck-Kennworteinstellungen auch die Gesichtserkennung (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Kennwort**). Aus diesem Grund ändern sich die folgenden Einstellungen:

- **Entsperrung durch Fingerabdruck** heißt nun **Touch ID und Face ID entsperren**.
- **Fingerabdruckänderung (nur überwacht)** heißt nun **Touch ID- und Face ID-Änderungen (nur überwacht)** .

Face ID ist ab iOS 11.0 verfügbar. Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#password).

Gilt für: iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>Das Feature „Apps“ ist von der Bewertungsregion abhängig, wenn Spiele- und App Store-Features auf iOS-Geräten eingeschränkt werden <!-- 4593948  -->
Auf iOS-Geräten können Sie Features mit Bezug zu Spielen, dem App Store und dem Anzeigen von Dokumenten zulassen oder einschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **App Store, Dokumentanzeige, Spiele**). Sie können außerdem die Bewertungsregion auswählen, z. B. USA. In einem zukünftigen Update wird das Feature **Apps** der **Bewertungsregion** untergeordnet und von der **Bewertungsregion** abhängig sein.

Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gilt für: iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>Administrative Vorlagen für Gruppenrichtlinien     <!--  3510695 -->
Es werden administrative Vorlagen veröffentlicht, mit denen Sie Intune zum Konfigurieren ausgewählter Gruppenrichtlinieneinstellungen für Windows-Computer verwenden können, um die Sicherheit von Geräten in der Cloud zu verbessern.  Diese Vorlagen nutzen den Richtlinien-CSP (Konfigurationsdienstanbieter), um bis zu 2500 zusätzliche Einstellungen von Office, Windows und OneDrive bereitzustellen.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Neue Einstellungen für die Windows-Sicherheitsbaseline  <!-- 3534649, 4217151          -->
Es werden neue Einstellungen zur Windows-Sicherheitsbaseline hinzugefügt. Die erste Einstellung ist für die virtualisierungsbasierte Sicherheit und erfordert den sicheren Start. Mit der zweiten Einstellung können Sie die Sprachaktivierung von Windows-Apps bei gesperrtem Bildschirm verwalten.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>Sicherheitsbaselines werden allgemein verfügbar  <!--  3785395       -->
Die Vorschauphase des Sicherheitsbaselinefeatures ist bald vorbei. Das Feature wird dann allgemein verfügbar sein. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Die Windows-Sicherheitsbaselinevorlage wird allgemein verfügbar   <!--  3794072       -->
Die Vorschauphase der Windows-Sicherheitsbaselinevorlage ist bald vorbei. Sie wird dann allgemein verfügbar sein. Die Vorschauversion der Vorlage wird von einer neuen Vorlage abgelöst.

<!-- ***********************************************-->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Zuweisen von Bereichsmarkierungen zu allen verwalteten Geräten in einer Sicherheitsgruppe <!-- 3173810 -->
Derzeit können Sie eine Bereichsmarkierung zu einem Gerät zuweisen, indem Sie zur **Eigenschaftenseite** des jeweiligen Geräts navigieren und die Bereichsmarkierungen auswählen. In einem zukünftigen Update können Sie Bereichsmarkierungen einer Sicherheitsgruppe zuweisen. Die Bereichsmarkierungen werden allen Geräten in dieser Sicherheitsgruppe zugewiesen. Klicken Sie hierzu auf **Intune** > **Rollen** > **Bereich (Markierungen)**  > **Erstellen** > **Bereich (Markierungen)** , und wählen Sie dann die Gruppen aus, denen Sie die Bereichsmarkierung zuweisen möchten. Die Bereichsmarkierung wird allen Geräten in diesen Gruppen zugewiesen. Bereichsmarkierungen, die mit diesem Feature festgelegt werden, überschreiben die Bereichsmarkierungen, die mit der aktuellen Vorgehensweise zugewiesen wurden. (In einem zukünftigen Update wird der aktuelle Ablauf zum Zuweisen von Bereichsmarkierungen zu Geräten schreibgeschützt.)

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Anzeigen der Sicherheitspatchebene von Android-Geräten <!-- 4461911  -->
Sie können die Sicherheitspatchebene von Android-Geräten anzeigen. Klicken Sie hierzu auf **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Überwachen** > **Hardware**.


<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


