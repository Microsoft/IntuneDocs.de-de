---
title: Geräteprofile in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Hier finden Sie eine Übersicht über die verschiedenen Microsoft Intune-Geräteprofile mit Angaben zu Features, Einschränkungen, E-Mail-Adressen, WLAN, VPN, Education, Zertifikaten, zum Upgrade von Windows 10, BitLocker und Windows Defender, Windows Information Protection sowie zu benutzerdefinierten Einstellungen für die Gerätekonfiguration im Azure-Portal. Verwenden Sie diese Profile zum Verwalten und Schützen von Daten und Geräten in Ihrem Unternehmen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 590ce850b97502b357dec86932e1445718860af2
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253543"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Was sind Microsoft Intune Geräteprofile?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune umfasst Einstellungen und Features, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Features werden mithilfe von Profilen verwaltet. Beispiele für Profile: 

- Ein WLAN-Profil, das verschiedenen Geräten den Zugriff auf Ihr Unternehmensnetzwerks ermöglicht
- Ein VPN-Profil, das verschiedenen Geräten den Zugriff auf Ihren VPN-Server in Ihrem Unternehmensnetzwerks ermöglicht

Dieser Artikel enthält eine Übersicht über die verschiedenen Profile, die Sie für Ihre Geräte erstellen können. Verwenden Sie diese Profile, um Features auf den Geräten zuzulassen oder zu verhindern.

## <a name="before-you-begin"></a>Vorbereitung
Um die verfügbaren Features anzuzeigen, öffnen Sie zunächst das [Azure-Portal](https://portal.azure.com) und anschließend Ihre Intune-Ressource. 

**Gerätekonfiguration** umfasst folgende Optionen:

- **Übersicht**: Hier werden die Status Ihrer Profile sowie weitere Details zu den Profilen angezeigt, die Sie Benutzern und Geräten zugewiesen haben.
- **Verwalten**: Mit dieser Option erstellen Sie Geräteprofile und laden benutzerdefinierte [PowerShell-Skripts](intune-management-extension.md) zur Ausführung im Profil hoch.
- **Überwachen**: Mit dieser Option prüfen Sie den Status eines Profils und zeigen Protokolle zu Ihren Profilen an.
- **Setup**: Mit dieser Option fügen Sie eine Zertifizierungsstelle (SCEP oder PFX) hinzu oder aktivieren Telecom Expense Management für das Profil.

## <a name="create-the-profile"></a>Erstellen des Profils

Unter [Erstellen von Gerätekonfigurationsprofilen](device-profile-create.md) finden Sie eine ausführliche Anleitung zum Erstellen eines Profils. 

## <a name="device-features---ios-and-macos"></a>Gerätefeatures auf iOS und macOS

Mit [Gerätefeatures](device-features-configure.md) können Sie Features auf iOS- und macOS-Geräten wie AirPrint, Benachrichtigungen und freigegebene Gerätekonfigurationen steuern.

Dieses Features unterstützt folgende Betriebssysteme:
- iOS 
- macOS


## <a name="device-restrictions"></a>Geräteeinschränkungen
Mit [Geräteeinschränkungen](device-restrictions-configure.md) werden Einstellungen für Sicherheit, Hardware, Datenfreigabe und viele andere Einstellungen auf dem Gerät gesteuert. Sie können beispielsweise ein Geräteeinschränkungsprofil erstellen, das verhindert, dass Benutzer von iOS-Geräten auf die Kamera des Geräts zugreifen. 

Dieses Features unterstützt folgende Betriebssysteme:

- Android
- iOS
- macOS
- Windows 10
- Windows 10 Team

## <a name="endpoint-protection"></a>Endpoint Protection
Mit [Endpoint Protection-Einstellungen für Windows 10](endpoint-protection-windows-10.md) können Sie BitLocker- und Windows Defender-Einstellungen für Windows 10-Geräte konfigurieren.

Informationen zum Integrieren von WDATP (Windows Defender Advanced Threat Protection) mit Microsoft Intune finden Sie unter [Configure endpoints using Mobile Device Management (MDM) tools (Konfigurieren von Endpunkten mithilfe der mobilen Geräteverwaltung (MDM))](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection).

Dieses Features unterstützt folgende Betriebssysteme:
- Windows 10 und höher

## <a name="identity-protection"></a>Schutz der Identität
[Identity Protection](identity-protection-configure.md) steuert die Windows Hello for Business-Funktionen auf Windows 10- und Windows 10 Mobile-Geräten. Konfigurieren Sie diese Einstellungen, um Windows Hello for Business für Benutzer und Geräte zur Verfügung zu stellen und die Anforderungen für Geräte-PINs und Gesten festzulegen.  

Dieses Features unterstützt folgende Betriebssysteme:  
- Windows 10 und höher
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

Im Profil für [Kioskeinstellungen](kiosk-settings.md) kann ein Gerät so konfiguriert werden, dass auf diesem eine oder mehrere Apps ausgeführt werden. In Ihrem Kiosk können Sie auch andere Features wie ein Startmenü und einen Webbrowser anpassen.

Dieses Features unterstützt folgende Betriebssysteme:
- Windows 10 und höher

## <a name="email"></a>E-Mail
Mit dem Profil für [E-Mail-Einstellungen](email-settings-configure.md) können Sie Exchange ActiveSync-E-Mail-Einstellungen auf den Geräten erstellen, zuweisen und überwachen. E-Mail-Profile helfen beim Sicherstellen der Einheitlichkeit, beim Reduzieren der Anzahl von Supportanfragen und ermöglichen Endbenutzern den Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten, ohne dass ihrerseits eine Konfiguration erforderlich wäre. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN
Mit [VPN-Einstellungen](vpn-settings-configure.md) können Sie Benutzern und Geräten in Ihrer Organisation VPN-Profile zuweisen, damit diese einfach eine sichere Verbindung mit dem Netzwerk herstellen können. 

Virtuelle private Netzwerke (Virtual Private Networks, VPNs) ermöglichen Benutzern einen sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. Mit einem VPN-Verbindungsprofil stellen Geräte eine Verbindung mit dem VPN-Server her. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>WLAN
Mit [WLAN-Einstellungen](wi-fi-settings-configure.md) können Sie Benutzern und Geräten WLAN-Einstellungen zuweisen. Wenn Sie ein WLAN-Profil zuweisen, erhalten Benutzer Zugriff auf Ihr Unternehmens-WLAN, ohne es selbst konfigurieren zu müssen. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows 8.1 (nur Import)

## <a name="esim-cellular---public-preview"></a>eSIM-Mobiltelefone: Public Preview

Mithilfe von [eSIM-Mobilfunkprofilen](esim-device-configuration.md) können Sie Tarife für Mobilfunkdaten auf Ihre verwalteten Geräten für den Zugriff auf das Internet und auf Daten konfigurieren.  Sobald Sie Aktivierungscodes von Ihrem Mobilfunkanbieter erhalten haben, können Sie Intune zum Importieren dieser Codes verwenden und Ihren auf eSIM ausgelegten Geräten zuweisen.

Dieses Features unterstützt folgende Betriebssysteme:
- Windows 10 Fall Creators Update und höher

## <a name="education"></a>Education
Mit den [Education settings - Windows 10](education-settings-configure.md) (Education-Einstellungen: Windows 10) können Sie Optionen für die [Take a Test-Windows-App](https://education.microsoft.com/gettrained/win10takeatest) konfigurieren. Wenn Sie diese Optionen konfigurieren, können keine anderen Apps auf dem Gerät ausgeführt werden, bis der Test abgeschlossen ist.

In den [Education settings - iOS](education-settings-configure-ios-shared.md) (Education-Einstellungen: iOS) wird die iOS-Classroom-App so konfiguriert, dass der Unterricht strukturiert und Schüler-/Kursteilnehmer-Geräte im Kursraum gesteuert werden können. Sie können iPad-Geräte so konfigurieren, dass mehrere Schüler/Kursteilnehmer gemeinsam ein Gerät verwenden können.

## <a name="edition-upgrade"></a>Upgrade der Edition
Mit [Windows 10-Editionsupgrades](edition-upgrade-configure-windows-10.md) können Sie Geräte, auf denen einige Windows 10-Versionen ausgeführt werden, automatisch auf eine neuere Edition upgraden.

Dieses Features unterstützt folgende Betriebssysteme: 
- Windows 10 und höher

## <a name="update-policies"></a>Updaterichtlinien
Im Artikel [iOS-Updaterichtlinien](software-updates-ios.md) erfahren Sie, wie Sie iOS-Richtlinien erstellen und zuweisen, um Softwareupdates auf Ihren iOS-Geräten zu installieren. Außerdem können Sie den Installationsstatus überprüfen.

Dieses Features unterstützt folgende Betriebssysteme:
- iOS

## <a name="certificates"></a>Zertifikate
Mit [Zertifikate](certificates-configure.md) können Sie vertrauenswürdige SCEP- und PKCS-Zertifikate konfigurieren, die Geräten zugewiesen und zum Authentifizieren von WLAN-, VPN- und E-Mail-Profilen verwendet werden können.

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>WIP-Profil (Windows Information Protection)
[Windows Information Protection](windows-information-protection-configure.md) unterstützt Sie dabei, das Unternehmen vor Datenlecks zu schützen, ohne gleichzeitig die Benutzerfreundlichkeit für die Mitarbeiter einzuschränken. Die Lösung schützt auch Unternehmens-Apps und -daten vor versehentlichen Datenlecks auf unternehmenseigenen sowie auf persönlichen Geräten, die die Mitarbeiter bei der Arbeit verwenden. Dabei ist es nicht erforderlich, dass Sie Ihre Umgebung oder andere Apps ändern.

Dieses Features unterstützt folgende Betriebssysteme:
- Windows 10 und höher

## <a name="custom-profile"></a>Benutzerdefiniertes Profil
[Benutzerdefinierte Einstellungen](custom-settings-configure.md) bieten die Möglichkeit, Geräteeinstellungen zuzuweisen, die nicht in Intune integriert sind. So können beispielsweise auf Android-Geräten OMA-URI-Werte eingegeben werden. Auf iOS-Geräten können Sie eine Konfigurationsdatei importieren, die Sie in Apple Configurator erstellt haben. 

Dieses Features unterstützt folgende Betriebssysteme:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Verwaltung und Problembehandlung

[Verwalten Sie Ihre Profile](device-profile-monitor.md), um den Status von Geräten und die zugewiesenen Profile zu überprüfen. Lösen Sie Konflikte leichter, indem Sie sich die Einstellungen ansehen, die Konflikte verursachen, und die Profile, die diese Einstellungen enthalten. Im Artikel zu [Häufigen Problemen und Lösungen](device-profile-troubleshoot.md) finden Sie eine Liste mit Fragen und Antworten, um Sie bei der Arbeit mit Profilen zu unterstützen. Dort erfahren Sie u.a., was beim Löschen eines Profils passiert und wodurch Benachrichtigungen an Geräte gesendet werden.