---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b96fa9fac25f6de4180d3dcc9ee4022a2cc43fe
ms.sourcegitcommit: 7484ef8006f6b81d8976c328dd704512a31872ec
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70190246"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>In der Entwicklung befindliche Microsoft Intune-Features: September 2019

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

### <a name="managed-google-play-private-lob-apps----1464182----"></a>Verwaltete Google Play private Lob-apps <!-- 1464182  -->
Mit InTune können IT-Administratoren private Android-Branchen-apps in verwalteten Google Play über einen in der InTune-Konsole eingebetteten iframe veröffentlichen.  Derzeit müssen IT-Administratoren Lob-apps direkt in der Wiedergabe Veröffentlichungs Konsole von Google veröffentlichen, was viele Schritte erfordert und sehr zeitaufwändig ist.  Diese neue Funktion ermöglicht eine einfache Veröffentlichung von Branchen-apps mit nur einem minimalen Satz von Schritten, ohne die Intune-Konsole verlassen zu müssen.  Alle Android Enterprise-Verwaltungs Szenarien, die verwaltete Google Play verwenden, können diese Funktion nutzen (Arbeitsprofil, dedizierte, vollständig verwaltete und nicht registrierte Geräte).  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann in der Liste **App-Typ** die Option **verwaltete Google Play** aus. Weitere Informationen zu verwalteten Google Play-apps finden [Sie unter Hinzufügen von verwalteten Google Play-apps zu Android-Unternehmens Geräten mit InTune](apps-add-android-for-work.md).

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Unternehmensportal App-Installationsstatus Meldungen <!-- 2514416  -->
Die Unternehmensportal-APP zeigt den Endbenutzern zusätzliche APP-Installationsstatus Meldungen an. Die folgenden Bedingungen gelten für neue Win32-Abhängigkeits Features:
- Die App konnte nicht installiert werden. Vom Administrator definierte Abhängigkeiten wurden nicht erfüllt.
- Die APP wurde erfolgreich installiert, erfordert aber einen Neustart.
- Die APP wird gerade installiert. es ist jedoch ein Neustart erforderlich, um den Vorgang fortzusetzen.

### <a name="managed-google-play-iframe-support----2871756----"></a>Verwaltete Google Play IFRAME-Unterstützung <!-- 2871756  -->
InTune bietet Unterstützung für das direkte Hinzufügen und Verwalten von Weblinks in der InTune-Konsole über den verwalteten Google Play iframe.  Dadurch können IT-Administratoren eine URL und eine Symbol Grafik einreichen und diese Links auf Geräten wie reguläre Android-Apps bereitstellen. Alle Android Enterprise-Verwaltungs Szenarien, die verwaltete Google Play verwenden, können diese Funktion nutzen (Arbeitsprofil, dedizierte, vollständig verwaltete und nicht registrierte Geräte).  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann in der Liste **App-Typ** die Option **verwaltete Google Play** aus. Weitere Informationen zu verwalteten Google Play-apps finden [Sie unter Hinzufügen von verwalteten Google Play-apps zu Android-Unternehmens Geräten mit InTune](apps-add-android-for-work.md).

### <a name="macos-support-for-vpp-apps----3173501----"></a>macOS-Unterstützung für VPP-apps <!-- 3173501  -->
macOS-apps, die Sie mit Apple Business Manager erworben haben, werden in der-Konsole angezeigt, wenn Apple VPP-Token in InTune synchronisiert werden. Mithilfe der-Konsole können Sie Geräte-und benutzerbasierte Lizenzen für Gruppen zuweisen, widerrufen und neu zuweisen. Microsoft InTune unterstützt Sie bei der Verwaltung von VPP-apps, die zur Verwendung in Ihrem Unternehmen erworben wurden
- Melden von Lizenzinformationen aus dem App Store
- Nachverfolgen der Anzahl bereits verwendeter Lizenzen
- Verhindern der Installation überzähliger Kopien der App
Weitere Informationen über Intune und VPP finden Sie unter [Verwalten von per Volumenlizenz erworbenen Apps und Büchern mit Microsoft Intune](vpp-apps.md).

### <a name="macos-support-for-web-apps----3174427----"></a>macOS-Unterstützung für Web-Apps <!-- 3174427  -->
Sie können Web-Apps installieren, mit denen Sie eine Verknüpfung zu einer URL im Web zum Andocken mithilfe der macOS-Unternehmensportal hinzufügen können. Endbenutzer können auf der Seite "App-Details" für eine Web-App im macOS-Unternehmensportal auf die Aktion " **Installieren** " zugreifen. Weitere Informationen zum **Weblink** -App-Typ finden [Sie unter Hinzufügen von apps zu Microsoft InTune](apps-add.md).

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Zuweisen von Microsoft Edge Beta für macOS <!-- 4678761  -->
Sie können die neueste Version von Microsoft Edge Beta in InTune für macOS-Geräte hinzufügen und zuweisen. Wählen Sie in InTune die Option **Client apps** > **apps** >  > **app hinzufügen** **Microsoft Edge-macOS**aus. Weisen Sie dann Microsoft Edge Beta den vorgesehenen Gruppen zu. Microsoft Auto Update (Mau) hält Microsoft Edge auf dem neuesten Stand. Weitere Informationen zu Microsoft Edge finden Sie unter [Verwalten des Webzugriffs mithilfe von Microsoft Edge mit Microsoft InTune](manage-microsoft-edge.md).

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Lese-und Schreibvorgänge Graph-API Vorgänge für InTune-apps <!-- 5031704  -->
Anwendungen können die Intune-Graph-API mit Lese-und Schreibvorgängen über die APP-Identität ohne Benutzer Anmelde Informationen abrufen. Weitere Informationen zum Zugriff auf die Microsoft Graph-API für Intune finden Sie unter [Arbeiten mit Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit InTune-App-Schutzrichtlinien (app) auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile <!-- 3041956  -->
Mit diesem Feature können Sie den App-Installationsstatus und die installierte Version verwalteter Google Play-Apps für verfügbare App-Installationen auf Android Arbeitsprofilgeräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>Geräte Features, Geräte Einschränkungen und Erweiterungs Profile für IOS-und macOS-Einstellungen werden durch den Anmeldungstyp angezeigt. <!-- 4886161  -->

In InTune erstellen Sie Profile für IOS-und MacOS-Geräte (**Geräte Konfigurations** > **profile** > **erstellen das Profil** > **IOS** oder **macOS** für Platt Form > **Geräte Features.** , **Geräte Einschränkungen**oder **Erweiterungen** für den Profiltyp. Derzeit werden die verfügbaren Einstellungen in diesen Profilen aufgeführt. 

In einem zukünftigen Update werden die verfügbaren Einstellungen im InTune-Portal nach dem Anmeldungstyp kategorisiert, für den Sie gelten:

- iOS
  - Alle Registrierungs Typen
  - Geräteregistrierung und automatisierte Geräteregistrierung
  - Automatisierte Geräteregistrierung

- macOS
  - Alle Registrierungs Typen
  - Geräteregistrierung
  - Benutzer genehmigte und automatisierte Geräteregistrierung
  - Automatisierte Geräteregistrierung

Gilt für:

- iOS
  - [Gerätefeatures](ios-device-features-settings.md)
  - [Geräteeinschränkungen](device-restrictions-ios.md)

- macOS
  - [Gerätefeatures](macos-device-features-settings.md)
  - [Geräteeinschränkungen](device-restrictions-macos.md)
  - [Erweiterungen](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>Neue sprach Steuerungseinstellungen für überwachte IOS-Geräte, die im Kiosk Modus ausgeführt werden <!-- 4892835  -->

In InTune können Sie Richtlinien erstellen, um überwachte IOS-Geräte als Kiosk oder dediziertes Gerät auszuführen (**Geräte Konfigurations** > **profile** > **erstellen das Profil** > **IOS** für Platform >  **Geräte Einschränkungen** für den Profiltyp > **Kiosk (nur überwacht)** ). 

In einem zukünftigen Update werden neue Einstellungen angezeigt, die Sie steuern können:

- **Voice-Steuer**Element: aktiviert die Sprachsteuerung auf dem Gerät im Kiosk Modus.
- **Änderung des sprach Steuer**Elements: erlauben Sie Benutzern, die sprach Steuerungs Einstellung im Kiosk Modus auf dem Gerät zu ändern.

Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu den Einstellungen für den [IOS-Kiosk (nur überwacht)](device-restrictions-ios.md#kiosk-supervised-only).

Gilt für:

- iOS 13.0 und höher

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>Verwenden von Single Sign-on für apps und Websites auf Ihren IOS-und macOS-Geräten <!-- 4893175  -->
In einem zukünftigen Update gibt es einige neue Single Sign-on Einstellungen für IOS-und MacOS-Geräte (**Geräte Konfigurations** > **profile** > **erstellen ein Profil** > für**IOS** oder **MacOS** ). Plattform > **Geräte Features** für Profiltyp).

Verwenden Sie diese Einstellungen, um eine Single Sign-on Umgebung zu konfigurieren, insbesondere für apps und Websites, die die Kerberos-Authentifizierung verwenden. Sie können zwischen den Allgemeinen Anmelde Informationen Single Sign-on App-Erweiterung und der integrierten Kerberos-Erweiterung von Apple wählen.

Informationen zu den aktuellen Gerätefunktionen, die Sie konfigurieren können, finden Sie unter [IOS-Geräte Features](ios-device-features-settings.md) und [macOS-Geräte Features](macos-device-features-settings.md).

Gilt für:

- iOS 13.0 und neuer
- macOS 10.15 und neuer

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>Zuordnen von Domänen zu apps auf macOS-Geräten mit 10,15 und höher <!-- 4898079  -->
Auf macOS-Geräten können Sie verschiedene Features konfigurieren und diese Features mithilfe einer Richtlinie auf Ihre Geräte überführen (**Geräte Konfigurations** > **profile** > **Erstellen** > **macOS** für das Profil). Plattform > **Geräte Features** für Profiltyp). In einem zukünftigen Update können Sie Domänen zu ihren apps zuordnen. Diese Funktion hilft bei der Freigabe von Anmelde Informationen für Websites, die mit Ihrer APP verknüpft sind, und kann mit der Single Sign-on Erweiterung von Apple, den universellen Links und dem Kenn Wort AutoFill verwendet werden. 

Informationen zu den aktuellen Funktionen, die Sie konfigurieren können, finden Sie unter [macOS-Geräte Funktionseinstellungen in InTune](macos-device-features-settings.md).

Gilt für:

- macOS 10.15 und neuer

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>Verwenden Sie "iTunes" und "Apps" in der iTunes App Store-URL, wenn Sie Apps auf überwachten IOS-Geräten ein-oder ausblenden. <!-- 4928474  --> 
In InTune können Sie Richtlinien erstellen, um apps auf Ihren überwachten IOS-Geräten anzuzeigen oder auszublenden (**Geräte Konfigurations** > **profile** > **erstellen das Profil** > **IOS** für die Plattform > **Gerät Einschränkungen** für den Profiltyp > **anzeigen oder Ausblenden von apps (nur überwacht)** ). 

Sie können die iTunes-App Store-URL eingeben, `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`z. b.. In einem zukünftigen Update können Sie sowohl `apps` als auch `itunes` in der URL verwenden, z. b.:

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Weitere Informationen zu diesen Einstellungen finden Sie unter [anzeigen oder Ausblenden von apps (nur überwacht)](device-restrictions-ios.md#show-or-hide-apps-supervised-only).

Gilt für:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Unterstützung für IKEv2-VPN-Profile für iOS <!-- 1943438 -->
Sie können VPN-Profile für den nativen VPN-Client für iOS mithilfe des IKEv2-Protokolls erstellen. IKEv2 ist ein neuer Verbindungstyp unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **VPN** (Profiltyp) > **Einstellungen**.

Mit diesen VPN-Profilen wird der native VPN-Client konfiguriert. Es werden keine VPN-Client-Apps installiert oder an verwaltete Geräte gepusht. Für dieses Feature müssen Geräte in Intune registriert sein (MDM-Registrierung).

Die derzeit konfigurierbaren VPN-Einstellungen finden Sie unter [Configure VPN settings on iOS devices in Microsoft Intune (Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune)](vpn-settings-ios.md).

Gilt für: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>Geräteregistrierung

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Neue Mandanten werden standardmäßig von der Verwaltung von Android-Geräte Administratoren entfernt <!-- 4869790  -->
Die Geräte Administrator Funktionen von Android wurden durch Android Enterprise abgelöst. Daher wird empfohlen, stattdessen Android Enterprise für neue Registrierungen zu verwenden. In einem zukünftigen Update müssen neue Mandanten die folgenden erforderlichen Schritte in der Android-Registrierung durchführen, um die Geräte Administrator Verwaltung zu verwenden: Wechseln Sie zu **InTune** > **Geräte** > Registrierung**Android** -Registrierung. Persönliche und **unternehmenseigene Geräte mit Geräte Verwaltungs Berechtigungen** > **verwenden den Geräte Administrator zum Verwalten von Geräten.**  > 

Vorhandene Mandanten werden in ihren Umgebungen nicht geändert. 

Weitere Informationen zum Android-Geräte Administrator in InTune finden Sie unter Registrierung von [Android-Geräte Administratoren](https://docs.microsoft.com/intune/android-enroll-device-administrator).

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Passen Sie für IOS-Geräte den Datenschutz Bildschirm des Anmeldungsprozesses des Unternehmensportal <!-- 4394993  -->
Mithilfe von markdown können Sie den Datenschutz Bildschirm des Unternehmensportal anpassen, den Endbenutzern während der IOS-Registrierung angezeigt werden. Insbesondere können Sie die Liste der Dinge anpassen, die Ihre Organisation nicht auf dem Gerät sehen oder ausführen kann.

<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Bereitstellen von Software Updates für macOS-Geräte <!-- 3194876 -->
Sie können Software Updates für Gruppen von macOS-Geräten bereitstellen. Diese Funktion umfasst kritische, Firmware-und Konfigurationsdateien sowie andere Updates. Sie können beim nächsten Einchecken von Geräten Updates senden oder einen wöchentlichen Zeitplan auswählen, um Updates in oder außerhalb der von Ihnen festgelegten Zeitfenster bereitzustellen. Dies hilft, wenn Sie Geräte außerhalb der Standard Arbeitszeiten aktualisieren möchten oder wenn Ihr Helpdesk vollständig besetzt ist. Außerdem erhalten Sie einen ausführlichen Bericht zu allen macOS-Geräten, auf denen Updates bereitgestellt werden. Sie können einen Drilldown in den Bericht pro Gerät durchführen, um die Status bestimmter Updates anzuzeigen.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>Senden von benutzerdefinierten Benachrichtigungen an ein Gerät <!-- 4928910  -->
Sie können benutzerdefinierte Benachrichtigungen an bestimmte Geräte senden, auf denen die Unternehmensportal oder die Intune-App installiert ist. Navigieren Sie hierzu zu **InTune** > -**Geräte** > **alle Geräte** > Wählen Sie ein Gerät > **Weitere** > **benutzerdefinierte Benachrichtigung senden**aus. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Updates für vollständig verwaltete Android Enterprise-Features <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Wir werden die folgende Unterstützung für vollständig verwaltete Android-Geräte hinzufügen:

- SCEP-Zertifikate für vollständig verwaltete Android-Geräte sind für die Zertifikat Authentifizierung auf Geräten verfügbar, die als Gerätebesitzer verwaltet werden. SCEP-Zertifikate werden bereits auf Arbeitsprofil Geräten unterstützt.  Mit SCEP-Zertifikaten für den Gerätebesitzer haben Sie folgende Möglichkeit: <!-- 5227935 -->
    - Erstellen eines SCEP-Profils im Abschnitt "Do" von Android Enterprise
    - Verknüpfen von SCEP-Zertifikaten mit WLAN-Profilen für die Authentifizierung
    - Verknüpfen von SCEP-Zertifikaten mit VPN-Profilen für die Authentifizierung
    - Verknüpfen von SCEP-Zertifikaten mit e-Mail-Profilen für die Authentifizierung (über AppConfig)
- System-apps werden auf Android-Unternehmens Geräten unterstützt. In InTune fügen Sie eine Android Enterprise System-App hinzu, indem Sie **Client apps** > **apps** > **Hinzufügen**auswählen. Wählen Sie in der Liste **App-Typ** die Option **Android Enterprise System App**aus. Weitere Informationen zum Hinzufügen von Apps zu Intune finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](apps-add.md). <!-- 4062195 -->
- Unter **Geräte Konformität** > **Android-Unternehmens** > **Gerätebesitzer**können Sie eine Kompatibilitäts Richtlinie erstellen, mit der die Ebene "Google SafetyNet Nachweis" festgelegt wird.   <!-- 4631425 -->
- Auf vollständig verwalteten Android-Geräten werden die Mobile Threat Defense-Anbieter unterstützt. Unter **Geräte Konformität** > **Android-Unternehmens** > **Gerätebesitzer**können Sie eine akzeptable Bedrohungsstufe auswählen. <!-- 4631440 --> Unter [Android Enterprise-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen](compliance-policy-create-android-for-work.md#device-owner) werden die aktuellen Einstellungen aufgelistet.


Gilt für: 
- Vollständig verwaltete Android Enterprise-Geräte

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

### <a name="updated-support-experience-------5012398------"></a>Aktualisierter Support   <!--  5012398    -->
Im Rahmen der fortlaufenden Verbesserungen wird die Unterstützung der Konsolen internen Unterstützung für InTune aktualisiert.  Wir werden die Konsolen interne Suche und das Feedback zu häufigen Problemen verbessern und den Workflow optimieren, um den Support zu kontaktieren.     

<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Schutz für Windows Defender Antivirus manipulieren  <!-- 4705448       -->
Wir werden den Einstellungen, die Intune für Windows Defender Antivirus verwalten kann, *Manipulationsschutz* hinzufügen. Sie können ein Geräte Konfigurations Profil für Windows 10 Endpoint Protection verwenden, um den Manipulationsschutz zu aktivieren oder zu deaktivieren.  Weitere Informationen zum Manipulationsschutz finden Sie unter [verhindern von Änderungen an Sicherheitseinstellungen mit Manipulationsschutz](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) in der Windows-Dokumentation. 


<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).




