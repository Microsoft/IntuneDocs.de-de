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
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827818"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>In der Entwicklung befindliche Microsoft Intune-Features: Januar 2020

Um Ihnen bei Ihrer Vorbereitung und Planung zu helfen, sind auf dieser Seite Updates und Features der Intune-Benutzeroberfläche aufgeführt, die sich in der Entwicklung befinden, aber noch nicht freigegeben wurden. Zusätzlich zu den Informationen auf dieser Seite: 

- Wenn wir davon ausgehen, dass Sie vor einer Änderung Maßnahmen ergreifen müssen, werden wir einen ergänzenden Beitrag im Office-Nachrichtencenter veröffentlichen.
- Wenn eine Funktion in die Produktionsumgebung wechselt, egal ob es sich um eine Vorschauversion handelt oder allgemein verfügbar ist, wird die Funktionsbeschreibung von dieser Seite zu den [Neuerungen](whats-new.md)verschoben.
- Diese Seite und die Seite [Neuerungen](whats-new.md) werden regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.
- In der [Roadmap für Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) finden Sie strategische Ziele und Zeitpläne.

> [!NOTE]
> Diese Seite spiegelt unsere aktuellen Erwartungen an die Intune-Funktionen in einer zukünftigen Version wider. Termine und einzelne Features können sich ändern. Auf dieser Seite werden nicht alle Features in der Entwicklung beschrieben.

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Anzeigen von Benachrichtigungen für die Unternehmensportal-app unter Windows<!-- 1808082  -->
Wir werden die Unternehmensportal-App auf Windows-Geräten aktualisieren, um Benutzern Popup Benachrichtigungen anzuzeigen, auch wenn die Anwendung geschlossen wird. Das Update zeigt nur dann Benachrichtigungen für verfügbare apps an, wenn der Installationsstatus "abgeschlossen" oder "Fehler" lautet. Die Unternehmensportal-APP zeigt keine Benachrichtigungen für erforderliche Anwendungen an. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Anzeigen der Installationsstatus Meldungen für die Unternehmensportal-App<!-- 2514416  -->
Die Unternehmensportal-APP zeigt den Endbenutzern zusätzliche APP-Installationsstatus Meldungen an. Die folgenden Bedingungen gelten für neue Win32-Abhängigkeits Features:
- Die App konnte nicht installiert werden. Vom Administrator definierte Abhängigkeiten wurden nicht erfüllt.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>Neuzuweisen von Webclips zu Microsoft Edge auf IOS-Geräten<!-- 5455276 idready -->
Webclips, die als fixierte Web-Apps auf IOS-Geräten fungieren, müssen aktualisiert werden. Neu bereitgestellte Webclips werden in Microsoft Edge geöffnet, anstatt in der InTune Managed Browser, wenn Sie in einem geschützten Browser geöffnet werden müssen. Sie müssen bereits vorhandene Webclips neu zuweisen, um sicherzustellen, dass Sie anstelle des Managed Browser in Microsoft Edge geöffnet werden. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Benutzeroberflächen Änderung beim Hinzufügen von apps zu InTune<!-- 4705829 idready -->
Beim Hinzufügen von apps über InTune wird eine neue Benutzerfunktion angezeigt. Diese Umgebung bietet dieselben Einstellungen und Details, die Sie zuvor verwendet haben, aber die neue Umgebung folgt einem Assistenten ähnlichen Prozess, bevor Sie eine APP zu InTune hinzufügen. Diese neue Darstellung bietet auch eine Überprüfungs Seite, bevor Sie die APP hinzufügen. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Apps** > **Alle Apps** > **Hinzufügen** aus. Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----3136567--"></a>Neustarten von Win32-apps erforderlich <!-- 3136567-->
Sie können verlangen, dass eine Win32-App nach einer erfolgreichen Installation neu gestartet werden muss. Außerdem können Sie die Zeitspanne (die Toleranz Periode) auswählen, bevor der Neustart erfolgen muss.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Gerätekonfiguration

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Hinzufügen automatischer Proxy Einstellungen zu WLAN-Profilen für Android Enterprise-Arbeitsprofile<!-- 4490822 idready -->
Auf Geräten mit Android-Unternehmens Arbeits Profilen können Sie WLAN-Profile erstellen. Wenn Sie den Typ "Wi-Fi Enterprise" auswählen, können Sie auch den EAP-Typ (Extensible Authentication Protocol), der in Ihrem WLAN-Netzwerk verwendet wird, eingeben.

Wenn Sie in einem zukünftigen Update den Enterprise-Typ auswählen, können Sie die automatischen Proxy Einstellungen, einschließlich einer Proxy Server-URL, wie z. b. `proxy.contoso.com`, eingeben.

Die aktuellen WLAN-Einstellungen, die Sie konfigurieren können, finden Sie unter [Hinzufügen von WLAN-Einstellungen für Geräte mit Android Enterprise und Android Kiosk in Microsoft InTune](../configuration/wi-fi-settings-android-enterprise.md).

Gilt für:
- Android Enterprise-Arbeitsprofil

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Netzwerkgeräte-Konfigurations Profile für macOS-Geräte<!-- 3508686  -->
Ein neues MacOS-Geräte Konfigurations Profil ist verfügbar, das verkabelte Netzwerke (**Geräte Konfigurations** > **profile** > **Profil** > **macOS** für Plattform > **Kabelnetzwerk** für Profiltyp erstellen) konfiguriert. Verwenden Sie dieses Feature zum Erstellen von 802.1 x-Profilen zum Verwalten von verkabelten Netzwerken und zum Bereitstellen dieser Kabel Netzwerke auf Ihren macOS-Geräten.

Gilt für:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>VPN-Profile mit IKEv2-VPN-Verbindungen können "Always on" mit IOS-Geräten verwenden <!-- 1947932 idready -->
Auf IOS-Geräten können Sie ein VPN-Profil erstellen, das eine IKEv2-Verbindung verwendet (**Geräte Konfigurations** > **profile** > **Profil** > **IOS/ipados** für Platt Form > **VPN** für den Profiltyp erstellen). In einem zukünftigen Update können Sie Always on mit IKEv2 konfigurieren. Wenn die IKEv2-VPN-Profile konfiguriert sind, werden Sie automatisch mit dem VPN verbunden und bleiben verbunden. Die Verbindung bleibt auch dann bestehen, wenn Sie sich zwischen Netzwerken bewegen oder Geräte neu starten.

Unter IOS ist das Always on-VPN auf IKEv2-profile beschränkt.

Die derzeit konfigurierbaren IKEv2-Einstellungen finden Sie unter [Hinzufügen von VPN-Einstellungen auf iOS-Geräten in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Gilt für:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Verbesserte Benutzeroberfläche beim Erstellen von Konfigurations Profilen auf IOS-und macOS-Geräten<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Wenn Sie ein Profil für IOS-oder macOS-Geräte erstellen, wird die im Endpunkt Management Admin Center aktualisierte Funktion aktualisiert. Diese Änderung wirkt sich auf die folgenden Geräte Konfigurations Profile aus (**Geräte** > **Konfigurations profile** > **Profilerstellung** > **IOS** oder **macOS** für die Plattform):

- Benutzer definiert: IOS, macOS
- Gerätefunktionen: IOS, macOS
- Geräte Einschränkungen: IOS, macOS
- Endpoint Protection: macOS
- Erweiterungen: macOS
- Einstellungsdatei: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Verbesserte Benutzeroberfläche bei der Erstellung von oemconfig-Konfigurations Profilen auf Android-Unternehmens Geräten<!-- 5568645 idready  -->
Wenn Sie ein oemconfig-Profil für Android-Unternehmens Geräte erstellen oder bearbeiten, wird die im Endpoint Management-Admin Center erstellte Funktion aktualisiert. Die aktualisierte Erfahrung bietet eine Zusammenfassung der Einstellungen, die Sie auf einen Blick konfiguriert haben. Diese Änderung wirkt sich auf das oemconfig-Geräte Konfigurations Profil aus (**Geräte** > **Konfigurations profile** > **Profil erstellen** > **Android Enterprise** for Platform > **oemconfig** für den Profiltyp).

Diese Funktion gilt für:
- Android Enterprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Geräteregistrierung

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>Android-Registrierungen durch Gerätehersteller blockieren<!--5197392 idready-->
Sie können die Anmeldung von Geräten basierend auf dem Gerätehersteller blockieren. Dies gilt für Android-Geräte Administratoren und Android-Unternehmens Arbeitsprofil-Geräte. Informationen zu den Registrierungs Beschränkungen finden Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)> **Geräte** > Registrierungs **Einschränkungen**.



<!-- ***********************************************-->
## <a name="device-management"></a>Geräteverwaltung


### <a name="new-information-in-device-details---4471759-5604099----"></a>Neue Informationen in den Geräte Details<!-- 4471759 5604099  -->
Die folgenden Informationen werden auf der **Übersichts** Seite für Geräte hinzugefügt:
- Arbeitsspeicher Kapazität (Menge an physischem Arbeitsspeicher auf dem Gerät)
- Speicherkapazität (Menge an physischem Speicher auf dem Gerät) 
- CPU-Prozessortyp und -geschwindigkeit
- RAM-und Prozessor Daten

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>Neuer InTune-Endpunkt Sicherheits-Manager für integrierte Rollen<!--4253397 idready-->
Eine neue integrierte InTune-Rolle ist verfügbar: Endpoint Security-Manager. Diese neue Rolle gewährt Administratoren Vollzugriff auf den Endpunkt-Manager-Knoten in InTune und den reinen Zugriff auf andere Bereiche. Die Rolle ist eine Erweiterung der Rolle "Sicherheits Administrator" von Azure AD. Wenn Sie zurzeit nur globale Administratoren als Rollen haben, sind keine Änderungen erforderlich. Wenn Sie Rollen verwenden und die Granularität, die der Endpoint Security-Manager bereitstellt, verwenden möchten, weisen Sie diese Rolle zu, sobald Sie verfügbar ist. Weitere Informationen zu integrierten Rollen finden Sie unter [rollenbasierte Zugriffs Steuerung](role-based-access-control.md).

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Änderungen an der Benutzeroberfläche der InTune-Rollen<!--5801612 idready-->
Die Benutzeroberfläche für das [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > Mandanten **Verwaltung** > **Rollen** ändert sich in einen benutzerfreundlicheren und intuitiveren Entwurf. Diese Umgebung bietet die gleichen Einstellungen und Details, die Sie jetzt verwenden, aber die neue Umgebung verwendet einen Assistenten ähnlichen Prozess.


<!-- ***********************************************-->
## <a name="security"></a>Sicherheit

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Unterstützung abgeleiteter Anmelde Informationen für Android-Cobo<!--4839592-->
Sie können abgeleitete Anmelde Informationen auf vollständig verwalteten Android-Geräten verwenden. Es wird Unterstützung für das Abrufen abgeleiteter Anmelde Informationen für Entrust Datacard, Intercede und DISA-purebrot eingeschlossen. Sie können abgeleitete Anmelde Informationen für die APP-Authentifizierung, Wi-Fi, VPN oder S/MIME-Signierung und/oder Verschlüsselung mit Apps verwenden, die diese unterstützen. 

<!-- ***********************************************-->
## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Weitere Informationen:
Details zu aktuellen Entwicklungen finden Sie unter [Neuerungen in Microsoft Intune](whats-new.md).


