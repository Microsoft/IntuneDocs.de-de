---
title: Bei der Entwicklung - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-Funktionen in der Entwicklung
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587381"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>Bei der Entwicklung für Microsoft Intune – April 2019

Für Ihre Bereitschaft und planen, diese Seite enthält, die Intune UI aktualisiert und die features dieses Produkts, sind in der Entwicklung, aber noch nicht veröffentlicht wurden. Zusätzlich:

- Wenn wir davon ausgehen, dass Sie eine Aktion vor einer Änderung müssen, veröffentlichen wir ergänzende Post Office-Nachrichtencenter.
- Wenn eine Funktion wird entweder als Vorschau in der Produktion gestartet oder allgemein verfügbar ist, der featurebeschreibung wird verschieben außerhalb dieser Seite und auf die [neuerungen neue Seite](whats-new.md).
- Auf dieser Seite und die [neuerungen neue Seite](whats-new.md) in regelmäßigen Abständen aktualisiert werden. Überprüfen Sie, ob weitere Updates vorliegen.
- Finden Sie in der [M365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) für strategische lieferleistungen und Zeitpläne.

> [!Note]
> Diese Elemente entsprechen Microsofts aktuelle Erwartungen über Intune-Funktionen, die in einer zukünftigen Version verfügbar. Datums- und einzelne Funktionen möglicherweise ändern. Nicht alle Elemente in der Entwicklung haben eine funktionsbeschreibung auf dieser Seite.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>Festlegen Sie anmeldeeinstellungen und steuern Sie die Neustartoptionen auf MacOS-Geräten <!-- 1210083 -->
Klicken Sie auf MacOS-Geräten können Sie ein gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Wählen Sie **MacOS** für Plattform > **Gerätefunktionen** für Profiltyp). Neue Einstellungen für Anmeldung wird umfassen Elemente wie ein benutzerdefiniertes Banner angezeigt, wählen Sie, wie Benutzer melden Sie sich, anzeigen oder Ausblenden der energieeinstellungen und vieles mehr.

Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [Feature-Einstellungen für MacOS-Geräte](macos-device-features-settings.md).

Gilt für: MacOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Erweiterte Einstellungen für Windows Defender Firewall <!-- 1311949 -->
Sie werden bald Intune zum Verwalten von auf Clients für Windows Defender die benutzerdefinierte Firewallregeln verwenden können. Regeln können eingehenden und ausgehenden Verhalten für Anwendungen, die Netzwerkadressen und Ports angeben. 

### <a name="require-app-protection-conditional-access----1634317---"></a>Bedingter Zugriff auf App-Schutz erforderlich  <!--1634317 -->
Sie verwenden, werden *erfordern App-Schutzrichtlinie*, was bestätigt, dass Richtlinie App des Benutzers angewendet wird, bevor die Anmeldung abgeschlossen ist, um zu verhindern, dass Benutzer den Zugriff auf Daten, die Sie schützen, mit dem bedingten Zugriff. Während die erste Verwendung Erfahrung Richtlinie Assurance verlangsamen kann, ist es zum Schutz vor Netzwerkprobleme, administrative Fehlkonfigurationen oder absichtlich den anwendungsschutzrichtlinien dadurch hilfreich. 

### <a name="retire-noncompliant-devices----1827291---"></a>Nicht kompatible Geräte abkoppeln <!-- 1827291 -->
Wir werden eine neue Compliance-Aktion, um ein nicht konformes Gerät abkoppeln hinzufügen. Ein nicht konformes Gerät abkoppeln entfernt alle Unternehmensdaten aus und entfernt auch das Gerät von Intune verwaltet werden. Diese Aktion ausgeführt wird, wenn der konfigurierte Wert in Tagen erreicht wird. Der Mindestwert beträgt 30 Tage. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>Konfigurieren von Einstellungen für Kernelerweiterungen auf MacOS-Geräte <!-- 2043024 -->
Klicken Sie auf MacOS-Geräten können Sie ein gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Wählen Sie **MacOS** für Plattform). Eine neue Gruppe von Einstellungen können Sie konfigurieren und Verwenden von Kernelerweiterungen auf Ihren Geräten.

Gilt für: macOS 10.13.2 und höher

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Konfigurieren des Profils zum Überspringen einiger Bildschirme während des Setup-Assistenten <!-- 2276470 -->
Wenn Sie ein macOS-Registrierungsprofil erstellen, können Sie dieses konfigurieren, um folgende Bildschirme zu überspringen, wenn ein Benutzer den Setup-Assistenten durchläuft:
- Android-Migration
- Anzeigefarbton
- Datenschutz
- iCloudStorage: Wenn Sie ein neues Profil erstellen oder ein Profil bearbeiten, müssen die ausgewählten zu überspringenden Bildschirme mit dem Apple MDM-Server synchronisiert werden. Benutzer können eine manuelle Synchronisierung der Geräte durchführen, sodass es keine Verzögerung bei der Auswahl der Profiländerungen gibt.
Weitere Informationen finden Sie unter [Automatisches Registrieren von macOS-Geräten mit dem Programm zur Geräteregistrierung oder Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Sie installiert haben oder die versucht haben, installieren, können Benutzer von Geräten alle verwalteten apps anzeigen. <!-- 2352913 -->
Unternehmens-Portal für Windows listet alle verwalteten apps&ndash; erforderliche sowie verfügbare&ndash; auf dem Gerät eines Benutzers installiert werden. Benutzer werden können Sie zum Anzeigen, die versucht und ausstehende Anwendungsinstallationen und der aktuelle Status. Wenn apps in Ihrer Organisation nicht erforderlich oder verfügbar machen, wird Benutzern angezeigt, eine Meldung darüber informiert, dass keine Unternehmens-apps installiert wurden. Benutzer werden auch in der Lage, sortieren oder Filtern ihre apps durch Installationsstatus.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Bereichsmarkierungen für Apple-VPP-Token <!--2371886 -->
Sie werden bereichsmarkierungen Apple-VPP-Token hinzufügen. Nur Benutzer, die mit dem gleichen Bereich Tag zugewiesen haben Zugriff auf die Apple VPP-Token mit diesem Tag. VPP-apps und e-Books, die mit dem Token erworben haben, dessen bereichsmarkierungen erben. Weitere Informationen zu bereichsmarkierungen, finden Sie unter [Tags mithilfe von RBAC und Bereich](scope-tags.md).

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Verwenden Sie "Anwendbarkeitsregeln" beim Erstellen von Windows 10-Gerät-Konfigurationsprofile <!-- 2549910 -->
Erstellen Sie Windows 10-Gerät von Konfigurationsprofilen (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10** für Plattform). Können zum Erstellen einer **anwendbarkeitsregel** damit das Profil nur auf eine bestimmte Edition oder eine bestimmte Version angewendet wird. Beispielsweise erstellen Sie ein Profil, das einige BitLocker-Einstellungen aktiviert. Nachdem Sie das Profil hinzugefügt haben, verwenden Sie eine anwendbarkeitsregel, so dass das Profil gilt nur für Geräte mit Windows 10 Enterprise.

Gilt für: 
- Windows 10 und höher

### <a name="enable-win32-app-dependencies----2617348---"></a>Aktivieren Sie die Win32-app-Abhängigkeiten <!-- 2617348 -->
Öffentliche Vorschau – als Administrator, Sie werden zu fordern, dass andere apps als Abhängigkeiten installiert werden, bevor Sie Ihre Win32-app installieren können. Insbesondere muss das Gerät die abhängigen Apps installieren, bevor sie die Win32-app installiert. Diese Funktionalität wird verfügbar sein, nur, nachdem der Intune-Verwaltungs-Agent auf 1904-Version (größer als 1.18.120.0) dieser Vorgang kann 1 oder 2 Weitere Wochen aktualisiert wurde, nachdem wir den Dienst auf 1904 aktualisiert. Wählen Sie in Intune **Client-apps** > **Apps** > **hinzufügen** zum Anzeigen der **app hinzufügen** Blatt. Wählen Sie **Windows-app (Win32)** als die **App-Typ**. Weitere Informationen finden Sie unter [Intune Standalone - Win32-app-Verwaltung](apps-win32-app-management.md).

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Neue Einstellungen für geräteeinschränkungen für Android Enterprise Eigentümer des Geräts: ermöglichen Sie Benutzern die Verbindung mit Wi-Fi-Netzwerke auf Android Enterprise dedizierte-Geräten, die mit Multi-app-Kiosk-Modus <!--3041940 -->
Administratoren werden können, um eine neue Einstellung umzuschalten, mit der Benutzer Bluetooth auf ihren Android Enterprise dedizierte-Geräten mit Multi-app-Kiosk-Modus konfigurieren können. Wählen Sie zum Anzeigen dieser Einstellung in der Intune-Konsole **Intune** > **Gerätekonfiguration** > **Profile**  >  **Profil erstellen** > Wählen Sie **Android Enterprise** für Plattform > **nur gerätebesitzer, geräteeinschränkungen** für Profiltyp > **Einstellungen**   >  **Dedizierte Geräte** > Wählen Sie **mit mehreren Apps** aus der **Kiosk-Modus** Dropdown-Einstellung. Eine Option namens **WLAN-Konfiguration** zur Verfügung zu aktivieren. 

Gilt für: Android Enterprise dedizierte Geräte, die Multi-app-Kiosk-Modus ausgeführt. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Neue Einstellungen für geräteeinschränkungen für Android Enterprise Eigentümer des Geräts: können Benutzer konfigurieren, Bluetooth und auf Geräten mit Android Enterprise dedizierte Kopplung <!--3041941 -->
Administratoren werden können, um eine neue Einstellung umzuschalten, mit der Benutzer Bluetooth auf ihren Android Enterprise dedizierte-Geräten mit Multi-app-Kiosk-Modus konfigurieren können. Wählen Sie zum Anzeigen dieser Einstellung in der Intune-Konsole **Intune** > **Gerätekonfiguration** > **Profile**  >  **Profil erstellen** > Wählen Sie **Android Enterprise** für Plattform > **nur gerätebesitzer, geräteeinschränkungen** für Profiltyp > **Einstellungen**   >  **Dedizierte Geräte** > Wählen Sie **mit mehreren Apps** aus der **Kiosk-Modus** Dropdown-Einstellung. Eine Option namens **Bluetooth-Konfiguration** zur Verfügung zu aktivieren. 

Gilt für: Android Enterprise dedizierte Geräte, die Multi-app-Kiosk-Modus ausgeführt. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Überwachen des Status der Sicherheitsbaseline (öffentliche Vorschau) <!-- 3082047 --> 
Bei der Überwachung der *Gerätestatus* für Ihre Sicherheitsfunktionen, die Ansicht organisiert den Status durch die Baseline-Kategorien, z. B. *Sperrbildschirm*, *BitLocker*, und  *Browser*. Alle verfügbaren Baseline-Kategorien werden dargestellt werden. Für jede Kategorie sehen Sie, wie viele Geräte eine bestimmte Baseline-Kategorie stimmen nicht überein, sind falsch konfiguriert oder sind nicht anwendbar.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Intune Sicherheitsaufgaben Defender ATP (In der öffentlichen Vorschau) <!-- 3208597 -->
Als öffentliche Vorschau verfügbar, wird Intune schnell Sicherheitsaufgaben für die neu angekündigten Microsoft Defender Threat & Verwaltung von Sicherheitsrisiken hinzugefügt.  Mit dieser Integration können Vorgänge Sicherheitsadministratoren in Windows Defender ATP (WDETP) effektiver der empfohlenen Wiederherstellungsmaßnahmen für neue Bedrohungen für Intune-Administratoren kommunizieren. Das Hinzufügen von Sicherheitsaufgaben Fügt einen anmelderisiko basierenden Ansatz zum entdecken, zu priorisieren und Endpunkt Sicherheitslücken und Konfigurationsfehler zu beheben.

Um weitere Informationen zur von Sicherheitsaufgaben in Intune finden Sie im Blogbeitrag zu [Erweitern von Microsoft Defender ATP mindern von Bedrohungen und Verwaltung von Sicherheitsrisiken mithilfe von Intune Sicherheitsaufgaben](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Erstellen und Verwenden von OEMConfig gerätekonfigurationsprofile in Intune <!-- 3305883 -->
Intune unterstützt die Konfiguration von Android Enterprise-Geräten mit OEMConfig. Insbesondere ein gerätekonfigurationsprofil erstellen werden können, und wenden Sie Einstellungen für Android Enterprise-Geräte, die mit OEMConfig (**Gerätekonfiguration** > **Profile**  >  **Profil erstellen** > **Android Enterprise** für Plattform).

Support für OEMs ist derzeit auf einer pro-OEM-Basis. Wenn eine OEMConfig app Sie nicht in der Liste der OEMConfig apps verfügbar ist, wenden Sie sich an `IntuneOEMConfig@microsoft.com`.

Gilt für: 
- Android Enterprise

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Neue Einstellungen für geräteeinschränkungen für Android Enterprise Eigentümer des Geräts <!-- 3574254 -->
Auf Android Enterprise-Geräte können Sie ein Profil für geräteeinschränkungen zum Zulassen und beschränken Features, Kennwortregeln festlegen und vieles mehr erstellen (**Gerätekonfiguration** > **Profile**  >  **Profil erstellen** > Wählen Sie **Android Enterprise** für Plattform > **nur gerätebesitzer > geräteeinschränkungen** für Profiltyp). 

Neue Einstellungen, einschließlich der kennworteinstellungen, sodass vollständigen Zugriff auf Apps in Google Play Store für vollständig verwaltete Geräte, und weitere werden zur Verfügung stehen. 

Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](device-restrictions-android-for-work.md). 

Gilt für: Android Enterprise vollständig verwaltete Geräte

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Überprüfen Sie für eine TPM-Chipsatz in einer Konformitätsrichtlinie für Windows 10-Gerät <!-- 3617671 -->
Viele Windows 10 und höher haben Chipsätzen von Trusted Platform Module (TPM). Eine neue konformitätseinstellung überprüft, ob ein TPM auf dem Gerät ist.

[Windows 10 und höher kompatibilitätsrichtlinieneinstellungen](compliance-policy-create-windows.md) werden die aktuellen Einstellungen aufgeführt.

Gilt für: 
- Windows 10 und höher

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Konfigurieren Sie Ihre Win32-apps in Intune registrierten installiert werden Azure AD eingebundene Geräte <!-- 3695227 -->
Sie müssen möglicherweise weisen Sie Ihre Win32-apps zu Intune installiert werden, Azure AD registriert eingebundenen Geräten. Weitere Informationen über Win32-apps in Intune finden Sie unter [Win32-app-Verwaltung](apps-win32-app-management.md).

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Baseline für Windows Defender Advanced Threat Protection <!-- 3754134 -->
Wir werden die hinzuzufügende neue Baseline, damit Sie die Windows Defender Advanced Threat Protection-Einstellungen konfigurieren können.

### <a name="device-overview-shows-primary-user---794259---"></a>Geräteübersicht zeigt Primärbenutzer <!--794259 -->
Übersicht über die Seite mit dem Geräte wird der Primärbenutzer, die so genannte User Device Affinity Benutzer (UDA) angezeigt. Wählen Sie zum Anzeigen der Primärbenutzer für ein Gerät **Intune** > **Geräte** > **alle Geräte** > Wählen Sie ein Gerät. Der Primärbenutzer erscheint im oberen Bereich des der **Übersicht** Seite.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Erweiterter Unterstützung für Android Enterprise, vollständig verwaltete Geräte <!-- 3903241, 3903244, 3903246 -->
Wir erweitern die Unterstützung von Geräten mit Android Enterprise vollständig verwaltete wollen ([erstmals im Januar des 2019 angekündigt](whats-new.md#week-of-january-14-2019) Folgendes einschließen:
- Konformität
- Bedingter Zugriff
- Neuen Endbenutzer App

Um vollständig verwaltete Android-Geräte einzurichten, wechseln Sie zu **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte**. Unterstützung für vollständig verwaltete Android-Geräte weiterhin in der Vorschau, und einige Intune-Features möglicherweise nicht voll funktionsfähig sein. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Zusätzliche verwaltetes Google Play-app-berichterstellung für Geräte mit Arbeitsprofil Android Enterprise <!-- 4105925 -->
Verwaltetes Google Play-apps für Android Enterprise-arbeitsprofilgeräte bereitgestellt werden es möglich, zeigen Sie die Versionsnummer der app auf einem Gerät installiert. Dies gilt für nur erforderliche apps. Die gleiche Funktionalität für verfügbare apps wird in einer zukünftigen Version aktiviert.

### <a name="ios-third-party-keyboards----4111843---"></a>Tastaturen von Drittanbietern für iOS <!-- 4111843 -->
Unterstützung für Intune-app-Schutzrichtlinien (APP) für die **von Drittanbietern Tastaturen** Einstellung endet aufgrund einer Änderung der iOS-Plattform. Sie werden nicht in der Lage, diese Einstellung in der Intune-Verwaltungskonsole konfigurieren, und es wird nicht auf dem Client in das Intune App SDK erzwungen werden.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>Suche nach Windows Updates den Benutzer blockieren <!-- 3316758 -->
Wir fügen eine neue Windows Update-Ring-Einstellung, mit denen Sie für Benutzer die Überprüfung auf Windows-Updates blockieren. Diese Einstellung nicht in das Portal verfügbar, aber Sie können mithilfe der Graph-API von Intune konfiguriert werden.

### <a name="windows-update-notifications----3316782---"></a>Windows Update-Benachrichtigungen <!-- 3316782 -->
Wir fügen Unterstützung an den Windows Update Ring Konfigurationen sodass Sie die Windows Update-Benachrichtigungen zu konfigurieren, die den Benutzern angezeigt werden können. Diese Einstellung nicht in das Portal verfügbar, aber Sie können mithilfe der Graph-API von Intune konfiguriert werden.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>Einfacher Zugriff auf die Diagnoseeinstellungen für <!-- 3804627 -->
Fügen wir eine neue Option, um die **Überwachungsprotokolle** auf dem Blatt für jede Workload Überwachungsprotokoll geschrieben, in der Intune-Verwaltungskonsole, die Sie verwenden können, um direkt zu öffnen der *Diagnoseeinstellungen* Seite.

## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


