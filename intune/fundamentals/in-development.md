---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7113552e09a7c7fa145a452e56575bfaf5297c3e
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514562"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>In der Entwicklung befindliche Microsoft Intune-Features: Februar 2020

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich zu den Informationen auf dieser Seite gilt Folgendes: 

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office-Nachrichtencenter veröffentlichen.
- Wenn ein Feature in die Produktionsumgebung wechselt, wird die Featurebeschreibung von dieser Seite auf die Seite [Neuerungen in Microsoft Intune](whats-new.md) verschoben, unabhängig davon, ob es sich um eine Vorschauversion handelt oder ob das Feature bereits allgemein verfügbar ist.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitpläne.

> [!NOTE]
> Diese Seite spiegelt die aktuellen Planungen von Microsoft für Intune-Funktionen in einem zukünftigen Release wider. Termine und einzelne Features können sich ändern. Auf dieser Seite werden nicht alle Features beschrieben, die gerade entwickelt werden.

**RSS-Feed**: Bleiben Sie auf dem Laufenden, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>App-Verwaltung

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Anzeigen von Benachrichtigungen für die Unternehmensportal-App unter Windows<!-- 1808082  -->
Microsoft aktualisiert die Unternehmensportal-App auf Windows-Geräten, sodass für Benutzer Popupbenachrichtigungen angezeigt werden, selbst wenn die Anwendung nicht geöffnet ist. Nach dem Update werden Benachrichtigungen für verfügbare Apps nur angezeigt, wenn der Installationsstatus „Abgeschlossen“ oder „Fehlgeschlagen“ lautet. In der Unternehmensportal-App werden keine Benachrichtigungen mehr für erforderliche Anwendungen angezeigt. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Anzeigen von Installationsstatusmeldungen für die Unternehmensportal-App<!-- 2514416  -->
In der Unternehmensportal-App werden zusätzliche Statusmeldungen zur App-Installation für Endbenutzer angezeigt. Die folgenden Bedingungen gelten für neue Win32-Abhängigkeitsfunktionen:
- Die App konnte nicht installiert werden. Vom Administrator definierte Abhängigkeiten wurden nicht erfüllt.

### <a name="retarget-web-clips-to-microsoft-edge-on-iosipados-devices---5455276---"></a>Festlegen von Microsoft Edge als Zielbrowser für Webclips auf iOS-/iPadOS-Geräten<!-- 5455276 -->
Webclips, die als angeheftete Web-Apps auf iOS-/iPadOS-Geräten fungieren, müssen aktualisiert werden. Neu bereitgestellte Webclips werden in Microsoft Edge geöffnet, anstatt in Intune Managed Browser, wenn sie in einem geschützten Browser geöffnet werden müssen. Bereits vorhandene Webclips müssen neu zugewiesen werden, damit sie in Microsoft Edge anstatt in Managed Browser geöffnet werden.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>Verbesserungen an den Funktionen des macOS-Unternehmensportals<!-- 5568987 -->
Es werden Verbesserungen bei der Geräteregistrierung für macOS sowie an der Unternehmensportal-App für Mac durchgeführt. Sie können Folgendes erwarten:
- Eine bessere **AutoUpdate**-Umgebung von Microsoft während der Registrierung, mit der sichergestellt wird, dass Ihre Benutzer über die neueste Version des Unternehmensportals verfügen
- Eine erweiterte Konformitätsüberprüfung während der Registrierung
- Unterstützung für kopierte Incident-IDs, sodass Ihre Benutzer Fehler über ihre Geräte schneller an das Supportteam Ihres Unternehmens schicken können

Weitere Informationen zur Registrierung und der Unternehmensportal-App für Mac finden Sie im Artikel zur Registrierung Ihres macOS-Geräts mit der Unternehmensportal-App (https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp) 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Bildschirm aus dem Unternehmensportal bzw. der Android-Arbeitsprofilregistrierung entfernt<!--6103987 -->
Der Bildschirm **Wie geht es weiter?** wird aus dem Registrierungsflow des Android-Arbeitsprofils im Unternehmensportal entfernt, um die Handhabung zu optimieren. Wechseln Sie zu [Registrieren mit dem Android-Arbeitsprofil]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile), um den aktuellen Registrierungsflow für das Android-Arbeitsprofil anzuzeigen.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>App für Microsoft Defender Advanced Threat Protection (ATP) für macOS<!-- 5424518 idready -->
Intune bietet eine einfache Möglichkeit, die Microsoft Defender Advanced Threat Protection-App (ATP) für macOS auf verwalteten Mac-Geräten bereitzustellen. Weitere Informationen finden Sie unter [Was ist Microsoft Defender Advanced Threat Protection für Mac?](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac). 

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Gerätekonfigurationsprofil für das kabelgebundene Netzwerk für macOS-Geräte<!-- 3508686  -->
Ein neues Gerätekonfigurationsprofil für macOS ist verfügbar, das kabelgebundene Netzwerke konfiguriert. Navigieren Sie dafür zu **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS**, um die Plattform auszuwählen, und wählen Sie dann den Profiltyp **Kabelgebundenes Netzwerk** aus. Verwenden Sie dieses Feature zum Erstellen von 802.1x-Profilen für die Verwaltung von kabelgebundenen Netzwerken, und stellen Sie dieses Netzwerke für Ihre macOS-Geräte bereit.

Gilt für:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-iosipados-devices----1947932-idready---"></a>VPN-Profile mit IKEv2-VPN-Verbindungen können Always On auf iOS-/iPadOS-Geräten verwenden <!-- 1947932 idready -->
Auf iOS-/iPadOS-Geräten können Sie ein VPN-Profil erstellen, das eine IKEv2-Verbindung verwendet. Navigieren Sie hierfür zu **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS**, um die Plattform auszuwählen, und wählen Sie anschließend den Profiltyp **VPN** aus. In einem zukünftigen Update können Sie Always On mit IKEv2 konfigurieren. Wenn die IKEv2-VPN-Profile konfiguriert sind, stellen sie automatisch eine Verbindung zum VPN her und bleiben verbunden bzw. stellen im Fall eines Verbindungsverlusts die Verbindung schnell wieder her. Die Verbindung bleibt bestehen, selbst wenn das Netzwerk gewechselt wird oder Geräte neu gestartet werden.

Unter iOS/iPadOS ist das Always On-VPN auf IKEv2-Profile beschränkt.

Die derzeit konfigurierbaren IKEv2-Einstellungen finden Sie unter [Hinzufügen von VPN-Einstellungen auf iOS-/iPadOS-Geräten in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gilt für:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-iosipados-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Verbesserte Benutzeroberfläche für das Erstellen von Konfigurationsprofilen auf iOS-/iPadOS- und macOS-Geräten<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Wenn Sie ein Profil für iOS-/iPadOS- oder macOS-Geräte erstellen, wird das Microsoft Endpoint Manager Admin Center entsprechend aktualisiert. Diese Änderung wirkt sich auf die folgenden Gerätekonfigurationsprofile aus. (Navigieren Sie zu **Geräte** > **Konfigurationsprofile** > **Profil erstellen** > **iOS** oder **macOS**, um die Plattform auszuwählen):

- Benutzerdefiniert: iOS/iPadOS, macOS
- Gerätefunktionen: iOS/iPadOS, macOS
- Geräteeinschränkungen: iOS/iPadOS, macOS
- Endpoint Protection: macOS
- Erweiterungen: macOS
- Einstellungsdatei: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Verbesserte Benutzeroberfläche für das Erstellen von OEMConfig-Konfigurationsprofilen auf Android Enterprise-Geräten<!-- 5568645 idready  -->
Wenn Sie ein OEMConfig-Profil für Android Enterprise-Geräte erstellen oder bearbeiten, wird das Microsoft Endpoint Manager Admin Center entsprechend aktualisiert. Nach der Aktualisierung wird eine übersichtliche Zusammenfassung der Einstellungen angezeigt, die Sie konfiguriert haben. Diese Änderungen wirken sich auf die OEMConfig-Gerätekonfigurationsprofile aus. Navigieren Sie zu **Geräte** > **Konfigurationsprofile** > **Profil erstellen** > **Android Enterprise**, um die Plattform auszuwählen, und wählen Sie dann den Profiltyp **OEMConfig** aus.

Diese Funktion gilt für:
- Android Enterprise 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Ändern des primären Benutzers für Windows-Geräte <!-- 3794742 -->
Sie können den primären Benutzer für hybride Windows- und Azure AD-Geräte ändern. Navigieren Sie hierzu zu **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Eigenschaften** > **Primärer Benutzer**. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Seriennummer auf der Seite des Apple-MDM-Push-Zertifikats<!--5947765 -->
Auf der Seite des Apple-MDM-Push-Zertifikats wird die Seriennummer angezeigt. Die Seriennummer ist erforderlich, um erneut auf das Apple-MDM-Push-Zertifikat zuzugreifen, wenn der Zugriff auf die Apple-ID, über die das Zertifikat erstellt wurde, verloren gegangen ist. Wenn Sie die Seriennummer anzeigen möchten, wechseln Sie zu **Geräte** > **iOS** > **iOS-Registrierung** > **Apple-MDM-Push-Zertifikat**.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>Auswählen, welche iOS/iPadOS-Updates an registrierte Geräte gepusht werden sollen<!--5879689 -->
Sie können ein bestimmtes iOS/iPadOS-Update auswählen, das mithilfe von Push auf Geräte übertragen werden soll, die entweder mit Apple Business Manager oder Apple School Manager registriert wurden. Für solche Geräte muss eine Gerätekonfigurationsrichtlinie festgelegt werden, um die Sichtbarkeit von Softwareupdates für einige Tage zu verzögern. Um dieses Feature anzuzeigen, wechseln Sie zu MEM > **Geräte** > **iOS** > **Richtlinien für iOS/iPadOS aktualisieren** > **Profil erstellen**.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>Neue Optionen für den Updatezeitplan zum Übertragen von Betriebssystemupdates per Push an iOS/iPadOS-Geräte<!--5879689-->
Bei der Planung von Betriebssystemupdates für iOS/iPadOS-Geräte können Sie aus folgenden Optionen wählen. Dies gilt für Geräte, die die Registrierungstypen Apple Business Manager oder Apple School Manager verwendet haben.
- Beim nächsten Einchecken aktualisieren
- Update innerhalb des geplanten Zeitraums
- Update außerhalb des geplanten Zeitraums

Für die beiden letztgenannten Optionen können Sie mehrere Zeitfenster erstellen.

Wenn Sie die neuen Optionen anzeigen möchten, wechseln Sie zu MEM > **Geräte** > **iOS** > **Richtlinien für iOS/iPadOS aktualisieren** > **Profil erstellen**.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Überwachung und Problembehandlung

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>Verbesserte Intune-Berichterstellung<!-- 3791418 idready -->
Intune bietet nun verbesserte Berichtserstellungsfunktionen, einschließlich neuer Berichtstypen, besserer Berichtsorganisation, fokussierterer Ansichten, verbesserter Berichtsfunktionen sowie konsistenterer und aktuellerer Daten. Die Berichterstellungsfunktion ist bald allgemein verfügbar und befindet sich dann nicht mehr in der öffentlichen Vorschau. Zusätzlich bietet dieses Release Lokalisierungsunterstützung, Fehlerbehebungen, Verbesserungen am Design sowie aggregierte Gerätekonformitätsdaten auf Kacheln im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

Neue Berichtstypen konzentrieren sich auf Folgendes:
- **Operational** (betriebsbedingt): stellt neue Berichte mit einem negativen Integritätsfokus bereit 
- **Organizational** (organisationsbedingt): stellt eine umfassendere Zusammenfassung des Gesamtzustands bereit
- **Historical** (verlaufsbedingt): stellt Muster und Trends über einen bestimmten Zeitraum bereit
- **Specialist** (spezialisiert): ermöglicht die Verwendung von Rohdaten zur Erstellung Ihrer eigenen benutzerdefinierten Berichte

Die ersten neuen Berichte konzentrieren sich auf die Gerätekonformität. Weitere Informationen finden Sie im Blogbeitrag [Neues Berichtserstellungsframework für Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) und unter [Intune-Berichte](~/fundamentals/reports.md).



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Benutzeroberfläche für Intune-Rollen wird bald geändert<!--5801612 idready-->
Die Benutzeroberfläche für [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Mandantenverwaltung** > **Rollen** wird aktualisiert und ist dann benutzerfreundlicher und intuitiver. Nach der Aktualisierung haben Sie Zugriff auf dieselben Einstellungen und Details wie bisher. Der neue Prozess ähnelt dann aber eher einem Assistenten.


<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Unterstützung für abgeleitete Anmeldeinformationen auf Android-COBO-Geräten<!--4839592-->
Sie können abgeleitete Anmeldeinformationen auf vollständig verwalteten Android Enterprise-Geräten verwenden. Das Abrufen von abgeleiteten Anmeldeinformationen für Entrust Datacard, Intercede und DISA Purebred wird unterstützt. Sie können abgeleitete Anmeldeinformationen für die App-Authentifizierung, für WLAN, VPNs oder S/MIME-Signaturen und/oder -Verschlüsselung für Apps verwenden, die dies unterstützen.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>Verwenden der Antivirusrichtlinie zum Verwalten von Einstellungen für Microsoft Defender Antivirus und der Windows-Sicherheitsumgebung<!--6131401 -->
Über den Knoten *Endpunktsicherheit* können Sie Einstellungen für **Antivirus** konfigurieren. Wenn Sie die Richtlinie für Antivirus konfigurieren, definieren Sie die Einstellungen für Ihre Windows 10-Geräte über zwei Profiltypen:

- Microsoft Defender Antivirus: Verwalten Sie Einstellungen für den Cloudschutz, Antivirenausschlüsse, die Wiederherstellung, Überprüfungsoptionen und vieles mehr.
- Windows-Sicherheitsumgebung: Verwalten Sie, wie Benutzer mit Windows-Sicherheitseinstellungen auf ihren Geräten arbeiten können. Sie können konfigurieren, was Endbenutzer im Microsoft Defender Security Center anzeigen können und welche Benachrichtigungen sie erhalten. 

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Weitere Informationen:
Details zu aktuellen Entwicklungen finden Sie unter [Neuerungen in Microsoft Intune](whats-new.md).


