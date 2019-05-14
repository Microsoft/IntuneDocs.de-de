---
title: Bei der Entwicklung - Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-Funktionen in der Entwicklung
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910326"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Bei der Entwicklung für Microsoft Intune – Mai 2019

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Das Löschen eines Geräts im Apple-Portal wird im Intune-Portal angezeigt werden <!--2489996 -->
Wenn ein Gerät aus dem Apple Geräteregistrierungsprogramm oder Apple-Business-Manager-Portale gelöscht wird, wird das Gerät während der nächsten Synchronisierung automatisch aus Intune gelöscht.

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Baseline-Unterstützung für Schlüsselwort suchen.  <!-- 3082036         -->
Beim Erstellen oder Bearbeiten einer Security Baseline-Profil, Sie werden in Kürze mit *Suche* um die Einstellungen zu filtern, die in der Konsole angezeigt.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Zurücksetzen und Zurücksetzen von Geräten in einer Massenoperation mithilfe der Graph-API <!-- 3295288 -->
Sie werden zurückgesetzt und bis zu 100 Geräte mithilfe der Graph-API zurücksetzen können.

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie <!-- 3617671 -->
Viele Windows 10 und höher haben Chipsätzen von Trusted Platform Module (TPM). Dieses Update enthält eine neue konformitätseinstellung, die die TPM-Chip-Version auf dem Gerät überprüft wird. 

[Windows 10 und höher kompatibilitätsrichtlinieneinstellungen](compliance-policy-create-windows.md#device-security) beschreibt diese Einstellung.

Gilt für: Windows 10 und höher

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Intune-Verwaltung Erweiterung PowerShell-Skripts  <!-- 3734186    -->
Sie werden können zum Konfigurieren von PowerShell-Skripts mit Administratorrechte des Benutzers auf dem Gerät ausgeführt. Weitere Informationen finden Sie unter [mithilfe von PowerShell-Skripts auf Windows 10-Geräte in Intune](intune-management-extension.md).

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>Verhindern, dass Benutzer ihre privaten HotSpot ändern und Deaktivieren von Siri-Server, die Protokollierung von überwachten Geräten unter iOS <!-- 4097904  --> 
Sie erstellen ein Profil für geräteeinschränkungen für iOS-Gerät (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **iOS** für Plattform > **geräteeinschränkungen** für Profiltyp). Dieses Update umfasst neue Einstellungen, die Sie konfigurieren können:

- Privater Hotspot:
- Webserverprotokollierung

Eine Liste der verfügbaren Einstellungen finden Sie unter [Device settings to allow or restrict features (Geräteeinstellungen zum Zulassen oder Einschränken von Features)](device-restrictions-ios.md). 

Gilt für: iOS 12.2 und höher

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>Neue Classroom-Appeinstellungen für geräteeinschränkungen für DEP-registrierte MacOS-Geräte <!-- 4097905  --> 
Sie können gerätekonfigurationsprofile für MacOS-Geräte erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **MacOS** für Plattform > **geräteeinschränkungen** für Profiltyp). Dieses Update enthält neue Classroom-app-Einstellungen für DEP-registrierte Geräte und die Option zum Deaktivieren der iCloud-Fotomediathek.

Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [Einstellungen für MacOS-Geräte zum Zulassen und beschränken die Funktionen, die mit Intune](device-restrictions-macos.md).

Gilt für: macOS 10.14.4 und höher

### <a name="android-enterprise-app-management----4459905-idready---"></a>Android Enterprise-app-Verwaltung <!-- 4459905 idready -->
Damit es einfacher für IT-Administratoren zum Konfigurieren und verwenden die Android Enterprise-Management, Intune wird automatisch hinzugefügt vier allgemeine Android Enterprise apps mit der Intune-Verwaltungskonsole verknüpft. Die vier Android Enterprise-apps sind die folgenden:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)**  : für Android vollständig verwaltete Unternehmensszenarios verwendet.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**  -können Sie anmelden, um Ihre Konten, wenn Sie die zweistufige Überprüfung verwenden.
- **[Intune-Unternehmensportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)**  : für App-Protection-Richtlinien (APP) und Szenarien für Android Enterprise Work-Profil verwendet.
- [Verwaltete Startbildschirm](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : für Android Enterprise-dedizierte/Kiosk-Szenarios verwendet.

Bisher mussten IT-Administratoren manuell suchen und genehmigen diese apps in der [verwaltetes Google Play Store](https://play.google.com/store/apps) als Teil des Setups. Diese Änderung entfernt die zuvor manuelle Schritte zum vereinfachen und beschleunigen für Kunden, die Android Enterprise-Management verwendet.

Administratoren sehen diese vier apps automatisch auf die Zeit, dass sie ihre Intune-Mandanten zum ersten Mal mit verwaltetem Google Play verbinden ihre Intune-apps-Liste hinzugefügt. Weitere Informationen finden Sie unter [Ihr Intune-Konto mit Ihrem verwaltetes Google Play-Konto verbinden](connect-intune-android-enterprise.md). Für Mandanten, die ihren Mandanten bereits verbunden haben, oder bereits Android Enterprise verwenden gibt es nichts, was Administratoren tun müssen. Diese vier apps werden automatisch innerhalb von 7 Tagen, über den Abschluss der Bereitstellung der Mai 2019-Dienst angezeigt.

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Erweiterte Einstellungen für Windows Defender Firewall <!-- 1311949 -->
Sie werden bald Intune zum Verwalten von auf Clients für Windows Defender die benutzerdefinierte Firewallregeln verwenden können. Regeln können eingehenden und ausgehenden Verhalten für Anwendungen, die Netzwerkadressen und Ports angeben. 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Sie installiert haben oder die versucht haben, installieren, können Benutzer von Geräten alle verwalteten apps anzeigen. <!-- 2352913 -->
Unternehmens-Portal für Windows listet alle verwalteten apps&ndash; erforderliche sowie verfügbare&ndash; auf dem Gerät eines Benutzers installiert werden. Benutzer werden können Sie zum Anzeigen, die versucht und ausstehende Anwendungsinstallationen und der aktuelle Status. Wenn apps in Ihrer Organisation nicht erforderlich oder verfügbar machen, wird Benutzern angezeigt, eine Meldung darüber informiert, dass keine Unternehmens-apps installiert wurden. Benutzer werden auch in der Lage, sortieren oder Filtern ihre apps durch Installationsstatus.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Verwenden Sie "Anwendbarkeitsregeln" beim Erstellen von Windows 10-Gerät-Konfigurationsprofile <!-- 2549910 -->
Erstellen Sie Windows 10-Gerät von Konfigurationsprofilen (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10** für Plattform). Können zum Erstellen einer **anwendbarkeitsregel** damit das Profil nur auf eine bestimmte Edition oder eine bestimmte Version angewendet wird. Beispielsweise erstellen Sie ein Profil, das einige BitLocker-Einstellungen aktiviert. Nachdem Sie das Profil hinzugefügt haben, verwenden Sie eine anwendbarkeitsregel, so dass das Profil gilt nur für Geräte mit Windows 10 Enterprise.

Gilt für: 
- Windows 10 und höher

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Intune Sicherheitsaufgaben Defender ATP (In der öffentlichen Vorschau) <!-- 3208597 -->
Als öffentliche Vorschau verfügbar, wird Intune schnell Sicherheitsaufgaben für die neu angekündigten Microsoft Defender Threat & Verwaltung von Sicherheitsrisiken hinzugefügt.  Mit dieser Integration können Vorgänge Sicherheitsadministratoren in Windows Defender ATP (WDETP) effektiver der empfohlenen Wiederherstellungsmaßnahmen für neue Bedrohungen für Intune-Administratoren kommunizieren. Das Hinzufügen von Sicherheitsaufgaben Fügt einen anmelderisiko basierenden Ansatz zum entdecken, zu priorisieren und Endpunkt Sicherheitslücken und Konfigurationsfehler zu beheben.

Um weitere Informationen zur von Sicherheitsaufgaben in Intune finden Sie im Blogbeitrag zu [Erweitern von Microsoft Defender ATP mindern von Bedrohungen und Verwaltung von Sicherheitsrisiken mithilfe von Intune Sicherheitsaufgaben](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Baseline für Windows Defender Advanced Threat Protection <!-- 3754134 -->
Wir werden die hinzuzufügende neue Baseline, damit Sie die Windows Defender Advanced Threat Protection-Einstellungen konfigurieren können.



## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


