---
title: 'In der Entwicklung: Microsoft Intune'
titleSuffix: ''
description: In der Entwicklung befindliche Microsoft Intune-Features
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912629"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>In der Entwicklung befindliche Microsoft Intune-Features: Januar 2020

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

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Festlegen von Microsoft Edge als Zielbrowser für Webclips auf iOS-Geräten<!-- 5455276 -->
Webclips, die als angeheftete Web-Apps auf iOS-Geräten fungieren, müssen aktualisiert werden. Neu bereitgestellte Webclips werden in Microsoft Edge geöffnet, anstatt in Intune Managed Browser, wenn sie in einem geschützten Browser geöffnet werden müssen. Bereits vorhandene Webclips müssen neu zugewiesen werden, damit sie in Microsoft Edge anstatt in Managed Browser geöffnet werden. 


<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Gerätekonfigurationsprofil für das kabelgebundene Netzwerk für macOS-Geräte<!-- 3508686  -->
Ein neues Gerätekonfigurationsprofil für macOS ist verfügbar, das kabelgebundene Netzwerke konfiguriert. Navigieren Sie dafür zu **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS**, um die Plattform auszuwählen, und wählen Sie dann den Profiltyp **Kabelgebundenes Netzwerk** aus. Verwenden Sie dieses Feature zum Erstellen von 802.1x-Profilen für die Verwaltung von kabelgebundenen Netzwerken, und stellen Sie dieses Netzwerke für Ihre macOS-Geräte bereit.

Gilt für:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>VPN-Profile mit IKEv2-VPN-Verbindungen können Always On auf iOS-Geräten verwenden <!-- 1947932 idready -->
Auf iOS-Geräten können Sie ein VPN-Profil erstellen, das eine IKEv2-Verbindung verwendet. Navigieren Sie dafür zu **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS**, um die Plattform auszuwählen, und wählen Sie dann den Profiltyp **VPN** aus. In einem zukünftigen Update können Sie Always On mit IKEv2 konfigurieren. Wenn die IKEv2-VPN-Profile konfiguriert sind, stellen sie automatisch eine Verbindung zum VPN her und bleiben verbunden bzw. stellen im Fall eines Verbindungsverlusts die Verbindung schnell wieder her. Die Verbindung bleibt bestehen, selbst wenn das Netzwerk gewechselt wird oder Geräte neu gestartet werden.

Unter iOS ist das Always On-VPN auf IKEv2-Profile beschränkt.

Die derzeit konfigurierbaren IKEv2-Einstellungen finden Sie unter [Hinzufügen von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gilt für:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Verbesserte Benutzeroberfläche für das Erstellen von Konfigurationsprofilen auf iOS- und macOS-Geräten<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Wenn Sie ein Profil für iOS- oder macOS-Geräte erstellen, wird das Microsoft Endpoint Manager Admin Center entsprechend aktualisiert. Diese Änderung wirkt sich auf die folgenden Gerätekonfigurationsprofile aus. (Navigieren Sie zu **Geräte** > **Konfigurationsprofile** > **Profil erstellen** > **iOS** oder **macOS**, um die Plattform auszuwählen):

- Benutzerdefiniert: iOS, macOS
- Gerätefeatures: iOS, macOS
- Geräteeinschränkungen: iOS, macOS
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
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Benutzeroberfläche für Intune-Rollen wird bald geändert<!--5801612 idready-->
Die Benutzeroberfläche für [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Mandantenverwaltung** > **Rollen** wird aktualisiert und ist dann benutzerfreundlicher und intuitiver. Nach der Aktualisierung haben Sie Zugriff auf dieselben Einstellungen und Details wie bisher. Der neue Prozess ähnelt dann aber eher einem Assistenten.


<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Unterstützung für abgeleitete Anmeldeinformationen auf Android-COBO-Geräten<!--4839592-->
Sie können abgeleitete Anmeldeinformationen auf vollständig verwalteten Android Enterprise-Geräten verwenden. Das Abrufen von abgeleiteten Anmeldeinformationen für Entrust Datacard, Intercede und DISA Purebred wird unterstützt. Sie können abgeleitete Anmeldeinformationen für die App-Authentifizierung, für WLAN, VPNs oder S/MIME-Signaturen und/oder -Verschlüsselung für Apps verwenden, die dies unterstützen. 

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Weitere Informationen:
Details zu aktuellen Entwicklungen finden Sie unter [Neuerungen in Microsoft Intune](whats-new.md).


