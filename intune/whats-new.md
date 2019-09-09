---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09d80964a417772b1f011478db59398ceede5c5e
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122142"
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Hier finden Sie auch [wichtige Hinweise](#notices), [frühere Releases](whats-new-archive.md) und Informationen zur [Veröffentlichung von Intune-Dienstupdates](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Bei jedem [monatlichen Update](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kann das Rollout bis zu drei Tage dauern und erfolgt in dieser Reihenfolge:
> - 1\. Tag: Asien-Pazifik (APAC)
> - 2\. Tag: Europa, Naher Osten und Afrika (EMEA)
> - 3\. Tag: Nordamerika
> 
> Einige Features werden im Laufe mehrerer Wochen bereitgestellt und sind in der ersten Woche möglicherweise nicht für alle Kunden verfügbar.
>
> Auf der Seite [Features in der Entwicklung](in-development.md) finden Sie eine Liste der neuen Features in einem Release.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-august-26-2019"></a>Woche vom 26. August 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Konfigurieren von Microsoft Edge-Einstellungen mithilfe administrativer Vorlagen für Windows 10 und höher <!-- 5228061 -->

Auf Geräten mit Windows 10 oder höher können Sie administrative Vorlagen erstellen, um Gruppenrichtlinieneinstellungen in Intune zu konfigurieren. In diesem Update können Sie Einstellungen konfigurieren, die auf Microsoft Edge Version 77 und höher angewendet werden.

Weitere Informationen zu administrativen Vorlagen finden Sie unter [Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Intune](administrative-templates-windows.md).

Gilt für:

- Windows 10 und höher (Windows RS4 und höher)

## <a name="week-of-august-12-2019"></a>Woche vom 12. August 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>Steuern des Deinstallationsverhaltens einer iOS-App bei einer Aufhebung der Registrierung eines Geräts <!-- 3504144   -->
Administratoren können verwalten, ob eine App von einem Gerät entfernt oder auf dem Gerät beibehalten wird, wenn die Registrierung des Geräts auf Benutzer- oder Gerätegruppenebene aufgehoben wird. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>Kategorisieren von Apps aus dem Microsoft Store für Unternehmen <!-- 3926922 -->
Sie können Microsoft Store für Unternehmen-Apps kategorisieren. Wählen Sie hierzu **Intune** > **Client-Apps** > **Apps** > eine Microsoft Store für Unternehmen-App auswählen > **App-Informationen** > **Kategorie** aus. Weisen Sie im Dropdownmenü eine Kategorie zu.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Angepasste Benachrichtigungen für Microsoft Intune-App-Benutzer <!-- 4843354  -->
Die Microsoft Intune-App für Android unterstützt jetzt die Anzeige von benutzerdefinierten Pushbenachrichtigungen, wodurch sie an die Unterstützung angepasst ist, die kürzlich in den Unternehmensportal-Apps für iOS und Android hinzugefügt wurde. Weitere Informationen finden Sie unter [Senden benutzerdefinierter Benachrichtigungen in Intune](custom-notifications.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>Neue Features für dedizierte Android Enterprise-Geräte im Multi-App-Modus <!-- 3755304 3041943 3041946   -->
In Intune können Sie Features und Einstellungen in einer kioskartigen Umgebung auf Ihren dedizierten Android Enterprise-Geräten verwalten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Nur Gerätebesitzer, Geräteeinschränkungen** für Profiltyp).

In diesem Update werden die folgenden Features hinzugefügt:

- **Dedizierte Geräte** > **Multi-App**: Die **Virtuelle Startschaltfläche** kann angezeigt werden, indem auf dem Gerät nach oben gewischt wird oder die Schaltfläche auf dem Bildschirm schwebt, sodass Benutzer sie verschieben können.
- **Dedizierte Geräte** > **Multi-App**: **Flashlight-Zugriff** ermöglicht es Benutzern, die Taschenlampe zu verwenden. 
- **Dedizierte Geräte** > **Multi-App**: **Medienlautstärkeregler** ermöglicht es Benutzern, über einen Schieberegler die Medienlautstärke des Geräts zu steuern. 
- **Dedizierte Geräte** > **Multi-App**:  **Einen Bildschirmschoner aktivieren**, ein benutzerdefiniertes Bild hochladen und steuern, wann der Bildschirmschoner angezeigt wird.

Die aktuellen Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](device-restrictions-android-for-work.md#dedicated-device-settings).

Gilt für:  
- Dedizierte Android Enterprise-Geräte

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Neue App- und Konfigurationsprofile für vollständig verwaltete Android Enterprise-Geräte <!-- 3574215 3574238 3574235 3574232   -->
Mithilfe von Profilen können Sie Einstellungen konfigurieren, mit denen VPN-, E-Mail-und WLAN-Einstellungen auf Ihre (vollständig verwalteten) Android Enterprise-Gerätebesitzer-Geräte angewendet werden. In diesem Update haben Sie folgende Möglichkeiten:

- Sie können [App-Konfigurationsrichtlinien](app-configuration-policies-use-android.md) verwenden, um Outlook-, Gmail- und Nine Work-E-Mail-Einstellungen bereitzustellen.
- Sie können Gerätekonfigurationsprofile verwenden, um [Einstellungen für vertrauenswürdige Stammzertifikate](certificates-configure.md) bereitzustellen.
- Sie können Gerätekonfigurationsprofile verwenden, um [VPN](vpn-settings-android-enterprise.md)- und [WLAN](wi-fi-settings-android-enterprise.md)-Einstellungen bereitzustellen.

> [!IMPORTANT]
> Mit diesem Feature authentifizieren sich Benutzer mit Ihrem Benutzernamen und Kennwort für VPN-, WLAN- und E-Mail-Profile. Derzeit ist zertifikatbasierte Authentifizierung nicht verfügbar. 

Gilt für:  
- Android Enterprise-Gerätebesitzer (vollständig verwaltet)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>Steuern der Apps, Dateien, Dokumente und Ordner, die geöffnet werden, wenn Benutzer sich bei macOS-Geräten anmelden <!--3914202   -->
Sie können Funktionen auf macOS-Geräten aktivieren und konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** für Plattform > **Gerätefunktionen** für Profiltyp). 

In diesem Update gibt es eine neue „Anmeldeelemente“-Einstellung, mit der gesteuert wird, welche Apps, Dateien, Dokumente und Ordner geöffnet werden, wenn sich ein Benutzer am registrierten Gerät anmeldet. 

Informationen zu den aktuellen Einstellungen finden Sie unter [macOS-Gerätefunktionseinstellungen in Intune](macos-device-features-settings.md).

Gilt für:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>Stichtage ersetzen Einstellungen für erzwungenen Neustart für Windows-Updateringe   <!-- 4464404        -->
Um mit den neuesten [Windows-Wartungsänderungen](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing) übereinzustimmen, unterstützen die Windows 10-Updateringe von Intune jetzt [Einstellungen für Stichtage](windows-update-settings.md). *Stichtage* bestimmen, wann Funktions- und Sicherheitsupdates auf einem Gerät installiert werden.  Auf Geräten, auf denen Windows 10 1903 oder höher ausgeführt wird, ersetzen *Stichtage* die Konfigurationen für *erzwungenen Neustart*.  Zukünftig wird auch in früheren Versionen von Windows 10 *erzwungener Neustart* durch *Stichtage* ersetzt.  

Wenn Sie keine *Stichtage* konfigurieren, werden für Geräte weiterhin deren Einstellungen für *erzwungenen Neustart* verwendet. In einem zukünftigen Update wird die [Intune-Unterstützung für die Einstellungen für erzwungenen Neustart aber beendet werden](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-).  

Sie sollten die Verwendung von *Stichtagen* für sämtliche Ihrer Windows 10-Geräte planen. Sobald Einstellungen für *Stichtage* vorhanden sind, können Sie die Intune-Konfigurationen für *erzwungenen Neustart* auf „Nicht konfiguriert“ festlegen. Sind diese Konfigurationen auf „Nicht konfiguriert“ festgelegt, beendet Intune das Verwalten dieser Einstellungen auf Geräten, ohne die letzten Konfigurationen für die Einstellung vom Gerät zu entfernen. Daher bleiben die letzten Konfigurationen, die für *erzwungenen Neustart* festgelegt wurden, solange auf Geräten aktiv und wirksam, bis diese Einstellungen durch eine andere Methode als Intune geändert werden. Wenn sich später die Geräteversion von Windows ändert oder wenn später die Intune-Unterstützung für *Stichtage* auf die Windows-Version der Geräte erweitert wird, werden auf dem jeweiligen Gerät die neuen Einstellungen verwendet, die bereits vorhanden sind.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>Unterstützung für mehrere Microsoft Intune Certificate Connectors   <!--   4704642      -->
Intune unterstützt nun die Installation und Verwendung von mehreren [Microsoft Intune Certificate Connectors für PKCS-Vorgänge](certficates-pfx-configure.md). Diese Änderung unterstützt Lastenausgleich und Hochverfügbarkeit der Connectors. Jede Connectorinstanz kann Zertifikatanforderungen von Intune verarbeiten.  Ist ein Connector nicht verfügbar, übernehmen andere Connectors die Verarbeitung von Anforderungen. 

Wenn Sie mehrere Connectors verwenden möchten, müssen Sie kein Upgrade auf die neueste Version der Connector-Software durchführen.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>Neue Einstellungen und Änderungen an vorhandenen Einstellungen, um Funktionen auf iOS- und macOS-Geräten einzuschränken <!-- 4867699 4867709   -->
Sie können Profile erstellen, um Einstellungen auf iOS-und macOS-Geräten einzuschränken (**Gerätekonfigurationen** > **Profile** > **Profil erstellen** > **iOS** oder **macOS** für Plattformtyp > **Geräteeinschränkungen**). Dieses Update umfasst folgende Funktionen:

- Unter **macOS** > **Geräteeinschränkungen** > **Cloud und Speicher** verwenden Sie die neue **Handoff**-Einstellung, um Benutzer daran zu hindern, eine Arbeit auf einem macOS-Gerät zu beginnen und diese Arbeit auf einem anderen macOS- oder iOS-Gerät fortzusetzen.

  Die aktuellen Einstellungen finden Sie unter [macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-macos.md).

- Unter **iOS** > **Geräteeinschränkungen** gibt es einige Änderungen:

  - **Integrierte Apps** > **Mein iPhone suchen (nur überwacht)** : Neue Einstellung, die diese Funktion im App-Feature für die Suche blockiert. 
  - **Integrierte Apps** > **Meine Freunde suchen (nur überwacht)** : Neue Einstellung, die diese Funktion im App-Feature für die Suche blockiert. 
  - **Drahtlosnetzwerke** > **Änderung des WLAN-Status (nur überwacht)** : Neue Einstellung, die verhindert, dass Benutzer WLAN auf dem Gerät ein- oder ausschalten können.
  - **Tastatur und Wörterbuch** > **QuickPath (nur überwacht)** : Neue Einstellung, die die QuickPath-Funktion blockiert.
  - **Cloud und Speicher**: **Aktivitätsfortsetzung** wurde in **Handoff** umbenannt.

  Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md).

Gilt für:  
- macOS 10.15 und neuer
- iOS 13 und neuer

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>Einige nicht überwachte iOS-Geräteeinschränkungen werden mit der iOS 13.0-Version zu unbedingt überwachten Einschränkungen <!-- 4867809   -->
In diesem Update gelten einige Einstellungen für unbedingt überwachte Geräte mit der iOS 13.0-Version. Sind diese Einstellungen für nicht überwachte Geräte vor der iOS 13.0-Version konfiguriert und diesen zugewiesen, werden die Einstellungen weiterhin auf diese nicht überwachten Geräte angewendet. Diese Einstellungen gelten auch weiterhin, nachdem die Geräte auf iOS 13.0 aktualisiert wurden. Diese Einschränkungen werden auf nicht überwachten Geräten entfernt, die gesichert und wiederhergestellt werden. 

Zu diesen Einstellungen zählen:

- App Store, Dokumentanzeige, Spiele
  - App Store
  - Anstößige iTunes-Musik, Podcasts oder Nachrichteninhalte
  - Hinzufügen von Game Center-Freunden
  - Multiplayerspiele
- Integrierte Apps
  - Kamera
    - FaceTime
  - Safari
    - Automatisch ausfüllen
- Cloud und Speicher
  - In iCloud sichern
  - iCloud-Dokumentsynchronisierung blockieren
  - Synchronisierung zwischen iCloud und Keychain blockieren

Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md).

Gilt für:  
- iOS 13.0 und neuer

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>Verbesserter Gerätestatus für die macOS FileVault-Verschlüsselung  <!-- 4944983         -->
Wir haben einige der [Gerätestatusmeldungen](encryption-monitor.md#device-encryption-status) für die FileVault-Verschlüsselung auf macOS-Geräten aktualisiert.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>Für einige Windows Defender Antivirus-Überprüfungseinstellungen steht in Berichten der Status „Fehlgeschlagen“ <!-- 5119229 -->
In Intune können Sie Richtlinien erstellen, um Windows Defender Antivirus zum Überprüfen Ihrer Windows 10-Geräte zu verwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** für Plattform > **Geräteeinschränkungen** für Profiltyp > **Windows Defender Antivirus**). In Berichten steht für **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung** und **Art der durchzuführenden Systemüberprüfung** der Status „Fehlgeschlagen“, obwohl tatsächlich der Status „Erfolgreich“ gemeint ist. 

Dieses Verhalten wurde im vorliegenden Update korrigiert. Daher wird für die Einstellungen **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung** und **Art der durchzuführenden Systemüberprüfung** der Status „Erfolgreich“ mitgeteilt, wenn die Überprüfungen erfolgreich abgeschlossen wurden, und der Status „Fehlgeschlagen“, wenn die Einstellungen nicht angewendet werden konnten. 

Weitere Informationen zu den Windows Defender Antivirus-Einstellungen finden Sie unter [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](device-restrictions-windows-10.md#windows-defender-antivirus). 

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="default-scope-tags----3702875----"></a>Standardbereichsmarkierungen <!-- 3702875  -->
Es ist nun eine neue integrierte Standardbereichsmarkierung verfügbar. Alle nicht markierten Intune-Objekte, die Bereichsmarkierungen unterstützen, werden automatisch der Standardbereichsmarkierung zugewiesen. Die **Standard**-Bereichsmarkierung wird allen vorhandenen Rollenzuweisungen hinzugefügt, um Einklang mit der heutigen Administratorerwartung aufrechtzuerhalten. Wenn Sie nicht möchten, dass ein Administrator Intune-Objekte mit der Standardbereichsmarkierung sehen kann, entfernen Sie die Standardbereichsmarkierung aus der Rollenzuweisung. Diese Features ähnelt dem Feature für Sicherheitsbereiche in System Center Configuration Manager. Weitere Informationen finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Unterstützung für die Registrierung eines Android-Geräteadministrators <!-- 4869749   -->
Die Registrierungsoption „Android-Geräteadministrator“ wurde der Seite „Android-Registrierung“ hinzugefügt (**Intune** > **Geräteregistrierung** > **Android-Registrierung**). „Android-Geräteadministrator“ ist weiterhin standardmäßig für alle Mandanten aktiviert.  Weitere Informationen finden Sie unter [Android-Geräteadministratorregistrierung](android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Überspringen weiterer Bildschirme im Setup-Assistenten <!--4877451  -->
Sie können „Programm zur Geräteregistrierung“-Profile so festlegen, dass die folgenden Bildschirme des Setup-Assistenten übersprungen werden:
- Für iOS
    - Darstellung
    - Express-Sprache
    - Bevorzugte Sprache
    - Migration von Gerät zu Gerät
- Für macOS
    - Bildschirmzeit
    - Touch ID-Setup

Weitere Informationen zur Anpassung des Setup-Assistenten finden Sie unter [Erstellen eines Apple-Registrierungsprofils für iOS](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) und [Erstellen eines Apple-Registrierungsprofils für macOS](device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Hinzufügen einer Benutzerspalte zum CSV-Upload für AutoPilot-Geräte <!-- 3823054 -->
Sie können jetzt eine Benutzerspalte zum CSV-Upload für AutoPilot-Geräte hinzufügen. Hiermit können Sie Benutzer massenweise beim Importieren der CSV-Datei zuweisen. Das neue Format für die Zeilen in der CSV-Datei sieht wie folgt aus: „serial-number“, „windows-product-id“, „hardware-hash“, „optional-group-tag“, „optional-assigned-user“. Weitere Informationen finden Sie unter [Registrieren von Windows-Geräten in Intune mithilfe von Windows Autopilot](enrollment-autopilot.md).


### <a name="device-management"></a>Geräteverwaltung

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Konfigurieren des Zeitlimits für automatische Gerätebereinigung auf 30 Tage <!--4231059  -->
Sie können das Zeitlimit für automatische Gerätebereinigung auf 30 Tage als kürzesten Zeitraum (statt des vorherigen Limits von 90 Tagen) nach der letzten Anmeldung festlegen. Navigieren Sie dafür zu **Intune** > **Geräte** > **Setup** > **Gerätebereinigungsregeln**.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Buildnummer auf „Hardware“-Seite eines Android-Geräts enthalten <!-- 4461910   -->
Ein neuer Eintrag auf der „Hardware“-Seite für jedes Android-Gerät enthält die Buildnummer des Betriebssystems des Geräts. Weitere Informationen finden Sie unter [Anzeigen von Gerätedetails in Intune](device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Woche vom 5. August 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies ist ein unterstützter OEM für OEMConfig auf Android Enterprise-Geräten  <!-- 4843713 -->

In Intune können Sie Gerätekonfigurationsprofile erstellen und Einstellungen auf Android Enterprise-Geräte mit OEMConfig anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **OEMConfig** für Profiltyp).

In diesem Update ist Zebra Technologies ein unterstützter OEM (Original Equipment Manufacturer) für OEMConfig. Weitere Informationen zu OEMConfig finden Sie unter [Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig](android-oem-configuration-overview.md).

Gilt für:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>Woche vom 22. Juli 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>Angepasste Benachrichtigungen für Benutzer und Gruppen    <!-- 16766574          -->
Senden Sie benutzerdefinierte Pushbenachrichtigungen aus der Unternehmensportalanwendung an Benutzer auf iOS- und Android-Geräten, die Sie mit Intune verwalten. Diese mobilen Pushbenachrichtigungen bieten mit Freitext umfassende Anpassungsmöglichkeiten und können für beliebige Zwecke verwendet werden. Sie können Sie auf verschiedene Benutzergruppen in Ihrer Organisation ausrichten. Weitere Informationen finden Sie im Artikel zu [benutzerdefinierte Benachrichtigungen](custom-notifications.md).

#### <a name="googles-device-policy-controller-app----3041950----"></a>Device Policy Controller-App von Google <!-- 3041950  -->
Mit der App „Managed Home Screen“ ist nun der Zugriff auf die Android Device Policy-App von Google möglich. Die App „Managed Home Screen“ ist ein benutzerdefiniertes Startprogramm, das für Geräte verwendet wird, die bei Intune als dedizierte Android Enterprise-Geräte (AE) registriert sind und den Kioskmodus mit mehreren Apps verwenden. Zu Unterstützungs- und Debugzwecken können Sie auf die Android Device Policy-App zugreifen oder Benutzer auf diese weiterleiten. Diese Startfunktion ist verfügbar, sobald das Gerät registriert wird und sich bei der App „Managed Home Screen“ einloggt. Für diese Funktion sind keine weiteren Installationen nötig.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>Outlook-Sicherheitseinstellungen für iOS- und Android-Geräte <!-- 3212619 -->
Sie können jetzt sowohl allgemeine App-Einstellungen als auch Einstellungen für die Datenschutzkonfiguration für Outlook für iOS und Android über einfache Intune-Administratorsteuerung ohne Geräteregistrierung konfigurieren. Die allgemeinen App-Konfigurationseinstellungen bieten Parität mit den Einstellungen, die Administratoren bei der Verwaltung von Outlook für iOS und Android auf registrierten Geräten aktivieren können. Weitere Informationen über Outlook-Einstellungen finden Sie unter [Bereitstellen von Outlook für iOS und Android App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Verwenden von „Anwendbarkeitsregeln“ beim Erstellen von Windows 10-Gerätekonfigurationsprofilen <!-- 2549910 eeready   idstaged -->

Sie können Windows 10-Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** (Plattform) > **Anwendbarkeitsregeln**). Mit diesem Update können Sie eine **Anwendbarkeitsregel** so erstellen, dass das Profil nur für eine bestimmte Edition oder Version gilt. Sie können beispielsweise ein Profil erstellen, das einige BitLocker-Einstellungen aktiviert. Sobald Sie das Profil hinzugefügt haben, aktivieren Sie eine Anwendbarkeitsregel, damit das Profil nur für Geräte mit Windows 10 Enterprise gilt.

Informationen zum Hinzufügen einer Anwendbarkeitsregel finden Sie unter [Anwendbarkeitsregeln](device-profile-create.md#applicability-rules).

Gilt für: Windows 10 und höher

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>Verwenden Sie Token, um gerätespezifische Informationen in benutzerdefinierten Profilen für iOS- und macOS-Geräte hinzuzufügen. <!-- 3330008  -->
Sie können benutzerdefinierte Profile auf iOS- und macOS-Geräten verwenden, um Einstellungen und Funktionen zu konfigurieren, die nicht in Intune integriert sind (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** oder **macOS** (Plattform) > **Benutzerdefiniert** (Profiltyp)). Mit diesem Update können Sie Ihren `.mobileconfig`-Dateien Token hinzufügen, um gerätespezifische Informationen hinzuzufügen. Sie können beispielsweise `Serial Number: {{serialnumber}}` zu Ihrer Konfigurationsdatei hinzufügen, um die Seriennummer des Geräts anzuzeigen.

Informationen zum Erstellen eines benutzerdefinierten Profils finden Sie unter [Benutzerdefinierte iOS-Einstellungen](custom-settings-ios.md) oder [Benutzerdefinierte macOS-Einstellungen](custom-settings-macos.md).

Gilt für:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Neuer Konfigurations-Designer beim Erstellen eines OEMConfig-Profils für Android Enterprise <!-- 3712769   -->
In Intune können Sie ein Gerätekonfigurationsprofil erstellen, das eine OEMConfig-App verwendet (Gerätekonfiguration > Profile > Profil erstellen > Android Enterprise (Plattform) > OEMConfig (Profiltyp)). Dadurch öffnet sich ein JSON-Editor mit einer Vorlage und Werten, die Sie ändern können. 

Dieses Update enthält einen Konfigurations-Designer mit verbesserter Benutzerfreundlichkeit, der in die App eingebettete Details wie Titel, Beschreibungen und mehr anzeigt. Der JSON-Editor ist weiterhin verfügbar und zeigt alle Änderungen an, die Sie im Konfigurations-Designer vornehmen.

Informationen zu den aktuellen Einstellungen finden Sie unter [Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig](android-oem-configuration-overview.md).

Gilt für: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Aktualisierte Benutzeroberfläche für die Konfiguration von Windows Hello  <!-- 4089576            -->
Wir haben die Konsole aktualisiert, in der Sie [Intune für die Verwendung von Windows Hello for Business konfigurieren](windows-hello.md). Alle Konfigurationseinstellungen sind nun im gleichen Bereich der Konsole verfügbar, in dem Sie die Unterstützung für Windows Hello aktivieren. 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
Das Intune PowerShell SDK, das die Intune-API über Microsoft Graph unterstützt, wurde auf Version 6.1907.1.0 aktualisiert. Das SDK unterstützt jetzt folgende Optionen:
- Arbeitet mit Azure Automation.
- Unterstützt Lesevorgänge, die nur für die Anwendungsauthentifizierung gelten. 
- Unterstützt benutzerfreundliche verkürzte Namen als Aliase.
- Entspricht den PowerShell-Benennungskonventionen. Insbesondere wurde der Parameter `PSCredential` (im Cmdlet `Connect-MSGraph`) in `Credential` umbenannt.
- Unterstützt die manuelle Angabe des Wertes des Headers `Content-Type` bei Verwendung des Cmdlets `Invoke-MSGraphRequest`.

Weitere Informationen finden Sie unter [PowerShell SDK für Microsoft Intune Graph-API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>Updates für Registrierungseinschränkungen  <!-- 2871968 -->
Die Registrierungseinschränkungen für neue Mandanten wurden aktualisiert, sodass Android Enterprise-Arbeitsprofile standardmäßig zulässig sind. Für vorhandene Mandanten ergeben sich keine Änderungen. Um die Arbeitsprofile von Android Enterprise verwenden zu können, müssen Sie Ihr [Intune-Konto noch mit Ihrem verwalteten Google Play-Konto verbinden](https://docs.microsoft.com/intune/connect-intune-android-enterprise).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Aktualisierungen der Benutzeroberfläche für die Apple-Registrierung und Registrierungseinschränkungen <!--4089575, 4089579  -->
Die beiden folgenden Prozesse verwenden eine Benutzeroberfläche im Assistentenstil:
- Apple-Geräteregistrierung. Weitere Informationen finden Sie unter [Automatisches Registrieren von iOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](device-enrollment-program-enroll-ios.md).
- Erstellung einer Registrierungseinschränkung. Weitere Informationen finden Sie unter [Festlegen von Registrierungseinschränkungen](enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Behandeln von Vorkonfigurationen von Unternehmensgerätebezeichern für Android Q-Geräte <!-- 4711509  idmiss -->
In Android Q (v10) entfernt Google die Möglichkeit für MDM-Agents auf älteren verwalteten (Geräteadministrator) Android-Geräten, um Informationen zum Gerätebezeichner zu erfassen.  Intune bietet ein Feature, mit dem IT-Administratoren eine [Liste von Geräteseriennummern oder IMEIs vorkonfigurieren können](https://docs.microsoft.com/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number), um diese Geräte automatisch als unternehmenseigen zu kennzeichnen. Dieses Feature funktioniert nicht für Android Q-Geräte, die vom Geräteadministrator verwaltet werden.  Unabhängig davon, ob die Seriennummer oder die IMEI für das Gerät hochgeladen wird, wird sie bei der Intune-Anmeldung immer als persönlich betrachtet.  Sie können die Angaben zum Besitzer nach der Registrierung manuell auf das Unternehmen umstellen.  Dies betrifft nur neue Registrierungen, bestehende registrierte Geräte sind nicht betroffen.  Android-Geräte, die mit Arbeitsprofilen verwaltet werden, sind von dieser Änderung nicht betroffen und arbeiten weiterhin wie bisher.  Darüber hinaus können Android Q-Geräte, die als Geräteadministrator registriert sind, die Seriennummer oder IMEI in der Intune-Konsole nicht mehr als Geräteeigenschaften melden.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Die Symbole für Android Enterprise-Registrierungen haben sich geändert (Arbeitsprofil, dedizierte Geräte sowie vollständig verwaltete Geräte). <!-- 4977730 -->
Die Symbole für Android Enterprise-Registrierungsprofile wurden geändert. Zum Anzeigen der neuen Symbole gehen Sie zu **Intune** > **Registrierungen** > **Android-Registrierungen** > **Registrierungsprofile**.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Änderung bezüglich der Windows-Diagnosedatensammlung <!-- 4113859 -->
Der Standardwert für die Diagnosedatensammlung hat sich für Geräte mit Windows 10, Version 1903 und höher, geändert. Ab Windows 10 Version 1903 ist die Sammlung von Diagnosedaten standardmäßig aktiviert. Windows-Diagnosedaten sind wichtige technische Daten von Windows-Geräten über das Gerät und die Funktionsweise von Windows und der zugehörigen Software. Weitere Informationen finden Sie unter [Konfigurieren von Windows-Diagnosedaten in Ihrer Organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Autopilotgeräte verwenden auch in die „Vollständige“ Telemetrie, sofern im Autopilotprofil mit [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) nichts anderes festgelegt ist.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="improve-device-location---3855417----"></a>Gerätestandort verbessern<!-- 3855417  -->
Mithilfe der Aktion **Gerät suchen** können Sie die exakten Koordinaten eines Geräts vergrößern. Weitere Informationen zum Auffinden verlorener IOS-Geräte finden Sie unter [Suchen von verlorenen iOS-Geräten](device-locate.md).


### <a name="device-security"></a>Gerätesicherheit

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Erweiterte Einstellungen für Windows Defender-Firewall (öffentliche Vorschauversion)  <!--  1311949     -->  
Verwenden Sie Intune, um [benutzerdefinierte Firewallregeln als Teil eines Gerätekonfigurationsprofils](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) für Endpoint Protection unter Windows 10 zu verwalten. Regeln können das Eingangs- und Ausgangsverhalten von Anwendungen, Netzwerkadressen und Ports festlegen. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>Aktualisierte Benutzeroberfläche für die Verwaltung von Sicherheitsbaselines   <!-- 4091125     -->
Wir haben die [Erstellung und Bearbeitung](security-baselines.md#create-the-profile) in der Intune-Konsole für unsere Sicherheitsbaselines aktualisiert. Die Änderungen umfassen:

Ein einfacheres Format im Assistentenstil, das zu einem einzigen Blatt zusammengefasst wurde. Dank dieses neuen Designs müssen IT-Experten nicht mehr auf mehreren Blättern arbeiten und einen Drilldown in mehrere separate Bereiche ausführen.  
Sie können nun Zuweisungen als Teil des Erstellungs- und Bearbeitungsprozesses erstellen, anstatt später zurückkehren zu müssen, um Baselines zuzuweisen. Wir haben eine Zusammenfassung der Einstellungen hinzugefügt, die Sie vor der Erstellung einer neuen Baseline und bei der Bearbeitung einer bestehenden anzeigen können. Beim Bearbeiten zeigt die Zusammenfassung nur die Liste der Elemente an, die in der einen Kategorie der zu bearbeitenden Eigenschaften festgelegt sind.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Woche vom 15. Juli 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Symbole für „Managed Home Screen“ und verwaltete Einstellungen <!-- 4918107 -->
Das Symbol für die App „Managed Home Screen“ und für die **verwalteten Einstellungen** wurde aktualisiert. Die App „Managed Home Screen“ wird nur von Geräten verwendet, die bei Intune als dedizierte Android Enterprise-Geräte (AE) registriert sind und im Kioskmodus mit mehreren Apps ausgeführt werden. Weitere Informationen über die App „Managed Home Screen“ finden Sie unter [Konfigurieren der Managed Home Screen-App von Microsoft für Android Enterprise](app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android Device Policy auf dedizierten Android Enterprise-Geräten <!-- 4918136 -->
Die Android Device Policy-Anwendung kann über den Debugbildschirm der App „Managed Home Screen“ aufgerufen werden. Die App „Managed Home Screen“ wird nur von Geräten verwendet, die bei Intune als dedizierte Android Enterprise-Geräte (AE) registriert sind und im Kioskmodus mit mehreren Apps ausgeführt werden. Weitere Informationen finden Sie unter [Konfigurieren der Managed Home Screen-App von Microsoft für Android Enterprise](app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates----3902931---"></a>Aktualisierungen des iOS-Unternehmensportals <!-- 3902931 -->
Ihr Unternehmensname in den Verwaltungsaufforderungen der iOS-App ersetzt den aktuellen Text „i.manage.microsoft.com“. Beispielsweise sehen Benutzer ihren Unternehmensnamen anstelle von „i.manage.microsoft.com“, wenn sie versuchen, eine iOS-App aus dem Unternehmensportal zu installieren, oder wenn sie die Verwaltung der App erlauben. Diese Neuerung wird in den nächsten Tagen für alle Kunden eingeführt.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>Verwalten von FileVault für macOS   <!--  3858502 + 4557986 + 1210104  -->
Mit Intune können Sie die [FileVault-Verschlüsselung für MacOS-Geräte verwalten](encrypt-devices.md). Zum Verschlüsseln von Geräten verwenden Sie ein Profil für die Endpoint Protection-Gerätekonfiguration.

Unsere Unterstützung für FileVault umfasst die Verschlüsselung unverschlüsselter Geräte, das Hinterlegen eines persönlichen Wiederherstellungsschlüssels, die automatische oder manuelle Rotation von persönlichen Verschlüsselungsschlüsseln und das Abrufen von Schlüsseln für Ihre Unternehmensgeräte. Endbenutzer können auch die Website des Unternehmensportals nutzen, um den persönlichen Wiederherstellungsschlüssel für ihre verschlüsselten Geräte zu erhalten. 

Wir haben den Verschlüsselungsbericht neben Informationen zu BitLocker auch mit [Informationen zu FileVault](encryption-monitor.md) ergänzt, sodass Sie alle Verschlüsselungsdetails Ihrer Geräte zentral anzeigen können. 

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>Die Windows Autopilot-Zurücksetzung entfernt den primären Benutzer des Geräts <!-- 4156123 -->
Bei der Verwendung der Autopilot-Zurücksetzung auf einem Gerät, wird dessen primäre Benutzer entfernt. Der nächste Benutzer, der sich nach dem Zurücksetzen anmeldet, wird als primärer Benutzer festgelegt. Dieses Feature wird in den nächsten Tagen für alle Kunden eingeführt.

## <a name="week-of-july-8-2019"></a>Woche vom 8. Juli 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Neue Office-, Windows- und OneDrive-Einstellungen in administrativen Vorlagen für Windows 10 <!-- 3510695 -->

Sie können in Intune Verwaltungsvorlagen erstellen, die die Gruppenrichtlinienverwaltung vor Ort nachahmen (**Geräteverwaltung** > **Profile** > **Profil** > **Windows 10 und höher** (Plattform) > **Administrationsvorlage** (Profiltyp)).

Dieses Update enthält weitere Office-, Windows- und OneDrive-Einstellungen, die Sie Ihren Vorlagen hinzufügen können. hinzufügen können. Mit diesen neuen Einstellungen können Sie jetzt über 2.500 Einstellungen konfigurieren, die zu vollständig cloudbasiert sind.

Weitere Informationen zu diesem Feature finden Sie unter [Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Microsoft Intune](administrative-templates-windows.md).

Gilt für: Windows 10 und höher

## <a name="week-of-july-1-2019"></a>Woche vom 1. Juli 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>AAD und APP auf Android Enterprise-Geräten <!-- 3574267 -->
Beim Onboarding vollständig verwalteter Android Enterprise-Geräte registrieren sich Benutzer jetzt bei der ersten Einrichtung Ihres neuen oder auf Werkseinstellungen zurückgesetzten Geräts bei Azure Active Directory (AAD). Bisher musste der Benutzer bei einem vollständig verwalteten Gerät nach Abschluss der Einrichtung die Microsoft Intune-App manuell starten, um die AAD-Registrierung zu beginnen. Wenn der Benutzer jetzt nach der ersten Einrichtung zur Startseite des Geräts gelangt, ist das Gerät sowohl registriert als auch angemeldet.

Zusätzlich zu den AAD-Updates werden die Intune-App-Schutzrichtlinien (APP) jetzt auf vollständig verwalteten Android-Unternehmensgeräten unterstützt. Diese Funktionalität wird mit dem Rollout verfügbar. Weitere Informationen finden Sie unter [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](apps-add-android-for-work.md).

## <a name="week-of-june-24-2019"></a>Woche vom 24. Juni 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Konfigurieren, welche Browser zu Unternehmensdaten verlinken dürfen <!-- 3145939 -->
Intune-Schutzrichtlinien für Apps für Android- und iOS-Geräte ermöglichen Ihnen jetzt die Übertragung von Unternehmensweblinks an einen spezifischen anderen Browser als Intune Managed Browser oder Microsoft Edge.  Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Die Seite „Alle Apps“ zeige Online-/Offline-Apps aus dem Microsoft Store für Unternehmen an<!--4089647 -->
Die Seite **Alle Apps** enthält nun eine Kennzeichnung, um Anwendungen im Microsoft Store für Unternehmen (MSFB) als Online- oder Offlineanwendungen zu identifizieren. Jede MSFB-App erhält jetzt ein Suffix für **Online** oder **Offline**. Die App-Detailseite enthält auch Informationen zu **Lizenztyp** und **Unterstützung der Gerätekontextinstallation** (nur offline lizenzierte Apps).

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Unternehmensportal-App auf freigegebenen Windows-Geräten <!--4393553 -->
Benutzer können nun auf freigegebenen Windows-Geräten auf die Unternehmensportal-App zugreifen. Den Endbenutzern wird auf der Gerätekachel jetzt die Kennzeichnung **Freigegeben** angezeigt. Dies gilt für die Windows-Unternehmensportal-App Version 10.3.45609.0 und höher.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>Anzeigen aller installierten Apps auf der neuen Unternehmensportal-Webseite <!-- 4224326 -->
Auf der neuen Seite **Installierte Apps** der Unternehmensportalwebsite werden alle verwalteten Apps (sowohl erforderliche als auch verfügbare) aufgeführt, die auf den Geräten eines Benutzers installiert sind. Neben dem Zuweisungstyp können Benutzer auch den Herausgeber, das Veröffentlichungsdatum und den aktuellen Installationsstatus der Apps sehen. Wenn Sie keine Apps für Ihre Benutzer als erforderlich oder verfügbar eingerichtet haben, erhalten sie die Meldung, dass keine Unternehmens-Apps installiert wurden. Die neue Webseite finden Sie, indem Sie die [Unternehmensportalwebsite](https://portal.manage.microsoft.com) aufrufen und auf **Installierte Apps** klicken.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>Mit der neuen Ansicht können Benutzer alle verwalteten Apps sehen, die auf einem Gerät installiert sind <!-- 2352913 -->  
In der Unternehmensportal-App für Windows werden nun alle verwalteten (sowohl erforderlichen als auch verfügbaren) Apps aufgelistet, die auf dem Gerät eines Benutzers installiert sind. Benutzer können versuchte und ausstehende App-Installationen sowie deren aktuellen Status einsehen. Wenn Sie keine Apps für Ihre Benutzer als erforderlich oder verfügbar eingerichtet haben, erhalten sie die Meldung, dass keine Unternehmens-Apps installiert wurden. Die neue Ansicht finden Sie im Navigationsbereich des Unternehmensportals unter **Apps** > **Installierte Apps**.    

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Konfigurieren von Einstellungen für Kernelerweiterungen auf macOS-Geräten <!-- 2043024 -->
Sie können auf macOS-Geräten ein Gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** (Plattform)). Dieses Update enthält weitere Einstellungen, die Sie zum Konfigurieren und Verwenden von Kernelerweiterungen auf Ihren Geräten verwenden können. Sie können bestimmte Erweiterungen hinzufügen oder alle Erweiterungen von einem bestimmten Partner oder Entwickler zulassen.

Weitere Informationen zu diesem Feature finden Sie in der [Übersicht zu Kernelerweiterungen](kernel-extensions-overview-macos.md) und in den [Einstellungen für die Kernelerweiterung](kernel-extensions-settings-macos.md).

Gilt für: macOS 10.13.2 und höher

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>Weitere Konfigurationsoptionen für die Einstellung „Apps from the store only“ (Nur Apps aus dem Store) für Windows 10-Geräte <!-- 2697002 -->
Wenn Sie ein Geräteeinschränkungsprofil für Windows-Geräte erstellen, können Sie die Einstellung **Apps from the store only** (Nur Apps aus dem Store) verwenden, damit Benutzer nur Apps aus dem Microsoft Store installieren können (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Diese Einstellung wird in diesem Update mit weiteren Optionen erweitert. 

Die neuen Einstellungen finden Sie unter [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](device-restrictions-windows-10.md#app-store).

Gilt für: Windows 10 und höher

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Bereitstellen mehrerer Zebra Mobility Extensions-Geräteprofile für ein Gerät, für dieselbe Benutzergruppe oder dieselbe Gerätegruppe <!-- 4089955 -->
Sie können Zebra Mobility Extensions (MX) in einem Gerätekonfigurationsprofil in Intune verwenden, um für Zebra-Geräte Einstellungen anzupassen, die nicht in Intune integriert sind. Derzeit können Sie ein Profil für ein einzelnes Gerät bereitstellen. In diesem Update können Sie mehrere Profile für Folgendes bereitstellen:
- für dieselbe Benutzergruppe
- für dieselbe Gerätegruppe
- für ein einzelnes Gerät

Unter [Nutzen und Verwalten von Zebra-Geräten mithilfe von Zebra Mobility Extensions in Microsoft Intune](android-zebra-mx-overview.md) wird die Verwendung von MX in Intune veranschaulicht.

Gilt für: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Für einige Kioskeinstellungen auf iOS-Geräten wird „Blockieren“ anstelle von „Zulassen“ verwendet. <!-- 4404075  -->
Beim Erstellen eines Geräteeinschränkungsprofils für iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Kiosk**) legen Sie die **Automatische Sperre**, den **Ruftonschalter**, die **Automatische Ausrichtung**, die **Standbytaste** und die **Lautstärkeregler** fest. 

Diese Werte sind in diesem Update **Blockieren** (blockiert das Feature) und **Nicht konfiguriert** (lässt das Feature zu). Die Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#kiosk-supervised-only). 

Gilt für: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>Verwenden von Face ID für die Kennwortauthentifizierung auf iOS-Geräten <!-- 4490704 -->
Wenn Sie ein Geräteeinschränkungsprofil für iOS-Geräte erstellen, können Sie einen Fingerabdruck als Kennwort verwenden. In einem Update ermöglichen die Fingerabdruck-Kennworteinstellungen auch die Gesichtserkennung (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Kennwort**). Aus diesem Grund wurden die folgenden Einstellungen geändert:

- **Entsperrung durch Fingerabdruck** heißt nun **Touch ID und Face ID entsperren**.
- **Fingerabdruckänderung (nur überwacht)** heißt nun **Touch ID- und Face ID-Änderungen (nur überwacht)** .

Face ID ist ab iOS 11.0 verfügbar. Die Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#password).

Gilt für: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>Einschränken von Spiele- und App Store-Features auf iOS-Geräten ist jetzt von der Bewertungsregion abhängig <!-- 4593948 -->
Auf iOS-Geräten können Sie Features mit Bezug zu Spielen, dem App Store und dem Anzeigen von Dokumenten zulassen oder einschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **App Store, Dokumentanzeige, Spiele**). Sie können außerdem die Bewertungsregion auswählen, z. B. USA. 

In diesem Update ist das Feature **Apps** der **Bewertungsregion** untergeordnet und von der **Bewertungsregion** abhängig. Die Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gilt für: iOS

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>Windows Autopilot-Unterstützung für Azure AD Hybrid Join <!-- 4809146-->
Windows Autopilot für vorhandene Geräte unterstützt jetzt Azure AD Hybrid Join (zusätzlich zur vorhandenen Azure AD Join-Unterstützung). Gilt für Geräte mit Windows 10, Version 1809 und höher. Weitere Informationen finden Sie unter [Windows Autopilot für vorhandene Geräte](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).



### <a name="device-management"></a>Geräteverwaltung

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Anzeigen der Sicherheitspatchebene von Android-Geräten <!-- 4461911 -->
Sie können jetzt die Sicherheitspatchebene von Android-Geräten anzeigen. Klicken Sie hierzu auf **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Hardware**.
Die Patchebene ist im Abschnitt **Betriebssystem** aufgeführt.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Zuweisen von Bereichsmarkierungen zu allen verwalteten Geräten in einer Sicherheitsgruppe <!-- 3173810 -->
Sie können jetzt einer Sicherheitsgruppe Bereichsmarkierungen zuweisen. Die Bereichsmarkierungen werden allen Geräten in dieser Sicherheitsgruppe zugewiesen. Die Bereichsmarkierung wird allen Geräten in diesen Gruppen zugewiesen. Bereichsmarkierungen, die mit diesem Feature festgelegt werden, überschreiben die Bereichsmarkierungen, die mit der aktuellen Vorgehensweise zugewiesen wurden. Weitere Informationen finden Sie unter [Verwenden der RBAC und von Bereichsmarkierungen für eine verteilte IT](scope-tags.md).

### <a name="device-security"></a>Gerätesicherheit

#### <a name="use-keyword-search-with-security-baselines-------"></a>Verwenden der Schlüsselwortsuche mit Sicherheitsbaselines <!--  -->
Wenn Sie [Sicherheitsbaselineprofile](security-baselines.md#create-the-profile) erstellen oder bearbeiten, können Sie in der neuen *Suchleiste* Schlüsselwörter angeben, um die verfügbaren Einstellungsgruppen nach denen zu filtern, die Ihre Suchkriterien enthalten. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>Das Sicherheitsbaselinefeatures ist jetzt allgemein verfügbar  <!-- 3785395 -->
Die Vorschauphase des **Sicherheitsbaselinefeatures** ist vorbei. Das Feature ist jetzt allgemein verfügbar (GA).  Dies bedeutet, dass das Feature jetzt in der Produktion eingesetzt werden kann. Die einzelnen Basislinienvorlagen können jedoch in der Vorschauphase verbleiben und werden ausgewertet und nach eigenen Zeitplänen an die allgemeine Verfügbarkeit freigegeben.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>Die MDM-Sicherheitsbaselinevorlage ist jetzt allgemein verfügbar   <!-- 3794072, 4217151,  3534649 -->
Die Vorschauphase der MDM-Sicherheitsbaselinevorlage ist vorbei. Das Feature ist jetzt allgemein verfügbar (GA). Die GA-Vorlage ist mit **MDM-Sicherheitsbaseline für Mai 2019** gekennzeichnet.  Dies ist eine neue Vorlage und kein Upgrade der Vorschauversion.  Da es sich um eine neue Vorlage handelt, müssen Sie die [darin enthaltenen Einstellungen](security-baseline-settings-windows.md) überprüfen und dann neue Profile erstellen, um die Vorlage auf Ihrem Gerät bereitzustellen. Andere Sicherheitsbaselinevorlagen können in der Vorschau verbleiben. Eine Liste der verfügbaren Baselines finden Sie unter [Verfügbare Sicherheitsbaselines](security-baselines.md#available-security-baselines).  

Die Vorlage *MDM-Sicherheitsbaseline für Mai 2019* ist nicht nur eine neue Vorlage, sondern enthält auch die beiden Einstellungen, die wir kürzlich in unserem Artikel „In Entwicklung“ angekündigt haben:  
- Sperrbildschirm: Per Sprache zu aktivierende App über einen Sperrbildschirm  
- DeviceGuard: Verwendet die virtualisierungsbasierte Sicherheit (VBS) beim nächsten Neustart von Geräten.  

Die *MDM-Sicherheitsbaseline für Mai 2019* beinhaltet auch mehrere neue Einstellungen, einige Einstellungen wurden entfernt und der Standardwert einer Einstellung wurde überarbeitet. Eine detaillierte Liste der Änderungen von Vorschau zu GA finden Sie unter **Was hat sich in der neuen Vorlage geändert?** .

#### <a name="security-baseline-versioning-----3194322---"></a>Versionsverwaltung für Sicherheitsbaselines  <!-- 3194322 -->
Sicherheitsbaselines für die Intune-Unterstützung der Versionsverwaltung. Mit dieser Unterstützung können Sie Ihre bestehenden Sicherheitsbaselineprofile aktualisieren, um die neuere Baselineversion zu verwenden, ohne eine neue Baseline von Grund auf neu erstellen und bereitstellen zu müssen, sobald neue Versionen der jeweiligen Sicherheitsbaseline veröffentlicht werden. Darüber hinaus können Sie in der Intune-Konsole Informationen über jede Baseline anzeigen, wie z.B. die Anzahl der einzelnen Profile, die die Baseline verwenden, wie viele der verschiedenen Baselineversionen von Ihren Profilen verwendet werden und wann die neueste Version einer bestimmten Sicherheitsbaseline veröffentlicht wurde.  Weitere Informationen finden Sie unter **Sicherheitsbaselines**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>Die Einstellung „Sicherheitsschlüssel zur Anmeldung verwenden“ wurde verschoben  <!-- 4501151 -->
Die Gerätekonfigurationseinstellung für Identity Protection mit dem Namen **Sicherheitsschlüssel zur Anmeldung verwenden** ist keine Untereinstellung mehr von *Windows Hello for Business konfigurieren*. Es handelt sich nun um eine Einstellung auf oberster Ebene, die immer verfügbar ist, auch wenn Sie die Verwendung von Windows Hello for Business nicht aktivieren. Weitere Informationen finden Sie unter [Identity Protection](identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>Neue Berechtigungen für zugewiesene Gruppenadministratoren   <!-- 4504437   -->
Die in Intune integrierte Rolle des Schuladministrators verfügt nun über CRUD-Berechtigungen (Create, Read, Update und Delete [Erstellen, Lesen, Aktualisieren und Löschen]) für verwaltete Apps. Dieses Update bedeutet, dass Sie, wenn Sie in Intune for Education als Gruppenadministrator zugewiesen sind, nun das iOS-MDM-Push-Zertifikat, die iOS-MDM-Servertoken und die iOS-VPP-Token zusammen mit [allen vorhandenen Berechtigungen](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions) erstellen, anzeigen, aktualisieren und löschen können. Um eine dieser Aktionen durchzuführen, gehen Sie zu **Mandanteneinstellungen** > **iOS-Geräteverwaltung**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>Anwendungen können die Graph-API verwenden, um Lesevorgänge ohne Benutzeranmeldeinformationen aufzurufen <!-- 4655885 -->
Anwendungen können Lesevorgänge der Intune-Graph-API mithilfe der App-Identität ohne Benutzeranmeldeinformationen aufrufen. Weitere Informationen zum Zugriff auf die Microsoft Graph-API für Intune finden Sie unter [Arbeiten mit Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>Anwenden von Bereichsmarkierungen für Apps aus dem Microsoft Store für Unternehmen <!-- 4392555 -->
Sie können jetzt Bereichsmarkierungen für Apps aus dem Microsoft Store für Unternehmen anwenden. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung (RBAC) und Bereichsmarkierungen für verteilte IT](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Woche vom 17. Juni 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="new-features-in-microsoft-intune-app"></a>Neue Features in der Microsoft Intune-App
Der Microsoft Intune-App (Preview) für Android wurden neue Features hinzugefügt. Benutzer mit vollständig verwalteten Android-Geräten haben jetzt folgende Möglichkeiten:  

* Sie können die Geräte anzeigen und verwalten, die sie über das Intune-Unternehmensportal oder die Microsoft Intune-App registriert haben.    
* Sie können sich an ihre Organisation wenden, um Unterstützung zu erhalten.    
* Sie können Feedback an Microsoft senden.    
* Sie können Geschäftsbedingungen anzeigen, sofern diese von ihrer Organisation festgelegt wurden.    

## <a name="week-of-june-10-2019"></a>Woche ab 10. Juni 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Neue Beispiel-Apps für die Intune SDK-Integration auf GitHub verfügbar <!-- 2653471 -->
Dem GitHub-Konto „msintuneappsdk“ wurden neue Beispielanwendungen für iOS (Swift), Android, Xamarin.iOS, Xamarin Forms und Xamarin.Android hinzugefügt. Diese Apps dienen zur Ergänzung unserer vorhandenen Dokumentation und veranschaulichen die Integration des SDK für die Intune-App in Ihre eigenen mobilen Apps. Wenn Sie App-Entwickler sind und weitere Unterstützung für das Intune SDK benötigen, sehen Sie sich die folgenden verknüpften Beispiele an:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): Eine native iOS-App (Swift) für Chats, die die Azure Active Directory-Authentifizierungsbibliothek (ADAL) für die vermittelte Authentifizierung verwendet.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): Eine native Android-App für Aufgabenlisten, die die ADAL für die vermittelte Authentifizierung verwendet.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): Eine Xamarin.Android-App für Aufgabenlisten, die die ADAL für die vermittelte Authentifizierung verwendet. Dieses Repository enthält auch die Xamarin.Forms-App.
- [Xamarin.iOS-Beispiel-App](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): Eine Barebone-Beispiel-App für Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Woche vom 27. Mai 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Berichterstellung über potenziell schädlichen Apps auf Android-Geräten <!-- 4223162 -->
Intune stellt jetzt zusätzliche Berichterstellungsinformationen über potenziell schädliche Apps auf Android-Geräten bereit. 

## <a name="week-of-may-20-2019"></a>Woche vom 20. Mai 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="windows-company-portal-app----3316993---"></a>Windows-Unternehmensportal-App <!-- 3316993 -->
Die Windows-Unternehmensportal-App enthält jetzt die neue Seite **Geräte**. Auf der Seite **Geräte** werden den Endbenutzern alle ihre registrierten Geräte angezeigt. Benutzer sehen diese Änderung im Unternehmensportal, wenn sie Version 10.3.4291.0 und höher verwenden. Informationen zum Konfigurieren des Unternehmensportals finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot-Gerät – Attributname „OrderID“ in „Gruppentag“ geändert <!-- 4659453 -->

Um die Aussagekraft zu erhöhen, wurde der Attributname **OrderID** bei Autopilot-Geräten in **Gruppentag** geändert. Wenn Sie Autopilot-Geräteinformationen über freigegebene Clustervolumen (CSVs) hochladen, müssen Sie „Gruppentag“ (und nicht „OrderID“) als Spaltenüberschrift verwenden.  

## <a name="week-of-may-13-2019"></a>Woche vom 13. Mai 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App  <!-- 1927359  -->
Bei Geräten, die bereits mithilfe des Setup-Assistenten über eine der Methoden von Apple für die Registrierung von Unternehmensgeräten registriert wurden, unterstützt Intune das Unternehmensportal nicht mehr, wenn es manuell von Endbenutzern aus dem App-Store installiert wurde. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Wenn Benutzer die Unternehmensportal-App aus dem App Store installieren und dann versuchen, diese Geräte darüber zu registrieren, erhalten sie eine Fehlermeldung. Es wird vorausgesetzt, dass diese Geräte die Unternehmensportal-App nur dann verwenden, wenn sie während der Registrierung von Intune mithilfe von Push automatisch übertragen wird. Registrierungsprofile in Intune im Azure-Portal werden aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Wenn Sie wünschen, dass Ihre DEP-Gerätebenutzer die Unternehmensportal-App verwenden, müssen Sie Ihre Einstellungen in einem Registrierungsprofil angeben. 

Darüber hinaus wird der Bildschirm **Gerät identifizieren** im iOS-Unternehmensportal entfernt. Deshalb müssen Administratoren, die den bedingten Zugriff aktivieren oder Unternehmens-Apps bereitstellen möchten, das DEP-Registrierungsprofil aktualisieren. Diese Anforderung gilt nur, wenn die DEP-Registrierung mit dem Setup-Assistenten authentifiziert wird. In diesem Fall müssen Sie die Unternehmensportal-App mithilfe von Push auf das Gerät übertragen. Wählen Sie dazu **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > anschließend ein Token > **Profile** > dann ein Profil und > **Eigenschaften** aus, und > legen Sie für **Unternehmensportal installieren** den Wert **Ja** fest.

Um die Unternehmensportal-App auf bereits registrierten DEP-Geräten zu installieren, müssen Sie zu „Intune“ > „Client-Apps“ wechseln und sie als verwaltete App mit App-Konfigurationsrichtlinien mithilfe von Push übertragen. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Konfigurieren, wie Endbenutzer eine LOB-App mithilfe einer App-Schutzrichtlinie aktualisieren können <!-- 3568384 -->
Sie können jetzt konfigurieren, wo Ihre Endbenutzer eine aktualisierte Version einer LOB-App (Line-of-Business-App, branchenspezifische App) erhalten können. Endbenutzer sehen diese Funktion im bedingten Startdialogfeld **App-Mindestversion**, in dem der Benutzer aufgefordert wird, auf eine Mindestversion der LOB-App zu aktualisieren. Sie müssen diese Updatedetails als Teil Ihrer LOB-App-Schutzrichtlinie (APP) angeben. Dieses Feature ist unter iOS und Android verfügbar. Unter iOS erfordert dieses Feature, dass die App integriert (oder mit dem Wrapping Tool umschlossen) und dafür das Intune SDK für iOS, V. 10.0.7 oder höher, verwendet wird. Unter Android wäre für dieses Feature die neueste Unternehmensportal-App erforderlich. Um zu konfigurieren, wie ein Endbenutzer eine LOB-App aktualisiert, muss eine verwaltete App-Konfigurationsrichtlinie mit dem Schlüssel `com.microsoft.intune.myappstore` an diese gesendet werden. Der gesendete Wert definiert, aus welchem Speicher der Endbenutzer die App herunterladen wird. Wenn die App über das Unternehmensportal bereitgestellt wird, muss der Wert `CompanyPortal` sein. Für alle anderen Speicher müssen Sie eine vollständige URL eingeben.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>PowerShell-Skripts zur Erweiterung der Intune-Verwaltung  <!-- 3734186  -->
Sie können PowerShell-Skripts so konfigurieren, dass sie mit Administratorrechten des Benutzers auf dem Gerät ausgeführt werden. Weitere Informationen finden Sie unter [Verwenden von PowerShell-Skripts auf Windows 10-Geräten in Intune](intune-management-extension.md) und [Win32-App-Verwaltung](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Verwaltung von Android Enterprise-Apps <!-- 4459905 -->
Um IT-Administratoren die Konfiguration und Nutzung der Android Enterprise-Verwaltung zu erleichtern, fügt Intune der Intune-Verwaltungskonsole automatisch vier gängige Android Enterprise-bezogene Apps hinzu. Die vier Android Enterprise-Apps sind wie folgt:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : für vollständig verwaltete Android Enterprise-Szenarien.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : hilft bei der Anmeldung bei Ihren Konten, wenn Sie die zweistufige Überprüfung verwenden.
- **[Intune-Unternehmensportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : wird für App Protection Policies (APP) und Szenarien mit Android Enterprise-Arbeitsprofilen genutzt.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : wird für dedizierte/Kioskszenarien mit Android Enterprise verwendet.

Bisher mussten IT-Administratoren diese Apps im [verwalteten Google Play Store](https://play.google.com/store/apps) als Teil des Setups manuell auffinden und genehmigen. Durch diese Änderung entfallen diese bislang manuellen Schritte, sodass Kunden die Android Enterprise-Verwaltung einfacher und schneller nutzen können.

Administratoren werden feststellen, dass diese vier Apps automatisch zur Liste ihrer Intune-Apps hinzugefügt wurden, wenn sie ihren Intune-Mandanten zum ersten Mal mit dem verwaltetem Google Play Store verbinden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto](connect-intune-android-enterprise.md). Für Mandanten, die ihren Mandanten bereits verbunden haben oder Android Enterprise bereits nutzen, gibt es keinerlei Administrationsaufwand. Diese vier Apps werden automatisch binnen 7 Tagen nach Abschluss des Dienstrollouts vom Mai 2019 verfügbar sein.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>PFX-Zertifikatconnector für Microsoft Intune aktualisiert  <!-- 1533038 -->
Wir haben ein Update zum [PFX-Zertifikatconnector für Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht, das ein Problem behebt, bei dem vorhandene PFX-Zertifikate weiter erneut verarbeitet werden. Dies führt dazu, dass der Connector die Verarbeitung neuer Anforderungen beendet.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Intune-Sicherheitsaufgaben für Defender ATP (in öffentlicher Vorschau)     <!-- 3208597 -->
In der öffentlichen Vorschau können Sie Intune verwenden, um [Sicherheitsaufgaben für Microsoft Defender Advanced Threat Protection (ATP)](atp-manage-vulnerabilities.md) zu verwalten. Diese Integration in ATP bietet einen risikobasierten Ansatz zur Erkennung, Priorisierung und Behebung von Schwachstellen und Fehlkonfigurationen an Endpunkten, wobei gleichzeitig die Zeitspanne zwischen Ermittlung und Risikominderung verkürzt wird.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie <!-- 3617671   idstaged-->
Viele Geräte unter Windows 10 und höher haben Chipsätze von Trusted Platform Module (TPM). Dieses Update enthält eine neue Konformitätseinstellung, die die Version des TPM-Chips auf dem Gerät überprüft. 

Unter [Richtlinieneinstellungen für Windows 10 und höher](compliance-policy-create-windows.md#device-security) wird diese Einstellung beschrieben.

Gilt für: Windows 10 und höher

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Hindern von Endbenutzern am Ändern ihres privaten Hotspots und Deaktivieren der Siri-Serverprotokollierung auf iOS-Geräten <!-- 4097904   -->  
Sie können auf einem iOS-Gerät ein Geräteeinschränkungsprofil einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). Dieses Update umfasst neue Einstellungen, die Sie konfigurieren können:

- **Integrierte Apps**: Serverseitige Protokollierung für Siri-Befehle
- **Drahtlos**: Benutzeränderung des persönlichen Hotspots (nur überwacht)

Zum Anzeigen dieser Einstellungen wechseln Sie zu [built-in app settings for iOS](device-restrictions-ios.md#built-in-apps) (Integrierte App-Einstellungen für iOS) und [wireless settings for iOS](device-restrictions-ios.md#wireless) (Drahtloseinstellungen für iOS).

Gilt für: iOS 12.2 und höher

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Neue Geräteeinschränkungseinstellungen für Classroom-App für macOS-Geräte <!-- 4097905   --> 
Sie können für macOS-Geräte Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). Dieses Update enthält neue Classroom-App-Einstellungen, die Option zum Sperren von Screenshots und die Option zum Deaktivieren der iCloud-Fotomediathek.

Die aktuellen Einstellungen finden Sie unter [macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-macos.md).

Gilt für: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Die iOS-Einstellung „Kennwort für Zugriff auf App Store“ wird umbenannt<!-- 4557891  -->
Die Einstellung **Kennwort für Zugriff auf App Store** wird umbenannt in **iTunes Store-Kennwort für alle Käufe erforderlich** (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für „Plattform“ > **Geräteeinschränkungen** für „Profiltyp“ > **App Store, Dokumentanzeige, Spiele**).

Zum Anzeigen der verfügbaren Einstellungen wechseln Sie zu [App Store, Dokumentanzeige, Spiele > iOS-Einstellungen](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gilt für: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender Advanced Threat Protection-Baseline (Vorschauversion)  <!--  3754134 -->
Wir haben eine Vorschauversion der Sicherheitsbaseline für [Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md)-Einstellungen hinzugefügt. Diese Baseline ist verfügbar, wenn Ihre Umgebung den Anforderungen zur Verwendung von [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) entspricht.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Statusseite für die Windows-Registrierung ist jetzt allgemein verfügbar <!-- 3605348 -->
Die Statusseite für die Registrierung ist jetzt in der Vorschauversion nicht mehr enthalten. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Update bei Intune-Benutzeroberfläche – Erstellung eines Autopilot-Registrierungsprofils  <!-- 4593669 -->
Die Benutzeroberfläche zum Erstellen eines Autopilot-Registrierungsprofils wurde aktualisiert und an die Stile von Azure-Benutzeroberflächen angepasst. Weitere Informationen finden Sie unter [Erstellen eines Autopilot-Registrierungsprofils](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile). Zukünftig werden weitere Intune-Szenarien auf diesen neuen Stil der Benutzeroberfläche aktualisiert.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>„Autopilot-Zurücksetzung aktivieren“ bei allen Windows-Geräten <!-- 4225665 -->
„Autopilot-Zurücksetzung aktivieren “ funktioniert jetzt bei allen Windows-Geräten – sogar denen, die nicht zur Verwendung der Statusseite für die Registrierung konfiguriert wurden. Wenn für ein Gerät bei der Erstregistrierung keine Statusseite für die Registrierung konfiguriert wurde, wechselt das Gerät nach der Anmeldung direkt zum Desktop. Es kann bis zu acht Stunden dauern, bis die Synchronisierung abgeschlossen ist und das Gerät in Intune als konform angezeigt wird. Weitere Informationen finden Sie unter [Reset devices with remote Windows Autopilot Reset (Zurücksetzen von Geräten mit Remote-Windows Autopilot-Zurücksetzung)](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Exaktes IMEI-Format beim Durchsuchen von „Alle Geräte“ nicht erforderlich <!--30407680 -->
Wenn Sie **Alle Geräte** durchsuchen, müssen Sie in IMEI-Nummern keine Leerzeichen einbeziehen.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Das Löschen eines Geräts im Apple-Portal wird im Intune-Portal widergespiegelt <!--2489996 -->
Wenn ein Gerät aus dem Programm zur Geräteregistrierung von Apple oder den Apple Business Manager-Portalen gelöscht wird, wird das Gerät bei der nächsten Synchronisierung automatisch aus Intune gelöscht.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>Die Nachverfolgung auf der Seite zum Registrierungsstatus umfasst jetzt Win32-Apps <!-- 2714451 -->
Dies gilt nur für Geräte mit Windows 10, Version 1903 und höher. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](windows-enrollment-status.md).

### <a name="device-management"></a>Geräteverwaltung

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Zurücksetzen von Geräten in einem Massenvorgang mithilfe der Graph-API <!-- 3295288 -->
Mithilfe der Graph-API können Sie jetzt in einem Massenvorgang bis zu 100 Geräte zurücksetzen.


### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Der Verschlüsselungsbericht ist in der öffentlichen Vorschau nicht mehr enthalten   <!-- 4587546      -->
Der [report for BitLocker and device encryption](encryption-monitor.md) (Bericht für BitLocker-Geräteverschlüsselung) ist jetzt allgemein verfügbar und nicht mehr Teil der öffentlichen Vorschau. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Outlook-Signatur und biometrische Einstellungen für iOS- und Android-Geräte <!-- 4050557 -->
Sie können jetzt angeben, ob die Standardsignatur in Outlook auf iOS- und Android-Geräten aktiviert ist. Darüber hinaus können Sie wählen, dass Benutzer die biometrische Einstellung in Outlook für iOS ändern dürfen.

## <a name="week-of-may-6-2019"></a>Woche vom 6. Mai 2019 

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>NAC-Unterstützung (Network Access Control, Netzwerkzugriffssteuerung) für F5 Access für iOS-Geräte <!-- 4500808 -->

F5 hat ein Update zu BIG-IP 13 veröffentlicht, dass NAC-Funktionalität für F5 Access unter iOS in Intune ermöglicht. Zur Nutzung dieses Features ist Folgendes erforderlich:

- Aktualisieren Sie BIG-IP auf 13.1.1.5. BIG-IP 14 wird nicht unterstützt.
- Integrieren Sie BIG-IP für NAC in Intune. Lesen Sie dazu die Schritte in [Übersicht: Konfigurieren von APM für Gerätestatusüberprüfungen mit Endpunktverwaltungssystemen](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Überprüfen Sie die Einstellung **Netzwerkzugriffssteuerung (NAC) aktivieren** im VPN-Profil in Intune.

Die verfügbaren Einstellungen finden Sie unter [Configure VPN settings on iOS devices (Konfigurieren von VPN-Einstellungen auf iOS-Geräten)](vpn-settings-ios.md).

Gilt für: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>PFX-Zertifikatconnector für Microsoft Intune aktualisiert <!-- doc-vso 1521237  -->  
Wir haben ein Update für den [PFX-Zertifikatconnector für Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht, wodurch das Abrufintervall von 5 Minuten auf 30 Sekunden verkürzt wird.

## <a name="week-of-april-22-2019"></a>Woche vom 22. April 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Verwenden des Compliance-Managers zum Erstellen von Bewertungen für Microsoft Intune<!-- 4404750 -->

Der [Compliance-Manager](https://servicetrust.microsoft.com/ComplianceManager) (Link öffnet eine andere Microsoft-Website) ist ein Workflow-basiertes Tool für die Risikobewertung in Microsoft Service Trust Portal. Mit dem Tool können Sie die Aktivitäten zur Einhaltung behördlicher Bestimmung Ihres Unternehmens im Bezug auf Microsoft-Diensten überwachen, zuweisen und überprüfen. Sie können Ihre eigene Bewertung der Konformität mit Office 365, Azure, Dynamics, Professional Services und Intune erstellen. Zwei Bewertungen sind in Intune verfügbar: FFIEC und DSGVO.

Der Compliance-Manager unterstützt Sie beim Aufteilen der Kontrollen: Kontrollen, die von Microsoft verwaltet werden und Kontrollen, die von Ihrer Organisation verwaltet werden. Sie können die Bewertungen abschließen und anschließend extrahieren und drucken.

Die Konformität mit [FFIEC (Federal Financial Institutions Examination Council)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (Link öffnet eine andere Microsoft-Website) umfasst mehrere Standards für Onlinebanking, die vom FFIEC erlassen wurden. Diese Bewertung ist die am häufigsten angeforderte Bewertung von Finanzinstituten, die Intune verwenden. Sie interpretiert, wie Intune die Konformität mit Cybersicherheitsrichtlinien des FFIEC für öffentliche Cloud-Workloads unterstützt. Die FFIEC-Bewertung von Intune ist die zweite FFIEC-Bewertung im Compliance-Manager.

Im folgenden Beispiel werden die FFIEC-Kontrollen aufgeschlüsselt. 64 Kontrollen werden von Microsoft verwaltet. Ihre Organisation ist für die restlichen 12 Kontrollen zuständig.

![Beispielbewertung für die FFIEC-Bewertung in Intune, einschließlich Kundenaktionen und Microsoft-Aktionen](./media/intune-ffiec-assessment-status.png)

Die [DSGVO (Datenschutz-Grundverordnung)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (Link öffnet eine andere Microsoft-Website) ist ein Gesetz der Europäischen Union (EU), das die Rechte von Personen und ihren Daten schützt. Die DSGVO-Bewertung ist die am häufigsten angeforderte Bewertung zur Unterstützung der Konformität mit Datenschutzbestimmungen. 

Im folgenden Beispiel werden die DSGVO-Kontrollen aufgeschlüsselt. 49 Kontrollen werden von Microsoft verwaltet. Ihre Organisation ist für die restlichen 66 Kontrollen zuständig.

![Beispielbewertung für die DSGVO-Bewertung in Intune, einschließlich Kundenaktionen und Microsoft-Aktionen](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Woche vom 15. April 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>OpenSSL-Verschlüsselung für Android-App-Schutzrichtlinien <!-- 3747362 -->
Intune-App-Schutzrichtlinien für Android-Geräte nutzen nun eine OpenSSL-Verschlüsselungsbibliothek, die FIPS 140-2-konform ist. Weitere Informationen finden Sie im Abschnitt [Verschlüsselung](app-protection-policy-settings-android.md#encryption) unter [Einstellungen für App-Schutzrichtlinien in Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Aktivieren von Win32-App-Abhängigkeiten <!-- 2617348  -->
Als Administrator können Sie voraussetzen, dass Apps als Abhängigkeiten installiert werden, bevor Ihre Win32-App installiert wird. Das heißt, das Gerät muss die abhängige(n) App(s) installieren, bevor die Win32-App installiert wird. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen. Wählen Sie **Windows-App (Win32)** als **App-Typ** aus. Nachdem Sie die App hinzugefügt haben, können Sie auf **Abhängigkeiten** klicken, um die abhängigen Apps hinzuzufügen, die installiert werden müssen, bevor die Win32-App installiert werden kann. Weitere Informationen finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Installationsinformationen zur App-Version für Apps im Microsoft Store für Unternehmen <!-- 3537391   -->
Berichte zur App-Installation enthalten Informationen zur App-Version für Apps im Microsoft Store für Unternehmen. Klicken Sie in Intune auf **Client-Apps** > **Apps**. Wählen Sie eine **App im Microsoft Store für Unternehmen** aus, und klicken Sie dann im Abschnitt **Überwachen** auf **Geräteinstallationsstatus**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Ergänzungen zu Anforderungsregeln für Win32-Apps <!-- 3676883   -->
Sie können Anforderungsregeln mithilfe von PowerShell-Skripts, Registrierungswerten und Dateisysteminformationen erstellen. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann **Windows-App (Win32)** als **App-Typ** auf dem Blatt **App hinzufügen** aus.  Klicken Sie auf **Anforderungen** > **Hinzufügen**, um zusätzliche Anforderungsregeln zu konfigurieren. Wählen Sie dann entweder **Dateityp**, **Registrierung** oder **Skript** als **Anforderungstyp** aus. Weitere Informationen finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](apps-win32-app-management.md).

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Konfigurieren von Win32-Apps für die Installation auf in Intune registrierten, in Azure AD eingebundenen Geräten <!-- 3695227  -->
Sie können Ihre Win32-Apps für die Installation auf in Intune registrierten, in Azure AD eingebundenen Geräten zuweisen. Weitere Informationen zu Win32-Apps in Intune finden Sie unter [Eigenständiges Intune – Win32-App-Verwaltung](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---3794259----"></a>Primärer Benutzer in der Geräteübersicht <!--3794259  -->
Die Seite „Geräteübersicht“ zeigt den primären Benutzer (Affinität zwischen Benutzer und Gerät) an. Klicken Sie auf **Intune** > **Geräte** > **Alle Geräte**, und wählen Sie dann ein Gerät aus, um den primären Benutzer eines Geräts anzuzeigen. Der primäre Benutzer wird außerdem oben auf der Seite **Übersicht** angezeigt.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Zusätzliche Berichterstellung für verwaltete Google Play-Apps für Android Enterprise-Arbeitsprofilgeräte <!-- 4105925  -->
Sie können die Versionsnummer von auf Android Enterprise-Arbeitsprofilgeräten bereitgestellten, verwalteten Google Play-Apps anzeigen. Dies gilt nur für erforderliche Apps.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Tastaturen von Drittanbietern für iOS <!-- 4111843   -->
Die Intune APP-Unterstützung (App Protection Policy, App-Schutzrichtlinie) für die Einstellung **Tastaturen von Drittanbietern** für iOS wird aufgrund einer Änderung an der iOS-Plattform beendet. Sie können diese Einstellung in der Intune-Verwaltungskonsole nicht mehr konfigurieren, und sie wird auf dem Client im Intune App SDK nicht mehr erzwungen.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Festlegen der Anmeldeeinstellungen und Steuern der Neustartoptionen für macOS-Geräte <!-- 1210083  -->
Sie können auf macOS-Geräten ein Gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **macOS** auswählen > **Gerätefunktionen**). Dieses Update umfasst neue Einstellungen im Fenster „Anmelden“, z. B. die Anzeige eines benutzerdefinierten Banners, die Auswahl der Anmeldemethode für Benutzer, das Anzeigen oder Ausblenden von Energieeinstellungen und mehr.

Informationen zu diesen Einstellungen finden Sie unter [macOS device feature settings in Intune (Einstellungen von macOS-Gerätefeatures)](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Konfigurieren von WLAN auf dedizierten Geräten im Multi-App-Kioskmodus für Android Enterprise-Gerätebesitzer <!--3041940  -->
Sie können die Einstellungen für Android Enterprise-Gerätebesitzer aktivieren, wenn das Gerät als dediziertes Gerät im Multi-App-Kioskmodus ausgeführt wird. Mit diesem Update können Sie Benutzern ermöglichen, WLAN-Netzwerke zu konfigurieren und Verbindungen mit diesen herzustellen (**Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp) > **Dedizierte Geräte** > **Kioskmodus**: **Multi-App** > **WLAN-Konfiguration**). 

Eine Liste aller konfigurierbaren Einstellungen finden Sie unter [Android Enterprise device settings to allow or restrict features (Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-android-for-work.md).

Gilt für: Dedizierte Android Enterprise-Geräte im Multi-App-Kioskmodus


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Konfigurieren von Bluetooth und Kopplung auf dedizierten Geräten im Multi-App-Kioskmodus für Android Enterprise-Gerätebesitzer <!-- 3041941  -->
Sie können die Einstellungen für Android Enterprise-Gerätebesitzer aktivieren, wenn das Gerät als dediziertes Gerät im Multi-App-Kioskmodus ausgeführt wird. Mit diesem Update können Sie Benutzern ermöglichen, Bluetooth zu aktivieren und Geräte per Bluetooth zu koppeln (**Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp) > **Dedizierte Geräte** > **Kioskmodus**): **Multi-App** > **Bluetooth-Konfiguration**). 

Eine Liste aller konfigurierbaren Einstellungen finden Sie unter [Android Enterprise device settings to allow or restrict features (Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-android-for-work.md).

Gilt für: Dedizierte Android Enterprise-Geräte im Multi-App-Kioskmodus

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Erstellen und Verwenden von OEMConfig-Gerätekonfigurationsprofilen in Intune <!-- 3305883  -->
Mit diesem Update unterstützt Intune die Konfiguration von Android Enterprise-Geräten mit OEMConfig. Das heißt, Sie können ein Gerätekonfigurationsprofil erstellen und Einstellungen auf Android Enterprise-Geräte mit OEMConfig anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform)).

Die Unterstützung wird derzeit auf einer pro-OEM-Basis bereitgestellt. Wenden Sie sich an `IntuneOEMConfig@microsoft.com`, wenn eine OEMConfig-App, die Sie benötigen, nicht in der Liste von OEMConfig-Apps verfügbar ist.

Weitere Informationen zu diesem Feature finden Sie unter [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune (Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig in Microsoft Intune)](android-oem-configuration-overview.md).

Gilt für: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows Update-Benachrichtigungen  <!-- 3316758, 3316782  -->
Wir haben den Windows Update-Ringkonfigurationen zwei *Einstellungen für die Benutzeroberfläche* hinzugefügt, die Sie über die Intune-Konsole verwalten können. Sie können nun:
- Benutzern erlauben oder verweigern, [nach Windows-Updates zu suchen](windows-update-settings.md).
- die [Windows Update-Benachrichtigungsebene](windows-update-settings.md) verwalten, die Benutzern angezeigt wird.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Neue Einstellungen zur Geräteeinschränkung für Android Enterprise-Gerätebesitzer <!-- 3574254  -->
Sie können ein Geräteeinschränkungsprofil auf Android Enterprise-Geräten erstellen, um Features zuzulassen oder einzuschränken, Kennwortregeln festzulegen und mehr (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer > Geräteeinschränkungen** (Profiltyp)). 

Dieses Update umfasst neue Kennworteinstellungen, ermöglicht Vollzugriff auf Apps im Google Play Store für vollständig verwaltete Geräte und mehr. Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](device-restrictions-android-for-work.md). 

Gilt für: Vollständig verwaltete Android Enterprise-Geräte

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie <!-- 3617671 -->

Die Bereitstellung dieses Features verzögert sich und ist in einem zukünftigen Release geplant.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Änderungen der Benutzeroberfläche für den Microsoft Edge-Browser auf Geräten mit Windows 10 und höher <!-- 3775833   -->
Wenn Sie ein Gerätekonfigurationsprofil erstellen, können Sie Microsoft Edge-Features auf Geräten mit Windows 10 und höher zulassen oder einschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Microsoft Edge-Browser**). Die Microsoft Edge-Einstellungen werden in diesem Update besser beschrieben und sind einfacher zu verstehen. 

Diese Features finden Sie unter [Einstellungen für Geräteeinschränkungen in Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

Gilt für: Windows 10 und höher

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Erweiterte Unterstützung für vollständig verwaltete Android Enterprise-Geräte (Preview)  <!--   3903241, 3903244, 3903246   -->
Die sich noch in der Public Preview befindende Unterstützung vollständig verwalteter Android Enterprise-Geräte ([erstmals im Januar 2019 angekündigt](whats-new.md#week-of-january-14-2019)) wurde wie folgt erweitert: 

- Auf vollständig verwalteten und dedizierten Geräten können Sie [Konformitätsrichtlinien](compliance-policy-create-android-for-work.md) erstellen, die Kennwortregeln und Betriebssystemanforderungen enthalten (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android Enterprise** (Plattform) > **Gerätebesitzer** (Profiltyp)). 

  Auf dedizierten Geräten wird das Gerät möglicherweise als **nicht konform** angezeigt. Der bedingte Zugriff ist auf dedizierten Geräten nicht verfügbar. Stellen Sie sicher, dass Sie alle Aufgaben und Aktionen fertig stellen, damit dedizierte Geräte Ihre zugewiesenen Richtlinien einhalten.

- [Bedingter Zugriff](conditional-access.md): Richtlinien für den bedingten Zugriff, die für Android gelten, gelten auch für vollständig verwaltete Android Enterprise-Geräte. Benutzer können ihre vollständig verwalteten Geräte nun mithilfe der **Microsoft Intune-App** in Azure Active Directory registrieren. Anschließend können sie Kompatibilitätsprobleme anzeigen und beheben, um auf Unternehmensressourcen zuzugreifen.

- Neue Microsoft Intune-App für Endbenutzer: Für vollständig verwaltete Android-Geräte gibt es die neue Endbenutzer-App **Microsoft Intune**. Diese neue App ist besonders schlank und modern. Sie bietet ähnliche Funktionen wie die Unternehmensportal-App, aber für vollständig verwaltete Geräte. Weitere Informationen finden Sie unter der [Microsoft Intune-App auf Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Um vollständig verwaltete Android-Geräte einzurichten, wechseln Sie zu **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte**. Die Unterstützung für vollständig verwaltete Android-Geräte befindet sich weiterhin in der Preview, und einige Intune-Features sind möglicherweise noch nicht voll funktionsfähig.  

Weitere Informationen zu dieser Public Preview finden Sie im Blog unter [Microsoft Intune – Preview 2 for Android Enterprise Fully Managed devices (Microsoft Intune: Preview 2 für vollständig verwaltete Android Enterprise-Geräte)](https://aka.ms/preview2_AE_fullymanaged).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Konfigurieren des Profils zum Überspringen einiger Bildschirme während des Setup-Assistenten <!-- 2276470  -->
Wenn Sie ein macOS-Registrierungsprofil erstellen, können Sie dieses konfigurieren, um die folgenden Anzeigen zu überspringen, wenn ein Benutzer den Setup-Assistenten durchläuft:
- Darstellung
- Anzeigefarbton
- iCloudStorage: Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden.  Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.
Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung oder Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Massengerätebenennung beim Registrieren unternehmenseigener iOS-Geräte<!--3566569  -->
Wenn Sie eine der Unternehmensbereitstellungsmethoden (DEP/ABM/ASM) von Apple verwenden, können Sie ein Format für Gerätenamen festlegen, um eingehende iOS-Geräte automatisch zu benennen. Sie können ein Format festlegen, das den Gerätetyp und die Seriennummer in der Vorlage enthält. Klicken Sie hierzu auf **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > **Token auswählen** >**Profil erstellen** > **Device naming format** (Format für die Gerätebenennung). Sie können vorhandene Profile bearbeiten, der Name wird jedoch nur auf neu synchronisierte Geräte angewendet.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Update der Standardtimeoutnachricht für die Registrierungsstatusseite <!-- 3959331 -->
Die Standardtimeoutnachricht, die Benutzern angezeigt wird, wenn der im Profil für die Registrierungsstatusseite festgelegte Timeoutwert überschritten wird, wurde aktualisiert. Die neue Standardnachricht soll Benutzern dabei helfen, die nächsten Schritte für die Bereitstellung der Registrierungsstatusseite zu verstehen.  

### <a name="device-management"></a>Geräteverwaltung

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Ausmustern nicht konformer Geräte  <!-- 1827291   -->
Die Bereitstellung dieses Features verzögert sich und ist in einem zukünftigen Release geplant.


### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Übernahme der Änderungen an Intune Data Warehouse V1.0 in die Betaversion <!-- 4403765 -->
Als V1.0 in Version 1808 erstmals eingeführt wurde, gab es wichtige Unterschiede zur Beta-API. Diese Änderungen werden mit Version 1903 in der Betaversion der API berücksichtigt. Wenn Sie über wichtige Berichte verfügen, die die Betaversion der API nutzen, wird dringend empfohlen, dass Sie diese Berichte in V1.0 konvertieren, um Breaking Changes zu vermeiden. Weitere Informationen finden Sie im [Änderungsprotokoll für die Intune Data Warehouse-API](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Überwachen des Status der Sicherheitsbaseline (Public Preview) <!-- 3082047 --> 
Der Überwachung von Sicherheitsbaselines wurde eine [Ansicht für einzelne Kategorien](security-baselines-monitor.md#per-category-view) hinzugefügt. (Sicherheitsbaselines befinden sich weiterhin in Preview). Die Ansicht für einzelne Kategorien zeigt jede Kategorie der Baseline mit dem Prozentsatz der Geräte an, die in jede Statusgruppe dieser Kategorie fallen. Sie können nun anzeigen, wie viele Geräte nicht mit den individuellen Kategorien übereinstimmen und falsch konfiguriert oder nicht anwendbar sind.

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Bereichsmarkierungen für Apple-VPP-Token <!--2371886  -->
Sie können nun Bereichsmarkierungen zu Apple-VPP-Token hinzufügen. Nur Benutzer, denen die gleiche Bereichsmarkierung zugewiesen ist, können auf das Apple-VPP-Token mit dieser Markierung zugreifen. VPP-Apps und E-Books, die mit diesem Token erworben werden, erben seine Bereichsmarkierungen. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Woche vom 1. April 2019

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Update für Zertifikatconnectors  <!-- ICM 113304612 -->
Wir haben Updates für den [Intune-Zertifikatconnector und den PFX-Zertifikatconnector für Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht. Mit diesen neuen Releases wurden einige bekannte Probleme behoben.  

### <a name="app-management"></a>App-Verwaltung

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Update für die Benutzeroberfläche für die Unternehmensportal-App für iOS <!-- 2536024 -->
Die Startseite der Unternehmensportal-App für iOS-Geräte wurde neu gestaltet. Sie entspricht nun mehr dem Muster der iOS-Benutzeroberfläche, und zudem können Apps und E-Books besser gefunden werden.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Änderungen der Unternehmensportal-Registrierung für Benutzer von iOS 12-Geräten <!--3448635 -->  
Die Anzeigen und Schritte bei der Registrierung im Unternehmensportal für iOS wurden aktualisiert und entsprechen nun den Änderungen der MDM-Registrierung, die mit Apple iOS 12.2 veröffentlicht wurden. Der aktualisierte Workflow fordert Benutzer zu Folgendem auf:  

* Zulassen, dass Safari die Unternehmensportal-Website öffnet, das Verwaltungsprofil herunterlädt und dann zur Unternehmensportal-App zurückkehrt.  
* Öffnen der App „Settings“ (Einstellungen), um das Verwaltungsprofil auf dem Gerät zu installieren.
* Rückkehr zur Unternehmensportal-App, um die Registrierung abzuschließen.  

Die aktualisierten Registrierungsschritte und -anzeigen finden Sie unter [Enroll iOS device in Intune (Registrieren eines iOS-Geräts in Intune)](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Woche vom 25. März 2019

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Unterstützung der Power BI-Compliance-App über das Data Warehouse-Blatt in Microsoft Intune <!-- 4260871 -->
Zuvor wurde mit dem Link **Power BI-Datei herunterladen** auf dem Blatt **Intune Data Warehouse** ein Intune Data Warehouse-Bericht heruntergeladen (PBIX-Datei). Dieser Bericht wurde nun durch die Power BI-Compliance-App ersetzt. Die Power BI-Compliance-App erfordert kein gesondertes Laden oder Setup. Sie wird direkt im Power BI-Onlineportal geöffnet und zeigt Daten spezifisch für Ihren Intune-Mandanten basierend auf Ihren Anmeldeinformationen an. Klicken Sie in Intune auf der rechten Seite des Intune-Blatts auf den Link **Intune Data Warehouse einrichten**. Klicken Sie dann auf **Power BI-App abrufen**. Weitere Informationen finden Sie unter [Connect to the Data Warehouse with Power BI (Verbinden von Data Warehouse mit Power BI)](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Woche vom 18. März 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Bereitstellen von Microsoft Visio und Microsoft Project <!-- 3725386  -->
Sie können nun Microsoft Visio Pro für Office 365 und den Microsoft Project Online-Desktopclient mithilfe von Microsoft Intune als unabhängige Apps auf Windows 10-Geräten bereitstellen, wenn Sie die Lizenzen für diese Apps besitzen. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**, um das Blatt **App hinzufügen** anzuzeigen. Wählen Sie auf dem Blatt **App hinzufügen** den **App-Typ** **Windows 10** aus. Klicken Sie dann auf **App-Suite konfigurieren**, um zu installierende Apps auszuwählen. Weitere Informationen über Office 365-Apps für Windows 10-Geräte finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Änderung des Produktnamens von Microsoft Visio Pro für Office 365 <!-- 3593653  -->
**Microsoft Visio Pro für Office 365** heißt jetzt **Microsoft Visio Online Plan 2**.  Weitere Informationen zu Microsoft Visio finden Sie unter [Visio Online Plan 2](https://products.office.com/visio/visio-online-plan-2). Weitere Informationen über Office 365-Apps für Windows 10-Geräte finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Einstellung für die Zeichenbeschränkung für Intune-App-Schutzrichtlinien <!-- 3291302  -->
Intune-Administratoren können eine Ausnahme für die Intune-App-Richtlinieneinstellung zum **Einschränken des Ausschneidens, Kopierens und Einfügens bei anderen Apps** festlegen.  Als Administrator können Sie die Anzahl von Zeichen festlegen, die aus einer verwalteten App ausgeschnitten oder kopiert werden können. Mit dieser Einstellungen kann die festgelegte Zeichenanzahl, unabhängig von der Einstellung für das Einschränken von Ausschneiden, Kopieren und Einfügen bei anderen Apps, mit einer beliebigen App geteilt werden. Beachten Sie, dass die Version der Intune-Unternehmensportal-App für Android Version 5.0.4364.0 oder höher erfordert. Weitere Informationen finden Sie unter [iOS-Datenschutz](app-protection-policy-settings-ios.md#data-protection), [Android-Datenschutz](app-protection-policy-settings-android.md#data-protection) und [Überprüfen der Schutzprotokolle für Client-Apps](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Office-Bereitstellungstool-XML für die Bereitstellung von Office ProPlus <!-- 3192477   -->
Sie können das Office-Bereitstellungstool-XML bereitstellen, wenn Sie eine Instanz von Office ProPlus in der Intune-Verwaltungskonsole erstellen. Dadurch wird die Anpassbarkeit erweitert, wenn die vorhandenen Benutzeroberflächenoptionen von Intune nicht Ihre Anforderungen erfüllen. Weitere Informationen finden Sie unter [Zuweisen von Office 365-Apps zu Windows 10-Geräten mit Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) und [Konfigurationsoptionen für das Office-Bereitstellungstool](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>App-Symbole werden nun mit einem automatisch generierten Hintergrund angezeigt <!-- 1429026  -->
App-Symbole werden nun in der Windows-Unternehmensportal-App mit einem automatisch generierten Hintergrund basierend auf der dominanten Farbe des Symbols angezeigt (sofern diese ermittelt werden kann). Wenn möglich, ersetzt dieser Hintergrund den grauen Rahmen, der zuvor auf App-Kacheln sichtbar war. Diese Änderung wird ab Version 10.3.3451.0 des Unternehmensportals angezeigt.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installieren verfügbarer Apps mithilfe der Unternehmensportal-App nach der Windows-Massenregistrierung <!-- 2751523   -->
Windows-Geräte, die mit der [Windows-Massenregistrierung](windows-bulk-enroll.md) (Bereitstellungspakete) in Intune registriert wurden, können die Unternehmensportal-App nutzen, um verfügbare Apps zu installieren. Weitere Informationen über die Unternehmensportal-App finden Sie unter [Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](store-apps-company-portal-app.md) und [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Die Microsoft Teams-App kann als Teil der Office-App-Suite ausgewählt werden <!-- 3828932  -->
Die Microsoft Teams-App kann als Teil der Office ProPlus-App-Suite enthalten oder ausgeschlossen werden. Dieses Feature funktioniert ab Buildnummer 16.0.11328.20116 von Office ProPlus. Der Benutzer muss sich vom Gerät abmelden und neu anmelden, damit die Installation abgeschlossen werden kann. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie einen **Office 365 Suite**-App-Typ aus, und klicken Sie dann auf **App-Suite konfigurieren**.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Automatisches Starten einer App, wenn mehrere Apps auf Geräten mit Windows 10 oder höher im Kioskmodus ausgeführt werden <!-- 2351390 -->

Auf Geräten mit Windows 10 und höher können Sie viele Apps im Kioskmodus ausführen. Dieses Update umfasst eine **AutoLaunch**-Einstellung (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Kiosk** (Profiltyp) > **Multi-App-Kiosk**). Verwenden Sie diese Einstellung, um eine App automatisch zu starten, wenn der Benutzer sich auf dem Gerät anmeldet.

Eine Liste und Beschreibungen aller Kioskeinstellungen finden Sie unter [Windows 10 and later device settings to run as a kiosk in Intune (Geräteeinstellungen unter Windows 10 und höher für die Ausführung als Kiosk in Intune)](kiosk-settings-windows.md).

Gilt für: Windows 10 und höher

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>Betriebsprotokolle enthalten Details zu nicht konformen Geräten <!-- 4063755  -->
Beim Weiterleiten von Intune-Protokollen an Azure-Überwachungsfeatures können Sie auch Betriebsprotokolle weiterleiten. In diesem Update stellen Betriebsprotokolle auch Informationen zu nicht konformen Geräten bereit. 

Weitere Informationen zu diesem Feature finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Weiterleiten von Protokollen an Azure Monitor in mehreren Intune-Workloads <!-- 3804627 -->
In Intune können Sie Überwachungs- und Betriebsprotokolle an Event Hubs, Speicher und Log Analytics in Azure Monitor weiterleiten (**Intune** > **Überwachung** > **Diagnoseeinstellungen**). In diesem Update können Sie diese Protokolle in mehreren Intune-Workloads weiterleiten, einschließlich Konformität, Konfigurationen, Client-Apps und mehr. 

Weitere Informationen zum Weiterleiten von Protokollen an Azure Monitor finden Sie unter [Senden von Daten an den Speicher, an Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Erstellen und Verwenden von Mobility Extensions für Android Zebra-Geräte in Intune <!-- 3305880   -->
Mit diesem Update unterstützt Intune die Konfiguration von Android Zebra-Geräten. Das heißt, Sie können ein Gerätekonfigurationsprofil erstellen und Einstellungen mithilfe von mit StageNow generierten MX-Profilen (Mobility Extensions) auf Android Zebra-Geräte anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android** (Plattform) > **MX-Profil (nur Zebra)** (Profiltyp)).

Weitere Informationen zu diesem Feature finden Sie unter [Use and manage Zebra devices with mobility extensions in Intune (Verwenden und Verwalten von Zebra-Geräten mit Mobility Extensions in Intune)](android-zebra-mx-overview.md).

Gilt für: Android

### <a name="device-management"></a>Geräteverwaltung

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Verschlüsselungsbericht für Windows 10-Geräte (Public Preview)<!-- 2351538 -->  
Verwenden Sie den neuen [Verschlüsselungsbericht (Vorschau)](encryption-monitor.md), um Details zum Verschlüsselungsstatus Ihrer Windows 10-Geräte anzuzeigen. Die verfügbaren Details umfassen die TPM-Version des Geräts, die Verschlüsselungsbereitschaft und den -status, die Fehlerberichterstattung und mehr.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Zugriff auf BitLocker-Wiederherstellungsschlüssel über das Intune-Portal (Public Preview) <!-- 2351547   -->  
Sie können nun Intune zum [Anzeigen von Details](encryption-monitor.md) zur BitLocker-Schlüssel-ID und den BitLocker-Wiederherstellungsschlüsseln in Azure Active Directory verwenden.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-Unterstützung für Intune-Szenarios auf iOS- und Android-Geräten <!-- 3411007 -->
Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser unterstützt, und enthält Verbesserungen für die Benutzerfreundlichkeit. Zu den von Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures gehören doppelte Identitäten, die Integration von App-Schutzrichtlinien, die Integration von Azure-Anwendungsproxys sowie verwaltete Favoriten und Verknüpfungen auf der Startseite. Weitere Informationen finden Sie unter [Microsoft Edge support (Microsoft Edge-Unterstützung)](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune-Connector unterstützen Geräte mit nur Exchange Active Sync nicht mehr <!--3105122  -->
Die Intune-Konsole unterstützt das Anzeigen und Verwalten von Geräten mit nur EAS, die über den Intune-Connector mit Exchange Online verbunden sind, nicht mehr. Stattdessen stehen Ihnen folgende Optionen zur Verfügung:
- Registrieren von Geräten in der mobilen Geräteverwaltung (Mobile Device Management, MDM)
- Verwenden von App-Schutzrichtlinien zum Verwalten Ihrer Geräte
- Verwenden von Exchange-Steuerelementen gemäß den Anweisungen unter [Clients and mobile in Exchange Online (Clients und Mobilgeräte in Exchange Online)](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Suchen eines bestimmten Geräts auf der Seite „Alle Geräte“ mithilfe von [Name] <!--4254930 -->
Sie können nun nach exakten Gerätenamen suchen. Wechseln Sie zu **Intune** > **Geräte** > **Alle Geräte**, und umschließen Sie den gesuchten Gerätenamen im Suchfeld mit {}, um nach einer genauen Übereinstimmung zu suchen. Zum Beispiel: **{Gerät12345}** .

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Unterstützung für zusätzliche Connectors auf der Seite „Mandantenstatus“ <!-- 3617202  -->
Auf der [Mandantenstatusseite](tenant-status.md) werden nun Statusinformationen zu zusätzlichen Connectors, einschließlich *Windows Defender Advanced Threat Protection* (ATP) und anderen Mobile Threat Defense-Connectors, angezeigt.

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Gewähren des schreibgeschützten Zugriffs auf Intune für einige Azure Active Directory-Rollen <!-- 3637917  -->
Der schreibgeschützte Zugriff auf Intune wurde den folgenden Azure AD-Rollen gewährt. Berechtigungen, die mit Azure AD-Rollen gewährt werden, haben Vorrang vor der rollenbasierten Zugriffssteuerung von Intune.

Schreibgeschützter Zugriff auf Intune-Überwachungsdaten:

- Complianceadministrator
- Administrator für Konformitätsdaten

Schreibgeschützter Zugriff auf alle Intune-Daten:

- Sicherheitsadministrator
- Sicherheitsoperator
- Sicherheitsleseberechtigter

Weitere Informationen finden Sie unter [Rollenbasierte Zugriffssteuerung mit Microsoft Intune](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Bereichsmarkierungen für iOS-App-Bereitstellungsprofile <!--2934430   -->
Sie können einem iOS-App-Bereitstellungsprofil eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie das iOS-App-Bereitstellungsprofil auf diese zugreifen können. Weitere Informationen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Bereichsmarkierungen für App-Konfigurationsrichtlinien <!--2371891   -->
Sie können einer App-Konfigurationsrichtlinie eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie die App-Konfigurationsrichtlinie auf diese zugreifen können. Die App-Konfigurationsrichtlinie kann nur den Apps zugeordnet werden, denen dieselben Bereichsmarkierungen zugewiesen sind. Weitere Informationen finden Sie unter [Use RBAC and scope tags (Verwenden der rollenbasierten Zugriffssteuerung und von Bereichsmarkierungen)](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Microsoft Edge-Unterstützung für Intune-Szenarios auf iOS- und Android-Geräten <!-- 3411007 -->
Microsoft Edge unterstützt alle Verwaltungsszenarios, die Intune Managed Browser unterstützt, und enthält Verbesserungen für die Benutzerfreundlichkeit. Zu den von Intune-Richtlinien aktivierten Microsoft Edge-Unternehmensfeatures gehören doppelte Identitäten, die Integration von App-Schutzrichtlinien, die Integration von Azure-Anwendungsproxys sowie verwaltete Favoriten und Verknüpfungen auf der Startseite. Weitere Informationen finden Sie unter [Microsoft Edge support (Microsoft Edge-Unterstützung)](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Woche vom 25. Februar 2019

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell-Modul <!-- 951068  -->
Das Intune PowerShell-Modul, das Unterstützung für die Intune-API über Microsoft Graph bereitstellt, ist jetzt im [PowerShell-Katalog](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10) verfügbar.

- [Informationen zur Verwendung dieses Moduls](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Beispielszenarios für die Verwendung dieses Moduls](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Verbesserte Unterstützung für die Übermittlungsoptimierung  <!--3183757  -->
Die Unterstützung für die Konfiguration der Übermittlungsoptimierung in Intune wurde erweitert. Sie können nun eine erweiterte Liste von [Einstellungen für die Übermittlungsoptimierung](delivery-optimization-settings.md) konfigurieren und direkt über die Intune-Konsole auf Ihre Geräte abstimmen.


## <a name="week-of-february-18-2019"></a>Woche vom 18. Februar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Verwendung von Google Play Protect-APIs für Android-Geräte in Intune <!-- 2577355   -->
Manche IT-Administratoren arbeiten in einer Bring Your Own Device-Umgebung (BYOD), in der manche Endbenutzer ihre Mobiltelefone möglicherweise rooten oder jailbreaken. Viele Benutzer handeln zwar nicht in schlechter Absicht, dennoch kann dieses Verhalten dazu führen, dass viele Intune-Richtlinien umgangen werden, die zum Schutz der Organisationsdaten auf dem Gerät des Endbenutzers eingerichtet wurden. Deshalb enthält Intune eine Erkennung von Rooting und Jailbreaks für registrierte und nicht registrierte Geräte. Ab diesem Release verwendet Intune die Google Play Protect-APIs, um die bisherigen Überprüfungen auf Rooting für nicht registrierte Geräte zu ergänzen. Google stellt zwar nicht alle Überprüfungsmechanismen für Rooting zur Verfügung, aber diese APIs sollten dennoch Benutzer ermitteln können, die Ihre Geräte abweichend von der Gerätekonfiguration gerootet haben, um neuere Betriebssystemupdates für ältere Geräte zu erhalten. Diesen Benutzern kann der Zugriff auf Unternehmensdaten verwehrt werden, oder ihre Unternehmenskonten können aus den Apps entfernt werden, für die Richtlinien aktiviert sind. Es wurden zudem einige Updates für die Berichterstellung auf dem Blatt „Intune-App-Schutz“ vorgenommen, um IT-Administratoren die Arbeit zu erleichtern: Der Bericht „Gekennzeichnete Benutzer“ enthält die Benutzer, die durch eine Überprüfung mit der SafetyNet-API von Google Play Protect ermittelt wurden, und der Bericht „Potentially Harmful Apps“ (Potenziell schädliche Apps) enthält die Apps, die durch eine Überprüfung mit der Verify Apps-API von Google ermittelt wurden. Dieses Feature ist unter Android verfügbar.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informationen zu Win32-Apps auf dem Blatt „Problembehandlung“ <!-- 2617342   -->
Sie können nun Protokolldateien zu Fehlern bei der Installation von Win32-Apps über das Blatt **Problembehandlung** der Intune-App abrufen. Weitere Informationen zur Behandlung von Problemen mit der App-Installation finden Sie unter [Troubleshoot app installation issues (Problembehandlung bei der App-Installation)](troubleshoot-app-install.md) und [Behandeln von Win32-App-Problemen](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Details zum Status von iOS-Apps <!-- 3761235   -->
Es wurden neue Fehlermeldungen eingeführt, die bei folgenden Problemen bei der Installation von Apps ausgelöst werden:
- Fehler beim Installieren von VPP-Apps auf gemeinsam genutzten iPads
- Fehler bei deaktiviertem App Store
- Fehler beim Suchen von VPP-Lizenzen für Apps
- Fehler beim Installieren von System-Apps mit MDM-Anbietern
- Fehler beim Installieren von Apps, wenn das Gerät sich im Kioskmodus oder im Modus für verlorene Geräte befindet
- Fehler beim Installieren von Apps wenn der Benutzer nicht im App Store angemeldet ist

Navigieren Sie in Intune zu **Client-Apps** > **Apps** > Name der App > **Geräteinstallationsstatus**. Die neuen Fehlermeldungen werden in der Spalte **Statusdetails** angezeigt.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Neue Anzeige „App-Kategorien“ in der Unternehmensportal-App für Windows 10<!-- 3834780  -->
Eine neue Anzeige namens **App-Kategorien** wurde hinzugefügt, um das Durchsuchen und Auswählen von Apps im Unternehmensportal für Windows 10 zu verbessern. Für Benutzer werden Apps nun sortiert nach Kategorien wie **Empfohlen**, **Bildung** und **Produktivität** angezeigt. Diese Änderung ist im Unternehmensportal ab Version 10.3.3451.0 vorhanden. Informationen zu dieser neuen Anzeige finden Sie unter [Updates der Benutzeroberfläche für Endbenutzer-Apps in Intune](https://docs.microsoft.com/intune/whats-new-app-ui). Weitere Informationen zu den Apps im Unternehmensportal finden Sie unter [Install and share apps on your device (Installieren und Freigeben von Apps auf Ihrem Gerät)](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI-Compliance-App <!-- 1455231 doc-work-item -->
Sie können über die App [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) in Power BI auf Ihre Intune Data Warehouse-Instanz zugreifen. Mit dieser Power BI-App können Sie nun auf vorab erstellte Berichte zugreifen und diese freigeben, ohne dafür ein Setup durchzuführen und ohne Ihren Webbrowser zu verlassen. Weitere Informationen finden Sie im [Änderungsprotokoll für die Intune Data Warehouse-API](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Ausführung von PowerShell-Skripts auf einem 64-Bit-Host auf 64-Bit-Geräten <!-- 1862675   -->
Wenn Sie ein PowerShell-Skript zu einem Gerätekonfigurationsprofil hinzufügen, wird das Skript immer im 32-Bit-Modus ausgeführt, auch auf einem 64-Bit-Betriebssystem. Seit diesem Update kann ein Administrator das Skript auf einem 64-Bit-Gerät auf einem 64-Bit-Host von PowerShell ausführen (**Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen** > **Konfigurieren** > **Skript in 64-Bit-PowerShell-Host ausführen**).

Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte](intune-management-extension.md).

Gilt für: Windows 10 und höher

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS-Benutzer werden aufgefordert, ihr Kennwort zu aktualisieren <!-- 1873216 -->
Intune erzwingt die Einstellung **ChangeAtNextAuth** für macOS-Geräte. Diese Einstellung wirkt sich auf Benutzer und Geräte aus, die über Konformitätskennwortrichtlinien oder Geräteeinschränkungsprofile für Kennwörter verfügen. Benutzer werden einmal aufgefordert, ihr Kennwort zu aktualisieren. Diese Aufforderung wird angezeigt, wenn ein Benutzer zum ersten Mal eine Aufgabe ausführt, für die Authentifizierung erforderlich ist, z. B. die Anmeldung auf dem Gerät. Benutzer können ebenfalls dazu aufgefordert werden, ihre Kennwörter zu aktualisieren, wenn sie etwas tun, für das Administratorberechtigungen erforderlich sind, z. B. das Anfordern des Keychain-Zugriffs. 

Auch bei Änderungen an neuen oder vorhandenen Kennwortrichtlinien durch den Administrator werden Benutzer dazu aufgefordert, ihre Kennwörter zu aktualisieren.

Gilt für:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>Zuweisen von SCEP-Zertifikaten zu einem macOS-Gerät ohne Benutzer    <!-- 2340521    -->
Sie können SCEP-Zertifikate (Simple Certificate Enrollment-Protokoll) mit Geräteattributen zu macOS-Geräten hinzufügen (dies gilt auch für Geräte ohne Benutzeraffinität) und die Zertifikatprofile zu WLAN- oder VPN-Profilen zuordnen. Dadurch wird die bereits vorhandene Unterstützung erweitert, sodass [SCEP-Zertifikate zu Geräten mit und ohne Benutzeraffinität zugewiesen werden können](certificates-profile-scep.md), auf denen Windows, iOS oder Android ausgeführt wird.  Mit diesem Update wurde die Option hinzugefügt, den Zertifikattyp *Gerät* beim Konfigurieren eines SCEP-Zertifikatprofils für macOS auszuwählen.

Gilt für: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Update der Intune-Benutzeroberfläche für den bedingten Zugriff   <!-- 2432313   -->
Wir haben die Benutzeroberfläche für den bedingten Zugriff in der Intune-Konsole verbessert. Dazu gehören:
- Das Intune-Blatt *Bedingter Zugriff* wurde durch das entsprechende Blatt aus Azure Active Directory ersetzt. Dadurch wird sichergestellt, dass Sie alle Einstellungen und Konfigurationen für den [bedingten Zugriff](conditional-access.md) (eine Technologie von Azure AD) innerhalb der Intune-Konsole nutzen können. 
- Das Blatt *Lokaler Zugriff* wurde in *Exchange-Zugriff* umbenannt, und das Setup für den *Exchange-Dienstconnector* wurde auf dieses Blatt verschoben.  Dadurch ändert sich der Ort, an dem Sie [Details zu Exchange (online und lokal) konfigurieren und überwachen](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Ausführung von Kioskbrowsern und Microsoft Edge-Browser-Apps auf Windows 10-Geräten im Kioskmodus <!-- 2935135   -->
Sie können Windows 10-Geräte im Kioskmodus verwenden, um eine oder mehrere Apps auszuführen. Durch dieses Update wurden unter anderem folgende Änderungen an der Verwendung von Browser-Apps im Kioskmodus vorgenommen:

- Der Microsoft Edge-Browser und der Kioskbrowser können nun als ausführbare Apps zu Kioskgeräten hinzugefügt werden (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) bzw. **Kiosk** (Profiltyp)).
- Es stehen neue Features und Einstellungen zum Zulassen oder Gewähren zur Verfügung (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp)), einschließlich:

- Microsoft Edge-Browser:
  - Verwenden des Microsoft Edge-Kioskmodus
  - Aktualisieren des Browsers nach einer Leerlaufzeit

- Favoriten und Suche:
  - Zulassen von Änderungen an der Suchmaschine

Eine Liste dieser Einstellungen finden Sie unter:

- [Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als Kiosk in Intune](kiosk-settings-windows.md)
- [Microsoft Edge-Browser](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](device-restrictions-windows-10.md##favorites-and-search)

Gilt für: Windows 10 und höher

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Neue Einstellungen für Einschränkungen für iOS- und macOS-Geräte <!-- 3448774   -->
Sie können einige Einstellungen und Features auf iOS- und macOS-Geräten einschränken (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** bzw. **macOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Mit diesem Update werden weitere Features und Einstellungen hinzugefügt, die Sie steuern können. Sie können auf iOS-Geräten beispielsweise die Bildschirmzeit festlegen, eSIM-Einstellungen und Mobilfunktarife ändern und mehr. Außerdem können Sie Softwareupdates später für Benutzer bereitstellen oder das Content Caching auf macOS-Geräten blockieren. 

Weitere Informationen zu den einschränkbaren Features und Einstellungen finden Sie unter:

- [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md)
- [Einstellungen für Geräteeinschränkungen für macOS-Geräte in Microsoft Intune](device-restrictions-macos.md)

Gilt für:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>„Kioskgeräte“ heißen bei Android Enterprise-Geräten jetzt „Dedizierte Geräte“ <!-- 3598402   -->
Zur Anpassung an die Android-Terminologie wurde **Kiosk** für Android Enterprise-Geräte in **dedizierte Geräte** umbenannt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** (Plattform) > **Nur Gerätebesitzer** > **Geräteeinschränkungen** > **Dedizierte Geräte**).

Eine Liste der verfügbaren Einstellungen finden Sie unter [Device settings to allow or restrict features (Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-android-for-work.md#dedicated-device-settings).

Gilt für:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Verschiebung der iOS-Einstellungen von Safari und zum Verzögern der Sichtbarkeit von Updates für Benutzer auf der Benutzeroberfläche von Intune <!-- 3640850, 3803313   -->
Für iOS-Geräte können Sie Safari-Einstellungen festlegen und Softwareupdates konfigurieren. Mit diesem Update werden diese Einstellungen auf der Intune-Benutzeroberfläche verschoben:

- Die Safari-Einstellungen wurden von **Safari** (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)) zu **[Integrierte Apps](device-restrictions-ios.md#built-in-apps)** verschoben.
- Die Einstellung **Delaying user software update visibility for supervised iOS devices** (Sichtbarkeit von Updates für Benutzer von überwachten iOS-Geräten verzögern) (**Softwareupdates** > **Richtlinien für iOS aktualisieren**) wurde zu **Geräteeinschränkungen** >  **[Allgemein](device-restrictions-ios.md#general)** verschoben.  Weitere Informationen zu den Auswirkungen auf vorhandene Richtlinien finden Sie unter [Konfigurieren von iOS-Updaterichtlinien in Intune](software-updates-ios.md#configure-the-policy). 

Eine Liste der Einstellungen finden Sie unter:

- [iOS-Geräteeinschränkungen](device-restrictions-ios.md) 
- [iOS-Softwareupdates](software-updates-ios.md)

Diese Funktion gilt für: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>Umbenennung von „Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)“ auf iOS-Geräten in „Bildschirmzeit“ <!-- 3699164   -->
Sie können die Einstellung **Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)** für überwachte iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Allgemein**) konfigurieren. Mit diesem Update wurde die Einstellung in **Bildschirmzeit (nur überwacht)** umbenannt. 

Das Verhalten ändert sich nicht. Genauer gesagt: 

- iOS 11.4.1 und früher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltenden Einschränkungen in den Geräteeinstellungen bearbeiten. 
- iOS 12.0 und höher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltende **Bildschirmzeit** (einschließlich Einschränkungen von Inhalt und Datenschutz) in den Geräteeinstellungen bearbeiten. Auf Geräten, auf denen mindestens iOS 12.0 ausgeführt wird, wird die Registerkarte „Einschränkungen“ in den Geräteeinstellungen nicht mehr angezeigt. Diese Einstellungen befinden sich unter **Bildschirmzeit**. 

Eine Liste der Einstellungen finden Sie in den [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md#general).

Gilt für: 
- iOS


### <a name="device-management"></a>Geräteverwaltung

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Umbenennen eines registrierten Windows-Geräts <!-- 1911112  -->
Sie können registrierte Windows 10-Geräte (RS4 oder höher) jetzt umbenennen. Navigieren Sie hierfür zu **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Gerät umbenennen**. Dieses Feature unterstützt derzeit nicht das Umbenennen von Windows-Geräten mit Azure AD Hybrid.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Automatische Zuweisung von Bereichsmarkierungen zu Ressourcen, die von einem Administrator für diesen Bereich erstellt wurden <!-- 3173823  -->
Wenn ein Administrator eine Ressource erstellt, werden alle Bereichstags, die dem Administrator zugewiesen sind, automatisch auch den neuen Ressourcen zugewiesen.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Bericht für fehlgeschlagene Registrierungen wurde auf das Blatt „Geräteregistrierung“ verschoben <!-- 3560202  -->
Der Bericht zu **fehlgeschlagenen Registrierungen** wurde in den Abschnitt **Überwachen** des Blatts **Geräteregistrierung** verschoben. Zwei neue Spalten („Registrierungsmethode“ und „Betriebssystemversion“) wurden hinzugefügt.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Umbenennung des Berichts „Unternehmensportalabbruch“ in „Unvollständige Benutzerregistrierungen“ <!--3815076 eemiss -->
Der Bericht **Unternehmensportalabbruch** wurde in **Unvollständige Benutzerregistrierungen** umbenannt.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Woche vom 4. Februar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Dunkler Modus für Intune-Unternehmensportal für macOS <!-- 3300524  -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Unternehmensportal an die Farben dieses Modus angepasst.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Woche vom 21. Januar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Popupbenachrichtigungen für Win32-Apps <!-- 3136566   -->
Sie können die Anzeige von Popupbenachrichtigungen für die Benutzer pro App-Zuweisung unterdrücken. Wählen Sie in Intune **Client-Apps** > **Apps** > App-Auswahl > **Zuweisungen** > **Gruppen einschließen**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Update der Benutzeroberfläche für Intune-App-Schutzrichtlinien <!-- 3251427  -->
Wir haben die Bezeichnungen für Einstellungen und Schaltflächen für den Intune-App-Schutz geändert, um die Verständlichkeit zu erleichtern. Einige Änderungen sind:  
- Die Steuerelemente **Ja** / **Nein** wurden in erster Linie in die Steuerelemente **Blockieren** / **Zulassen** und **Deaktivieren** / **Aktivieren** geändert. Die Bezeichnungen wurden ebenfalls aktualisiert.  
- Einstellungen wurden darüber hinaus neu formatiert, um die Einstellungen und ihre Bezeichnungen im Steuerelement nebeneinander anzuzeigen und eine bessere Navigation zu ermöglichen.   

Die Standardeinstellungen und die Anzahl von Einstellungen bleiben gleich, aber durch die oben genannten Änderungen werden Verständlichkeit, Navigation und Verwendung der Einstellungen verbessert, um dem Benutzer eine einfachere Anwendung der ausgewählten App-Schutzrichtlinien zu ermöglichen. Weitere Informationen finden Sie unter [iOS-Einstellungen](app-protection-policy-settings-ios.md) und [Android-Einstellungen](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Zusätzliche Einstellungen für Outlook <!-- 3301182  -->
Sie können nun die folgenden zusätzlichen Einstellungen für Outlook für iOS und Android mit Intune konfigurieren:

- Lassen Sie nur die Verwendung von Geschäfts-, Schul- oder Unikonten in Outlook in iOS und Android zu.
- Stellen sie eine moderne Authentifizierung für Office 365 und eine hybride moderne Authentifizierung für lokale Konten bereit.
- Verwenden Sie `SAMAccountName` für das Feld „Benutzername“ im E-Mail-Profil, wenn die Basisauthentifizierung aktiviert ist.
- Ermöglichen Sie das Speichern von Kontakten.
- Konfigurieren von E-Mail-Infos externer Empfänger
- Konfigurieren Sie **Posteingang mit Relevanz**.
- Erfordern Sie biometrische Daten für den Zugriff auf Outlook für iOS.
- Blockieren Sie externe Bilder.

> [!NOTE]
> Wenn Sie die Richtlinien für den Intune-App-Schutz zur Verwaltung des Zugriffs auf Unternehmensidentitäten verwenden, sollten Sie ggf. nicht aktivieren, dass **biometrische Daten erforderlich** sind. Weitere Informationen finden Sie unter **Unternehmensanmeldeinformationen für Zugriff erforderlich** für [iOS-Zugriffseinstellungen](app-protection-policy-settings-ios.md#access-requirements) und [Android-Zugriffseinstellungen](app-protection-policy-settings-android.md#access-requirements).

Weitere Informationen finden Sie unter [Microsoft Outlook-Konfigurationseinstellungen](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Löschen von Android Enterprise-Apps <!-- 1352553 -->
Sie können verwaltete Google Play-Apps aus Microsoft Intune löschen. Um eine verwaltete Google Play-App zu löschen, öffnen Sie Microsoft Intune im Azure-Portal und wählen **Client-Apps** > **Apps** aus. Klicken Sie in der App-Liste auf die Auslassungspunkte (...) rechts neben der verwalteten Google Play-App, und wählen Sie dann in der angezeigten Liste die Option **Löschen** aus. Wenn Sie eine verwaltete Google Play-App aus der App-Liste löschen, wird die Genehmigung für die Google Play-App automatisch aufgehoben.

#### <a name="managed-google-play-app-type----1352580---"></a>App-Typ „Verwaltetes Google Play“ <!-- 1352580 -->
Der App-Typ **Verwaltetes Google Play** ermöglicht es Ihnen, [verwaltete Google Play-Apps](https://play.google.com/work/search?q=microsoft&c=apps) gezielt zu Intune hinzuzufügen. Als Intune-Administrator können Sie verwaltete Google Play-Apps ab sofort in Intune suchen, genehmigen, synchronisieren und genehmigte verwaltete Google Play-Anwendungen zuweisen.  Sie müssen nicht mehr separat zur verwalteten Google Play-Konsole navigieren, und es ist keine erneute Authentifizierung mehr erforderlich.  Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie in der Liste **App-Typ** als App-Typ **Verwaltetes Google Play** aus.

### <a name="default-android-pin-keyboard----3802457---"></a>Android-Standardtastatur für die PIN <!-- 3802457 -->
Endbenutzer, die eine Intune-App-Schutzrichtlinien-PIN auf ihren Android-Geräten vom Typ „Numerisch“ festgelegt haben, wird nun die Android-Standardtastatur anstelle der zuvor entworfenen, festen Android-Tastaturbenutzeroberfläche angezeigt. Diese Änderung wurde implementiert, damit die Standardtastaturen für die PIN-Typen „Numerisch“ und/oder „Passcode“ auf Android- und iOS-Geräten konsistent sind. Weitere Informationen über die Zugriffseinstellungen für Endbenutzer unter Android, z.B. APP-PIN, finden Sie unter [Android-Zugriffsanforderungen](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines (Public Preview) <!-- 2055484   -->

Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

Dieses Feature befindet sich in der Public Preview, d.h. Profile, die in dieser Version erstellt werden, werden nicht in die allgemein verfügbaren Vorlagen für Sicherheitsbaselines übernommen. Es wird davon abgeraten, diese Preview-Vorlagen in Produktionsumgebungen zu verwenden.

Weitere Informationen zu Sicherheitsbaselines finden Sie unter [Erstellen einer Windows 10-Sicherheitsbaseline in Intune](security-baselines-monitor.md).

Diese Funktion gilt für: Windows 10 und höher

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Nicht-Administratoren können BitLocker auf Windows 10-Geräten aktivieren, die in Azure AD eingebunden sind<!-- 2147379   -->
Beim Aktivieren der BitLocker-Einstellungen auf Windows 10-Geräten (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** als Plattform > **Endpunktschutz** als Profiltyp > **Windows-Verschlüsselung**) fügen Sie BitLocker-Einstellungen hinzu. 

Dieses Update enthält eine neue BitLocker-Einstellung, um Standardbenutzern (Nicht-Administratoren), die Verschlüsselung zu ermöglichen. 

Diese Einstellungen finden Sie unter [Endpunktschutzeinstellungen für Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Überprüfen der Konformität von Configuration Manager <!-- 2192052  eepublished  -->
Dieses Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10 und höher** > **Configuration Manager-Konformität**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über diese Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

[Configuration Manager-Konformität](compliance-policy-create-windows.md#configuration-manager-compliance) beschreibt diese Einstellung.

Gilt für: Windows 10 und höher

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Anpassen des Hintergrundbilds auf überwachten iOS-Geräten mithilfe eines Gerätekonfigurationsprofils <!-- 2809324   -->
Wenn Sie ein Gerätekonfigurationsprofil für iOS-Geräte erstellen, können Sie einige Features in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für die Plattform > **Gerätefeatures** anpassen. Dieses Update enthält neue **Hintergrundbildeinstellungen**, die es einem Administrator ermöglichen, ein.png-,.jpg- oder.jpeg-Bild auf dem Startbildschirm oder Sperrbildschirm zu verwenden. Die Einstellungen für das Hintergrundbild gelten nur für überwachte Geräte. 

Eine Liste dieser Einstellungen finden Sie [iOS-Einstellungen für Gerätefeatures](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10-Kiosk ist allgemein verfügbar <!-- 3594661  -->
In diesem Update wird das Kiosk-Feature auf Windows 10 und höher allgemein verfügbar (GA) gemacht. Alle Einstellungen, die Sie hinzufügen und konfigurieren können, finden Sie unter [Kioskeinstellungen für Windows 10 (und höher)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Die Kontaktfreigabe über Bluetooth in „Geräteeinschränkungen“ > „Gerätebesitzer für Android Enterprise“ wurde entfernt <!-- 3598396   -->
Wenn Sie ein Geräteeinschränkungsprofil für Android Enterprise-Geräte erstellen, gibt es die Einstellung **Kontaktfreigabe über Bluetooth**. In diesem Update wird die Einstellung **Kontaktfreigabe über Bluetooth** entfernt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen > Gerätebesitzer** für Profiltyp > **Allgemein**). 

Die Einstellung **Kontaktfreigabe über Bluetooth** wird für die Verwaltung von Android Enterprise-Gerätebesitzern nicht unterstützt. Die Entfernung dieser Einstellung hat deshalb keine Auswirkungen auf Geräte oder Mandanten – selbst dann, wenn diese Einstellung in Ihrer Umgebung aktiviert und konfiguriert ist.

Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](device-restrictions-android-for-work.md).

Gilt für: Android Enterprise-Gerätebesitzer

### <a name="device-management"></a>Geräteverwaltung

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Unterstützung für selektives Zurücksetzen für WIP-Geräte ohne Registrierung <!-- 1434452 -->
Windows Information Protection Without Enrollment (WIP-WE) ermöglicht es Kunden, ihre Unternehmensdaten auf Windows 10-Geräten zu schützen, ohne dass eine vollständige MDM-Registrierung erforderlich ist. Sobald Dokumente durch eine WIP-WE-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-WE-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Mobile App** > **Selektive App-Zurücksetzung** aus.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Neue Betriebsprotokolle und Möglichkeit zum Senden von Protokollen an Azure Monitor-Dienste <!-- 3762211  -->
Intune bietet ein integrierte Überwachungsprotokollierung, die Ereignisse bei Änderungen verfolgt. Dieses Update enthält neue Protokollierungsfeatures, darunter: 
- Betriebsprotokolle (Vorschau), die Details für Benutzer und Geräte anzeigen, die registriert sind, einschließlich der erfolgreichen und fehlerhaften Versuche.
- Die Überwachungs- und Betriebsprotokolle können an Azure Monitor gesendet werden, einschließlich Speicherkonten, Event Hubs und Log Analytics. Diese Dienste ermöglichen es Ihnen, Analysen wie Splunk und QRadar zu speichern, zu nutzen und Visualisierungen Ihrer Protokolldaten zu erhalten.

In [Senden von Daten an den Speicher, Event Hubs oder Log Analytics in Intune](review-logs-using-azure-monitor.md) finden Sie weitere Informationen zu diesem Feature.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Überspringen weiterer Setup-Assistent-Anzeigen auf einem iOS-DEP-Gerät <!-- 2687509  -->
Zusätzlich zu den Bildschirmanzeigen, die derzeit übersprungen werden können, können Sie festlegen, dass iOS-DEP-Geräte die folgenden Anzeigen im Setup-Assistenten überspringen, wenn ein Benutzer das Gerät registriert: Displayton, Privatsphäre, Android-Migration, Startschaltfläche, iMessage & FaceTime, Onboarding, Watch-Migration, Darstellung, Bildschirmzeit, Softwareupdate und SIM-Setup.
Um die zu überspringenden Bildschirme auszuwählen, wechseln Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, wählen Sie das Token und unter **Profile** das Profil aus, wählen Sie **Eigenschaften** > **Anpassung des Setup-Assistenten** und **Ausblenden**  für alle Bildschirme aus, die Sie überspringen möchten, und wählen Sie **OK** aus.
Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden. Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung <!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie jetzt verwaltetes Google Play zum Bereitstellen von Store-Apps und branchenspezifischen Apps für Benutzer verwenden. Insbesondere können Sie Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte kompromittieren müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Woche vom 14. Januar 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Vorschau der Unterstützung für vollständig verwaltete Android-Unternehmensgeräte <!-- 1574342  -->
Intune unterstützt jetzt vollständig verwaltete Android-Geräte in einem „Gerätebesitzer“-Szenario, in dem das Unternehmen Besitzer ist und die Geräte konsequent von der IT-Abteilung verwaltet und einzelnen Benutzern zugewiesen werden. So können Administratoren das gesamte Gerät verwalten, einen erweiterten Bereich von Richtlinienkontrollen erzwingen, die Arbeitsprofilen nicht zur Verfügung stehen, und Benutzer werden derart eingeschränkt, dass sie nur Apps von verwaltetem Google Play installieren können. Weitere Informationen finden Sie unter [Einrichten der Intune-Registrierung von vollständig verwalteten Android-Geräten](android-fully-managed-enroll.md) und [Registrieren Ihrer dedizierten Geräte oder vollständig verwalteten Geräte](android-dedicated-devices-fully-managed-enroll.md).  Hinweis: Dieses Feature befindet sich in der Vorschau. Einige Intune-Funktionen, wie z.B. Zertifikate, Konformität und bedingter Zugriff, stehen momentan für vollständig verwaltete Android-Benutzergeräte nicht zur Verfügung.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Woche vom 7. Januar 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-app-pin----2298397---"></a>Intune-App-PIN <!-- 2298397 -->
Als IT-Administrator können Sie die Anzahl der Tage konfigurieren, die ein Endbenutzer warten kann, bis seine Intune-App-PIN geändert werden muss. Die neue Einstellung *Anzahl von Tagen für PIN-Zurücksetzung* steht im Azure-Portal unter **Intune** > **Client-Apps** > **App-Schutzrichtlinien** > **Richtlinie erstellen** > **Einstellungen** > **Zugriffsanforderungen** zur Verfügung. Dieses Feature kann auf [iOS](app-protection-policy-settings-ios.md)- und [Android](app-protection-policy-settings-android.md)-Geräten verwendet werden und unterstützt positive ganze Zahlen als Wert.


#### <a name="intune-device-reporting-fields----2748738---"></a>Felder zur Geräteberichterstellung in Intune <!-- 2748738 -->
Intune bietet zusätzliche Felder zur Geräteberichtserstellung, einschließlich Feldern für App-Registrierungs-ID, Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-Modell. In Intune sind diese Felder unter **Client-Apps** > **Status des App-Schutzes** und **Bericht zum App-Schutz: iOS, Android** verfügbar. Darüber hinaus werden diese Parameter Sie bei der Konfiguration der **Zulassen**-Liste für den Gerätehersteller (Android), der **Zulassen**-Liste für das Gerätemodell (Android und iOS) sowie der Einstellung der mindestens erforderlichen Android-Sicherheitspatchversion unterstützen. 


### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und wurden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->

Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update:

- Administrative Vorlagen umfassen über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
- Administrative Vorlagen befinden sich in der öffentlichen Vorschauphase.
- Administrative Vorlagen werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
- Die Berichterstellung ist aktiviert.

Unter [Windows 10 templates to configure group policy settings (Windows 10-Vorlagen zur Konfiguration von Gruppenrichtlinieneinstellungen)](administrative-templates-windows.md) erfahren Sie mehr zu diesem Feature.

Gilt für: Windows 10 und höher

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Verwenden von S/MIME zum Verschlüsseln und Signieren von mehreren Geräten für einen Benutzer  <!-- 1333642 -->
Mit diesem Update wird die E-Mail-Verschlüsselung mit S/MIME mittels eines neuen Profils für importierte Zertifikate eingeführt. Navigieren Sie zu deren Verwendung zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, und wählen Sie zuerst die Plattform und dann den Profiltyp **Importiertes PKCS-Zertifikat** aus. In Intune können Sie Zertifikate im PFX-Format importieren. Intune kann dann genau diese Zertifikate an mehrere Geräte übergeben, die durch einen einzelnen Benutzer registriert wurden. Außerdem enthalten:
- Das native iOS-E-Mail-Profil unterstützt die Aktivierung der S/MIME-Verschlüsselung mithilfe importierter Zertifikate im PFX-Format.
- Die native E-Mail-App auf Windows Phone 10-Geräten verwendet automatisch das S/MIME-Zertifikat.
- Die privaten Zertifikate können über mehrere Plattformen übermittelt werden. Jedoch unterstützen nicht alle E-Mail-Apps S/MIME.
- Auf anderen Plattformen müssen Sie möglicherweise die E-Mail so konfigurieren, dass Sie S/MIME zulässt.  
- E-Mail-Apps, die die S/MIME-Verschlüsselung unterstützen, behandeln das Abrufen von Zertifikaten für die S/MIME-E-Mail-Verschlüsselung womöglich in einer Art und Weise, die von MDM nicht unterstützt werden kann, z.B. durch Lesen über den Zertifikatspeicher des Verlegers.
Weitere Informationen zu diesem Feature finden Sie unter [S/MIME für die Signierung und Verschlüsselung von E-Mails in Intune](certificates-s-mime-encryption-sign.md).
Unterstützt auf: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Neue Optionen zum automatischen Herstellen einer Verbindung und Beibehalten von Regeln bei der Verwendung von DNS-Einstellungen unter Windows 10 und höher <!-- 1333665, 2999078 -->
Auf Geräten unter Windows 10 und höher können Sie ein VPN-Konfigurationsprofil erstellen, das eine Liste von DNS-Servern zum Auflösen von Domänen enthält, z. B. „contoso.com“. Dieses Update enthält neue Einstellungen für die Namensauflösung (Klicken Sie auf **Gerätekonfiguration** > **Profile** > **Profil erstellen**. Wählen Sie **Windows 10 und höher** als Plattform und **VPN** als Profiltyp aus, und wählen Sie **DNS-Einstellungen** >**Hinzufügen** aus): 
- **Automatisch verbinden:** Wenn diese Option **Aktiviert** ist, stellt das Gerät automatisch eine Verbindung mit dem VPN her, wenn ein Gerät mit einer Domäne Kontakt aufnimmt, die Sie eingeben, z.B. „contoso.com“.
- **Persistent:** Standardmäßig sind alle Regeln der Namensauflösungsrichtlinie-Tabelle (Name Resolution Policy Table, NRPT) aktiv, solange das Gerät über dieses VPN-Profil verbunden ist. Wenn diese Einstellung für eine NRPT-Regel **aktiviert** ist, bleibt die Regel auch dann auf dem Gerät aktiv, wenn das VPN getrennt ist. Die Regel bleibt in Kraft, bis das VPN-Profil entfernt wird oder bis die Regel manuell entfernt wird – dies kann über PowerShell erfolgen.
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) werden die Einstellungen beschrieben. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Verwenden vertrauenswürdiger Netzwerkerkennung für VPN-Profile auf Windows 10-Geräten <!-- 1500165 -->
Wenn Sie die Erkennung vertrauenswürdiger Netzwerke verwenden, können Sie verhindern, dass VPN-Profile automatisch eine VPN-Verbindung herstellen, wenn der Benutzer sich bereits in einem vertrauenswürdigen Netzwerk befindet. Sie können DNS-Suffixe zum Aktivieren der Erkennung vertrauenswürdiger Netzwerke auf Geräten mit Windows 10 und höher hinzufügen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** als Plattform und **VPN** als Profiltyp).
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) sind die aktuellen VPN-Einstellungen aufgeführt.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Verwalten von Windows Holographic for Business-Geräten, die von mehreren Benutzern verwendet werden <!-- 1907917, 1063203 -->
Derzeit können Sie gemeinsame PC-Einstellungen auf Windows 10- und Windows Holographic for Business-Geräten mithilfe einer benutzerdefinierten OMA-URI-Einstellung konfigurieren. Mit diesem Update wird ein neues Profil zum Konfigurieren gemeinsamer PC-Einstellungen hinzugefügt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Freigegebenes, von mehreren Benutzern verwendetes Gerät**).
Im Artikel zu [Intune-Einstellungen zum Verwalten gemeinsam verwendeter Geräte](shared-user-device-settings.md) erfahren Sie mehr zu diesem Feature.
Gilt für: Windows 10 und höher, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Neue Windows 10-Updateeinstellungen <!--2626030  2512994  -->
Für Ihre [Windows 10-Updateringe](windows-update-for-business-configure.md) können Sie folgende Konfigurationen vornehmen:
- **Verhalten bei automatischen Updates**: Verwenden Sie die neue Option *Standard wiederherstellen* zum Wiederherstellen der ursprünglichen Einstellungen für automatische Updates auf einem Windows 10-Computer auf Computern, die das *Oktober 2018-Update* ausführen
- **Verweigern des Anhalten eines Updates**: Konfigurieren Sie eine neuen Softwareupdateseinstellung, mit der Sie blockieren oder zulassen können, dass Ihre Benutzer Updateinstallationen über die *Einstellungen* ihrer Computer anhalten. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS-E-Mail-Profile können S/MIME-Signatur und -Verschlüsselung verwenden <!-- 2662949 -->
Sie können ein E-Mail-Profil erstellen, das unterschiedliche Einstellungen enthält. Dieses Update umfasst S/MIME-Einstellungen, die zum Signieren und Verschlüsseln der E-Mail-Kommunikation auf iOS-Geräten verwendet werden können (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **E-Mail** als Profiltyp aus).
Unter [iOS-E-Mail-Konfigurationseinstellungen](email-settings-ios.md) werden die Einstellungen aufgelistet.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Einige BitLocker-Einstellungen unterstützen die Windows 10 Pro-Edition<!-- 2727036 -->
Sie können ein Konfigurationsprofil erstellen, das die Endpunktschutzeinstellungen auf Windows 10-Geräten einschließlich BitLocker festlegt. Mit diesem Update wird die Unterstützung für Windows 10 Professional für einige BitLocker-Einstellungen hinzugefügt. Diese Schutzeinstellungen finden Sie unter [Endpoint protection settings for Windows 10 (Endpunktschutzeinstellungen für Windows 10)](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>„Konfiguration freigegebener Geräte“ wurde für iOS-Geräte im Azure-Portal in „Nachricht auf Sperrbildschirm“ umbenannt<!-- 2809362 -->
Bei der Erstellung eines Konfigurationsprofils für iOS-Geräte können Sie **Konfigurationen für gemeinsam verwendete Geräte** vornehmen, um einem bestimmten Text auf dem Sperrbildschirm anzuzeigen. Dieses Update umfasst folgende Änderungen: 
- Die **Konfiguration freigegebener Geräte**-Einstellungen im Azure-Portal werden umbenannt in „Nachricht auf Sperrbildschirm (nur überwacht)“ (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **Gerätefunktionen** als Profiltyp aus, wählen Sie **Nachricht auf Sperrbildschirm** aus).
- Beim Hinzufügen von Sperrbildschirmnachrichten können Sie eine Seriennummer, einen Gerätenamen oder einen anderen gerätespezifischen Wert als Variable in **Bestandskennzeicheninformationen** und einer **Fußnote im Sperrbildschirm** einfügen. Sie können z.B. `Device name: {{devicename}}` oder `Serial number is {{serialnumber}}` mit geschweiften Klammern eingeben. [iOS-Token](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) listet die verfügbaren Token auf, die verwendet werden können.
In den [Einstellungen zur Anzeige von Nachrichten auf dem Sperrbildschirm](shared-device-settings-ios.md) werden die aktuellen Einstellungen aufgelistet.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Neue Einstellungen für App Store, Dokumentanzeige, Gaminggeräteeinschränkungen auf iOS-Geräten <!-- 2827760-->
Unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** als Plattform, **Geräteeinschränkungen** als Profiltyp und **App Store, Dokumentanzeige, Spiele** wurden die folgenden Einstellungen hinzugefügt: „Verwaltete Apps können Kontakt in nicht verwaltete Kontaktkonten schreiben“, „Nicht verwaltete Apps können aus verwalteten Kontaktkonten lesen“. In der [Liste der Einstellungen für iOS-Geräteeinschränkungen](device-restrictions-ios.md#app-store-doc-viewing-gaming) können Sie sich diese Einstellungen ansehen.

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Neue Benachrichtigungen, Hinweise und Keyguard-Einstellungen für Geräte von Android Enterprise-Gerätebesitzern <!-- 3201839 3201843 -->
Dieses Update umfasst mehrere neue Features für Android Enterprise-Geräte bei Ausführung als Gerätebesitzer. Um diese Features zu verwenden, wechseln Sie zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie als **Plattform** **Android Enterprise** und als **Profiltyp** **Nur Gerätebesitzer** > **Geräteeinschränkungen** aus.

Neue verfügbare Funktionen: 

- Deaktivieren der Anzeige von Systembenachrichtigungen einschließlich eingehender Anrufe, Systemwarnungen, Systemfehler und mehr.
- Das Überspringen des Startens von Tutorials und von Hinweisen für Apps, die erstmals geöffnet werden, wird vorgeschlagen.
- Deaktivieren erweiterter Keyguard-Einstellungen, z.B. Kamera, Benachrichtigungen, Fingerabdruckentsperrung und mehr.


Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Geräte von Android Enterprise-Gerätebesitzern können Always On-VPN-Verbindungen verwenden <!-- 3202194 -->
In diesem Update können Sie Always On-VPN-Verbindungen mit Geräten von Android Enterprise-Gerätebesitzern verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Sie können Always On-VPN wie folgt aktivieren: Wählen Sie in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** als Plattform, **Geräteeinschränkungen** für „Nur Gerätebesitzer“ und die Einstellungen für **Konnektivität** aus. Weitere Informationen finden Sie unter [Android Enterprise-Geräteeinstellungen](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Neue Einstellung zum Beenden von Prozessen im Task-Manager auf Windows 10-Geräten <!-- 3285177 --> 
Dieses Update umfasst eine neue Einstellung für Endprozesse im Task-Manager auf Windows 10-Geräten. Mithilfe eines Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform**  **Windows 10** und für **Profiltyp** **Geräteeinschränkungen** > **Allgemein** aus) lassen Sie diese Einstellung zu oder verhindern sie.
Weitere Informationen finden Sie unter [Einstellungen für Geräteeinschränkungen für Windows 10](device-restrictions-windows-10.md).
Gilt für: Windows 10 und höher


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Ausführlicheres Messaging zu Registrierungseinschränkungsfehlern <!-- 3111564 -->
Wenn die Einschränkungen für die Registrierung nicht erfüllt werden, werden nun aussagekräftigere Fehlermeldungen ausgegeben. Um diese Meldungen anzuzeigen, wechseln Sie zu **Intune** > **Problembehandlung**, und überprüfen Sie die Tabelle „Registrierungsfehler“. Weitere Informationen finden Sie in der Liste mit den [Registrierungsfehlern](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard zum Mandantenstatus  <!-- 1124854 -->
Auf der neuen Seite mit dem [Mandantenstatus](tenant-status.md) können Sie auf einen Blick den Status Ihres Mandanten und damit verbundene Informationen sehen.  Dieses Dashboard ist in vier Bereiche unterteilt:
- **Tenant Details** (Mandantendetails): Hier werden z. B. Ihre MDM-Autorität, die insgesamt bei Ihrem Mandanten angemeldeten Geräte und die Anzahl Ihrer Lizenzen angezeigt. In diesem Abschnitt wird auch die aktuelle Dienstversion für Ihren Mandanten angezeigt.
- **Connector Status** (Connectorstatus): Hier werden Informationen zu verfügbaren konfigurierten Connectors angezeigt und deaktivierte Connectors aufgelistet.  
   Basierend auf ihrem aktuellen Status werden die Connectors als „Healthy“ (Fehlerfrei), „Warning“ (Warnung) oder „Unhealthy“ (Fehlerhaft) gekennzeichnet. Wählen Sie einen Connector aus, den Sie sich genauer ansehen möchten, und zeigen Sie weitere Details an, oder konfigurieren Sie zusätzliche Informationen.
- **Intune Service Health** (Intune-Dienstintegrität): Hier werden aktive Vorfälle oder Ausfälle für Ihren Mandanten angezeigt. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen.
- **Intune News** (Neuigkeiten zu Intune): Hier werden aktive Meldungen Ihres Mandanten angezeigt. Dazu zählen u. a. Benachrichtigungen zu den neuesten Intune-Features.  Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Neue Hilfe- und Supportbenutzeroberfläche im Unternehmensportal für Windows 10 <!-- 1488939-->
Über die neue Seite für Hilfe und Support im Intune-Unternehmensportal können Benutzer Probleme beheben und Hilfe zu App- und Zugriffsproblemen erhalten. Über die neue Seite können sie Informationen zu Fehler- und Diagnoseprotokollen per E-Mail versenden und Informationen zum Helpdesk ihrer Organisation erhalten. Zudem gibt es einen Bereich mit häufig gestellten Fragen und Links zu relevanten Intune-Dokumentationsartikeln. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Neue Benutzeroberfläche für Hilfe und Support für Intune   <!-- #3307080 -->
Innerhalb der nächsten Tage wird diese neue Hilfe- und Supportbenutzeroberfläche für alle Mandanten verfügbar gemacht. Diese neue Benutzeroberfläche ist für Intune verfügbar und kann über das Blatt „Intune“ im [Azure-Portal](https://portal.azure.com/) verwendet werden.
Über die neue Benutzeroberfläche können Sie Ihr Problem in eigenen Worten beschreiben und erhalten Einblicke in die Problembehandlung sowie webbasierte Anleitungen zur Selbsthilfe. Diese Lösungen werden über einen regelbasierten Algorithmus für maschinelles Lernen angeboten, der auf Benutzeranfragen basiert. Zusätzlich zur themenspezifischen Anleitung können Sie auch den neuen Workflow zur Anfragestellung nutzen, um eine Supportanfrage per E-Mail oder Telefon zu stellen. Diese neue Benutzeroberfläche ersetzen die alte Benutzeroberfläche für Hilfe und Support, die statische, vorab ausgewählte Optionen enthielt. Diese basieren auf dem Bereich der Konsole, in dem Sie sich befinden, wenn Sie „Hilfe und Support“ öffnen. Weitere Informationen finden Sie unter [Anfordern von Support für Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-for-apps----1081941---"></a>Bereichsmarkierungen für Apps <!-- 1081941 -->
Sie können Bereichsmarkierungen erstellen, um den Zugriff für Rollen und Apps einzuschränken. Sie können einer App eine Bereichsmarkierung hinzufügen, sodass nur Benutzer mit der gleichen Bereichsmarkierung wie die App auf diese zugreifen können. Derzeit können Apps, die Intune über den verwalteten Google Play Store hinzugefügt wurden oder die mithilfe des Apple Volume Purchase Program (VPP) erworben wurden, keine Bereichsmarkierungen hinzugefügt werden (zukünftige Unterstützung dafür ist geplant). Weitere Informationen finden Sie unter [Use scope tags to filter policies (Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien)](scope-tags.md).

## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
