---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833549"
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

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>Steuern des Deinstallations Verhaltens der IOS-App bei der Registrierung des Geräts <!-- 3504144 -->
Administratoren können verwalten, ob eine APP auf einem Gerät entfernt oder aufbewahrt wird, wenn die Registrierung des Geräts auf Benutzer-oder Gerätegruppen Ebene aufgehoben wird. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Kategorisieren von Apps aus dem Microsoft Store für Unternehmen <!-- 3926922 -->
Sie können Microsoft Store für Business-Apps kategorisieren. Wählen Sie **hierzu die Option** > InTune-**Client**-apps > -appsaus **, >** eine Microsoft Store **für Business-app >-app auszuwählen.**  >  **InformationsKategorie.** Weisen Sie im Dropdown Menü eine Kategorie zu.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurieren von App-Benachrichtigungs Inhalten für Organisations Konten <!-- 2576686 -->
Mit InTune-App-Schutzrichtlinien (app) auf Android-und IOS-Geräten können Sie App-Benachrichtigungs Inhalte für Organisations Konten steuern. Diese Funktion erfordert Unterstützung von Anwendungen und ist möglicherweise nicht für alle App-fähigen Anwendungen verfügbar. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile <!-- 3041956  -->
Mit diesem Feature können Sie den App-Installationsstatus und die installierte Version verwalteter Google Play-Apps für verfügbare App-Installationen auf Android Arbeitsprofilgeräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>Einige nicht überwachte IOS-Geräte Einschränkungen werden nur mit der IOS 13,0-Version überwacht. <!-- 4867809  -->
Einige Einstellungen gelten für überwachte Geräte ab der IOS 13,0-Version. Zu diesen Einstellungen zählen:

- App Store, Dokumentanzeige, Spiele
  - App Store
  - Explizite iTunes-, Musik-, Podcast-oder News-Inhalte
  - Hinzufügen von Game Center-Freunden
  - Multiplayerspiele
- Integrierte Apps
  - Kamera
    - FaceTime
  - Safari
    - Automatisch ausfüllen
- Cloud und Speicher
  - In iCloud sichern
  - Icloud-Dokument Synchronisierung blockieren
  - Synchronisierung zwischen iCloud und Keychain blockieren

Wenn diese Einstellungen konfiguriert und vor der IOS 13,0-Version nicht überwachte Geräte zugewiesen werden, werden die Einstellungen weiterhin auf diese nicht überwachten Geräte angewendet. Sie gelten auch nach der Aktualisierung der Geräte auf IOS 13,0. Diese Einschränkungen werden auf nicht überwachten Geräten entfernt, die gesichert und wieder hergestellt werden. 

Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md).

Gilt für:  
- IOS 13,0 und höher

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>Neue Einstellungen und Änderungen an vorhandenen Einstellungen zum Einschränken von Features auf IOS-und macOS-Geräten <!-- 4867699 4867709  -->
Sie können Profile erstellen, um Einstellungen auf IOS-und macOS-Geräten einzuschränken (**Geräte Konfigurations** > **profile** > **Profilerstellen**). > **IOS** **odermacOS**für Platt Form Typen >**GeräteEinschränkungen**). Die folgenden Funktionen werden hinzugefügt:

- VerwendenSie unter **macOS-Geräte** > **Einschränkungen** >  **in der Cloud und im Speicher**die neue**Handoff-Einstellung.** Blockieren Sie die Arbeit von Benutzern auf einem MacOS-Gerät, und arbeiten Sie weiterhin mit einem anderen MacOS-oder IOS-Gerät.
  Die aktuellen Einstellungen finden Sie unter [macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-macos.md).
- Bei **IOS**- > **Geräte**Einschränkungen gibt es einige Änderungen:
  - **Integrierte apps** >  **: "mein iPhone suchen" (nur überwacht)** : neue Einstellung, die dieses Feature in der Funktion "meine APP suchen" blockiert. 
  - **Integrierte apps** >  **suchen meine Freunde (nur überwacht)** : neue Einstellung, die dieses Feature in der Funktion "meine APP suchen" blockiert. 
  - **Drahtlose** >  **Änderung des WLAN-Status (nur überwacht)** : neue Einstellung, die verhindert, dass Benutzer WLAN auf dem Gerät einschalten oder ausschalten.
  - **QuickPath für**Tastatur und Wörterbuch >  **(nur**überwacht): neue Einstellung, die die QuickPath-Funktion blockiert.
  - **Cloud und Speicher**: **die Aktivitäts** Fortsetzung wird **in "** Handoff" umbenannt.

  Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md).

Gilt für:  
- macOS 10,15 und höher
- IOS 13 und höher

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>Steuern der apps, Dateien, Dokumente und Ordner, die geöffnet werden, wenn sich der Benutzer bei macOS-Geräten anmeldet <!--3914202  -->
Sie sind in der Lage, Features auf macOS-Geräten zu aktivieren**und zu**konfigurieren >  **(Geräte Konfigurationprofile** > **Profilerstellen)** . >  **macOS** für Platt Form **> Geräte** Features für Profiltyp). 

Es gibt neue Einstellungen für Anmelde Elemente, mit denen gesteuert werden kann, welche apps, Dateien, Dokumente und Ordner geöffnet werden, wenn sich ein Benutzer am registrierten Gerät anmeldet. 

Informationen zu den aktuellen Einstellungen [finden Sie unter macOS-Geräte Funktionseinstellungen in InTune.](macos-device-features-settings.md)

Gilt für:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>Neue Features für Android Enterprise Dedicated-Geräte im Multi-APP-Modus <!-- 3755304 3041943 3041946  -->
Sie können Funktionen und Einstellungen in einem Kiosk-Stil auf Ihren dedizierten Geräten mit Android-Unternehmen steuern. **Wählen Sie hierzu Gerätekonfiguration**  > **ProfileProfilerstellen**  >  **AndroidEnterPriseaus.**  > **nur für Platt** **Form > Gerätebesitzer, Geräte** Einschränkungen für den Profiltyp.

Die folgenden Funktionen werden hinzugefügt:
- **Dedizierte**Geräte > Multi **-APP**: die**virtuelle Start** Schaltfläche kann angezeigt werden, indem Sie auf dem Gerät schwenken oder auf dem Bildschirm unverankert sind, damit Benutzer Sie verschieben können.
- **Dedizierte**Geräte > Multi **-App** :**derZugriff** auf die Taschenlampe ermöglicht Benutzern die Verwendung der Taschenlampe. 
- **Dedizierte**Geräte > Multi **-APP**: die **Medienvolumen Steuerung ermöglicht** es Benutzern, das Medien Volume des Geräts mithilfe eines Schiebereglers zu steuern. 
- **Dedizierte** > Geräte**Multi-App**: Aktivieren Sie einen Bildschirmschoner, laden Sie ein benutzerdefiniertes Bild hoch, und Steuern Sie, wann der Bildschirmschoner angezeigt wird

Die aktuellen Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Gilt für:  
- Dedizierte Android Enterprise-Geräte

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Neue APP-und Konfigurations Profile für vollständig verwaltete Android Enterprise-Geräte <!-- 3574215  -->
Mithilfe von Profilen können Sie Einstellungen konfigurieren, die VPN-, e-Mail-und WLAN-Einstellungen auf ihre vollständig verwalteten Android-Geräte anwenden. Folgende Aktionen sind möglich:
- Verwenden Sie App-Profile zum Bereitstellen von Outlook, Gmail und neun Work-e-Mail-Einstellungen.
- Verwenden Sie Geräte Konfigurations Profile, um Einstellungen für vertrauenswürdige Stamm Zertifikate bereitzustellen.
- Verwenden Sie Geräte Konfigurations Profile zum Bereitstellen von VPN-und WLAN-Einstellungen.

Benutzer authentifizieren sich mit Ihrem Benutzernamen und Kennwort für VPN-, WLAN-und e-Mail-Profile. Derzeit ist die Zertifikat basierte Authentifizierung nicht verfügbar. 

Gilt für:  
- Vollständig verwaltetes Android Enterprise

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Unterstützung für IKEv2-VPN-Profile für iOS <!-- 1943438 -->
Sie können VPN-Profile für den nativen VPN-Client für iOS mithilfe des IKEv2-Protokolls erstellen. IKEv2 ist ein neuer Verbindungstyp unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **VPN** (Profiltyp) > **Einstellungen**.

Mit diesen VPN-Profilen wird der native VPN-Client konfiguriert. Es werden keine VPN-Client-Apps installiert oder an verwaltete Geräte gepusht. Für dieses Feature müssen Geräte in Intune registriert sein (MDM-Registrierung).

Die derzeit konfigurierbaren VPN-Einstellungen finden Sie unter [Configure VPN settings on iOS devices in Microsoft Intune (Konfigurieren von VPN-Einstellungen für iOS-Geräte in Microsoft Intune)](vpn-settings-ios.md).

Gilt für: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Geräteregistrierung

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>Weitere Bildschirme im Setup-Assistenten überspringen <!--4877451 -->
Sie können Programm zur Geräteregistrierung Profile festlegen, um die folgenden Bildschirme des Setup-Assistenten zu überspringen: 
- Bildschirmzeit
- Touchscreen

Wechseln **Sie hierzu zu**   > **GeräteRegistrierungApple**-RegistrierungRegistrierungsprogrammToken  >  **> Token** auswählen **> Profile** > Wählen Sie ein Profil **>**  > Eigenschaften**bearbeitennebenAnpassung**des **Setup-Assistentenaus**.
Weitere Informationen zur Anpassung des Setup-Assistenten finden [Sie unter Erstellen eines Apple- ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)Registrierungs Profils.

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Android-Registrierungs Geräte-Administrator Unterstützung <!-- 4869749  -->
Die Registrierungsoption Android-Geräte Administrator wird der Seite Android-Registrierung**hinzugefügt (InTune** >  **-Geräte** > Registrierung Android **).** Registrierung). Der Android-Geräte Administrator ist weiterhin standardmäßig für alle Mandanten aktiviert.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Passen Sie für IOS-Geräte den Datenschutz Bildschirm des Anmeldungsprozesses des Unternehmensportal <!-- 4394993  -->
Mithilfe von markdown können Sie den Datenschutz Bildschirm des Unternehmensportal anpassen, den Endbenutzern während der IOS-Registrierung angezeigt werden. Insbesondere können Sie die Liste der Dinge anpassen, die Ihre Organisation nicht auf dem Gerät sehen oder ausführen kann.

<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Auf der Android-Geräte Hardware Seite enthaltene Buildnummer <!-- 4461910  -->
Ein neuer Eintrag auf der Hardware Seite für jedes Android-Gerät enthält die Buildnummer des Betriebssystems des Geräts.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurieren der automatischen Geräte Bereinigung auf bis zu 30 Tage <!--4231059  -->
Nach der letzten Anmeldung können Sie den Grenzwert für die automatische Bereinigung von Geräten auf 30 Tage festlegen (anstelle des aktuellen Limits von 90 Tagen). Wechseln **Sie hierzu zu InTune-Geräte**  > **Einrichten**  > **Geräte Bereinigungs**  >  **Regeln**.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

### <a name="default-scope-tag----3702875---"></a>Standard Bereichs Kennzeichen <!-- 3702875 -->
Es ist ein neues integriertes Standard Bereichs Kennzeichen verfügbar. Alle nicht markierten InTune-Objekte, die Bereichs Markierungen unterstützen, werden automatisch dem Standard Bereichs Kennzeichen zugewiesen. Das **standardbereichstag** wird allen vorhandenen Rollenzuweisungen hinzugefügt, um die Parität mit der Administrator Funktionalität zu gewährleisten. Wenn Sie nicht möchten, dass ein Administrator InTune-Objekte mit standardmäßigen Bereichs Tags sieht, entfernen Sie das Standard Bereichs Kennzeichen aus der Rollenzuweisung. Diese Funktion ähnelt der Funktion Sicherheitsbereiche in System Center Configuration Manager.

<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="import-and-export-security-baselines------3408610------------"></a>Importieren und Exportieren von Sicherheitsbaselines    <!--3408610          -->  
Wir fügen die Funktion zum Exportieren und Importieren von Sicherheitsbaselines hinzu. Mit diesem Feature können Sie Ihre Anpassungen mit Ihnen durchführen und Sie in InTune-Umgebungen freigeben.

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).




