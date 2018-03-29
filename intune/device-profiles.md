---
title: Geräteprofile in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Übersicht über die verschiedenen Microsoft Intune-Geräteprofile mit Angaben zu Features, Einschränkungen, E-Mail-Adressen, WLAN, VPN, Education, Zertifikaten, zum Upgrade von Windows 10, BitLocker und Windows Defender, Windows Information Protection sowie zu benutzerdefinierten Einstellungen für die Gerätekonfiguration im Azure-Portal. Verwenden Sie diese Profile zum Verwalten und Schützen von Daten und Geräten in Ihrem Unternehmen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e92a10f51fb403c802c1c6d3ea79ccf49a1e93fb
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Was sind Microsoft Intune Geräteprofile?

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune umfasst Einstellungen und Features, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Features werden mithilfe von Profilen verwaltet. Beispiele für Profile: 

- Ein WLAN-Profil, das verschiedenen Geräten den Zugriff auf Ihr Unternehmensnetzwerks ermöglicht
- Ein VPN-Profil, das verschiedenen Geräten den Zugriff auf Ihren VPN-Server in Ihrem Unternehmensnetzwerks ermöglicht

Dieses Thema enthält eine Übersicht über die verschiedenen Profile, die Sie für Ihre Geräte erstellen können. Verwenden Sie diese Profile, um Features auf den Geräten zuzulassen oder zu verhindern.

## <a name="before-you-begin"></a>Vorbereitung
Um die verfügbaren Features anzuzeigen, öffnen Sie zunächst das [Azure-Portal](https://portal.azure.com) und anschließend Ihre Intune-Ressource. 

**Gerätekonfiguration** umfasst folgende Optionen:

- **Übersicht**: Hier werden die Status Ihrer Profile sowie weitere Details zu den Profilen angezeigt, die Sie Benutzern und Geräten zugewiesen haben.
- **Verwalten**: Mit dieser Option erstellen Sie Geräteprofile und laden benutzerdefinierte [PowerShell-Skripts](intune-management-extension.md) zur Ausführung im Profil hoch.
- **Überwachen**: Mit dieser Option prüfen Sie den Status eines Profils und zeigen Protokolle zu Ihren Profilen an.
- **Setup**: Mit dieser Option fügen Sie eine Zertifizierungsstelle (SCEP oder PFX) hinzu oder aktivieren Telecom Expense Management für das Profil.

## <a name="create-the-profile"></a>Erstellen des Profils

Unter [Erstellen von Gerätekonfigurationsprofilen](device-profile-create.md) finden Sie eine ausführliche Anleitung zum Erstellen eines Profils. 

## <a name="device-features-profile"></a>Profil für Gerätefeatures

Mit [Gerätefeatures](device-features-configure.md) können Sie Features auf iOS- und macOS-Geräten wie AirPrint, Benachrichtigungen und freigegebene Gerätekonfigurationen steuern.

Dieses Features unterstützt folgende Betriebssysteme:  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>Profil für Geräteeinschränkungen
Mit [Geräteeinschränkungen](device-restrictions-configure.md) werden Einstellungen für Sicherheit, Hardware, Datenfreigabe und viele andere Einstellungen auf dem Gerät gesteuert. Sie können beispielsweise ein Geräteeinschränkungsprofil erstellen, das verhindert, dass Benutzer von iOS-Geräten auf die Kamera des Geräts zugreifen. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="email-profile"></a>E-Mail-Profil
Mit dem Profil für [E-Mail-Einstellungen](email-settings-configure.md) können Sie Exchange ActiveSync-E-Mail-Einstellungen auf den Geräten erstellen, zuweisen und überwachen. E-Mail-Profile helfen beim Sicherstellen der Einheitlichkeit, beim Reduzieren der Anzahl von Supportanfragen und ermöglichen Endbenutzern den Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten, ohne dass ihrerseits eine Konfiguration erforderlich wäre. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="wi-fi-profile"></a>Wi-Fi-Profil
Mit [WLAN-Einstellungen](wi-fi-settings-configure.md) können Sie Benutzern und Geräten WLAN-Einstellungen zuweisen. Wenn Sie ein WLAN-Profil zuweisen, erhalten Benutzer Zugriff auf Ihr Unternehmens-WLAN, ohne es selbst konfigurieren zu müssen. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows 8.1 (nur Import)

## <a name="vpn-profile"></a>VPN-Profil
Mit [VPN-Einstellungen](vpn-settings-configure.md) können Sie Benutzern und Geräten in Ihrer Organisation VPN-Profile zuweisen, damit diese einfach eine sichere Verbindung mit dem Netzwerk herstellen können. 

Virtuelle private Netzwerke (Virtual Private Networks, VPNs) ermöglichen Benutzern einen sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. Geräte verwenden ein VPN-Verbindungsprofil, um eine Verbindung mit dem VPN-Server zu initiieren. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>Education-Profil
Mit den [Education-Einstellungen](education-settings-configure.md) können Sie Optionen für die [Windows Take a Test-App](https://education.microsoft.com/gettrained/win10takeatest) konfigurieren. Wenn Sie diese Optionen konfigurieren, können keine anderen Apps auf dem Gerät ausgeführt werden, bis der Test abgeschlossen ist.

## <a name="certificates-profile"></a>Profil für Zertifikate
Mit [Zertifikate](certificates-configure.md) können Sie vertrauenswürdige SCEP- und PKCS-Zertifikate konfigurieren, die Geräten zugewiesen und zum Authentifizieren von WLAN-, VPN- und E-Mail-Profilen verwendet werden können.

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>Editionsupgradeprofil
Mit [Windows 10-Editionsupgrades](edition-upgrade-configure-windows-10.md) können Sie Geräte, auf denen einige Windows 10-Versionen ausgeführt werden, automatisch auf eine neuere Edition upgraden.

Dieses Features unterstützt nur Windows 10

## <a name="endpoint-protection-profile"></a>Endpoint Protection-Profil
Mit [Endpoint Protection-Einstellungen für Windows 10](endpoint-protection-windows-10.md) können Sie BitLocker- und Windows Defender-Einstellungen für Windows 10-Geräte konfigurieren.

Informationen zum Integrieren von WDATP (Windows Defender Advanced Threat Protection) mit Microsoft Intune finden Sie unter [Configure endpoints using Mobile Device Management (MDM) tools (Konfigurieren von Endpunkten mithilfe der mobilen Geräteverwaltung (MDM))](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection).

Dieses Features unterstützt nur Windows 10

## <a name="windows-information-protection-profile"></a>WIP-Profil (Windows Information Protection)
[Windows Information Protection](windows-information-protection-configure.md) unterstützt Sie dabei, das Unternehmen vor Datenlecks zu schützen, ohne gleichzeitig die Benutzerfreundlichkeit für die Mitarbeiter einzuschränken. Die Lösung schützt auch Unternehmens-Apps und -daten vor versehentlichen Datenlecks auf unternehmenseigenen sowie auf persönlichen Geräten, die die Mitarbeiter bei der Arbeit verwenden. Dabei ist es nicht erforderlich, dass Sie Ihre Umgebung oder andere Apps ändern.

Dieses Features unterstützt nur Windows 10

## <a name="custom-profile"></a>Benutzerdefiniertes Profil
[Benutzerdefinierte Einstellungen](custom-settings-configure.md) bieten die Möglichkeit, Geräteeinstellungen zuzuweisen, die nicht in Intune integriert sind. So können beispielsweise auf Android-Geräten OMA-URI-Werte eingegeben werden. Auf iOS-Geräten können Sie eine Konfigurationsdatei importieren, die Sie in Apple Configurator erstellt haben. 

Dieses Features unterstützt folgende Betriebssysteme:

- Android
- iOS
- macOS
- Windows Phone 8.1