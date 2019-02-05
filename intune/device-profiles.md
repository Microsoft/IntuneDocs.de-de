---
title: 'Gerätefunktionen und -einstellungen in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: In dieser Übersicht über die verschiedenen Microsoft Intune-Geräteprofile finden Sie Angaben zu Funktionen, Einschränkungen, E-Mail-Adressen, WLAN, VPN, Bildungswesen, Zertifikaten, zum Upgrade von Windows 10, BitLocker und Windows Defender, Windows Information Protection sowie zu administrativen Vorlagen und benutzerdefinierten Einstellungen für die Gerätekonfiguration im Azure-Portal. Verwenden Sie diese Profile zum Verwalten und Schützen von Daten und Geräten in Ihrem Unternehmen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: cf2bfbc992d4577e345b73f07ec465990feac317
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2019
ms.locfileid: "55229983"
---
# <a name="apply-features-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Anwenden von Einstellungen für Funktionen auf Ihren Geräten mit Geräteprofilen in Microsoft Intune

Microsoft Intune umfasst Einstellungen und Funktionen, die Sie auf unterschiedlichen Geräten in Ihrer Organisation aktivieren oder deaktivieren können. Diese Einstellungen und Funktionen werden zu „Konfigurationsprofilen“ hinzugefügt. Sie können Profile für verschiedene Geräte und Plattformen erstellen, wie iOS, Android und Windows, und dann mit Intune das Profil auf Geräte in Ihrem Unternehmen anwenden.

Beispiele für Profile:

- Verwenden Sie auf Windows 10-Geräten eine Profilvorlage, die ActiveX-Steuerelemente im Internet Explorer blockiert.
- Ermöglichen Sie es Benutzern auf iOS- und macOS-Geräten, AirPrint-Drucker in Ihrer Organisation zu verwenden.
- Gewähren oder verhindern Sie den Zugriff per Bluetooth auf das Gerät.
- Erstellen Sie ein WLAN- oder VPN-Profil, das verschiedenen Geräten den Zugriff auf Ihr Unternehmensnetzwerk ermöglicht.
- Verwalten Sie Softwareupdates, auch wenn sie installiert sind.
- Führen Sie ein Android-Gerät als dediziertes Kioskgerät aus, auf dem bei Bedarf auch mehr als eine App ausgeführt werden kann.

Dieser Artikel listet die Schritte zum Erstellen eines Profils auf und gibt einen Überblick über die verschiedenen Profiltypen, die Sie erstellen können. Verwenden Sie diese Profile, um bestimmte Funktionen auf den Geräten zuzulassen oder zu verhindern.

## <a name="create-the-profile"></a>Erstellen des Profils

1. Wählen Sie im [Azure-Portal](https://portal.azure.com) die Option **Alle Dienste** aus, filtern Sie nach **Intune**, und wählen Sie anschließend **Intune** aus.

2. Wählen Sie **Gerätekonfiguration** aus. Hierzu stehen Ihnen folgende Optionen zur Verfügung:

    - **Übersicht:** Hier werden die Status Ihrer Profile sowie weitere Details zu den Profilen angezeigt, die Sie Benutzern und Geräten zugewiesen haben.
    - **Verwalten:** Erstellen Sie Geräteprofile, und laden Sie benutzerdefinierte [PowerShell-Skripts](intune-management-extension.md) zur Ausführung im Profil hoch. Fügen Sie mit [eSIM](esim-device-configuration.md) Datenpläne zu Geräten hinzu.
    - **Überwachen:** Prüfen Sie den Status eines Profils, und zeigen Sie Protokolle zu Ihren Profilen an.
    - **Setup:** Fügen Sie eine Zertifizierungsstelle (SCEP oder PFX) hinzu, oder aktivieren Sie [Telecom Expense Management](telecom-expenses-monitor.md) für das Profil.

3. Wählen Sie **Profile** > **Profil erstellen** aus. Geben Sie die folgenden Eigenschaften ein:

   - **Name**: Geben Sie einen aussagekräftigen Namen für das Profil ein.
   - **Beschreibung**: Geben Sie eine Beschreibung für das Profil ein. Diese Einstellung ist optional, wird jedoch empfohlen.
   - **Plattform**: Wählen Sie die Plattform Ihrer Geräte aus. Folgende Optionen sind verfügbar:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 und höher**
       - **Windows 10 und höher**

   - **Profiltyp**: Wählen Sie den Typ der Einstellungen aus, den Sie erstellen möchten. Die angezeigte Liste variiert je nach ausgewählter **Plattform**.

       - [Administrative Vorlagen](administrative-templates-windows.md)
       - [Benutzerdefiniert](custom-settings-configure.md)
       - [Übermittlungsoptimierung](delivery-optimization-windows.md)
       - [Gerätefeatures](device-features-configure.md)
       - [Geräteeinschränkungen](device-restrictions-configure.md)
       - [Editionsupgrade und Moduswechsel](edition-upgrade-configure-windows-10.md)
       - [Bildungswesen](education-settings-configure.md)
       - [E-Mail](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Identity Protection](identity-protection-configure.md)  
       - [Kiosk](kiosk-settings.md)
       - [PKCS-Zertifikat](certficates-pfx-configure.md)
       - [SCEP-Zertifikat](certificates-scep-configure.md)
       - [ Vertrauenswürdiges Zertifikat](certificates-configure.md)
       - [Updaterichtlinien](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [WLAN](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Wenn Sie beispielsweise **iOS** für die Plattform auswählen, werden folgende Optionen für den Profiltyp angezeigt:

     ![Erstellen eines iOS-Profils in Intune](./media/create-device-profile.png)

4. Klicken Sie auf **Einstellungen**. Die Einstellungen sind nach Kategorien geordnet. Wählen Sie eine Kategorie aus, um eine Liste aller Einstellungen anzuzeigen, die Sie konfigurieren können.

5. Wählen Sie anschließend **OK** > **Erstellen** aus, um Ihre Änderungen zu speichern.

Weitere Informationen zu den verschiedenen Profiltypen finden Sie in den nächsten Abschnitten dieses Artikels.

## <a name="administrative-templates-preview"></a>Administrative Vorlagen (Vorschau)

[Administrative Vorlagen](administrative-templates-windows.md) enthält Hunderte von Einstellungen, die Sie für Internet Explorer, OneDrive, Remotedesktop, Word, Excel oder andere Office-Programme und vieles mehr konfigurieren können.

Diese Vorlagen bieten Administratoren eine einfache und vereinfachte Ansicht der Einstellungen ähnlich der Gruppenrichtlinie, sind aber zu 100 Prozent cloudbasiert. 

Dieses Features unterstützt folgende Betriebssysteme:

- Windows 10 und höher

## <a name="device-features"></a>Gerätefunktionen

Mit [Gerätefunktionen](device-features-configure.md) können Sie Funktionen auf iOS- und macOS-Geräten steuern, z.B. AirPrint, Benachrichtigungen und Nachrichten auf dem Sperrbildschirm.

Dieses Features unterstützt folgende Betriebssysteme:

- iOS 
- macOS

## <a name="device-restrictions"></a>Geräteeinschränkungen

Mit [Geräteeinschränkungen](device-restrictions-configure.md) werden Einstellungen für Sicherheit, Hardware, Datenfreigabe und viele andere Einstellungen auf dem Gerät gesteuert. Sie können beispielsweise ein Geräteeinschränkungsprofil erstellen, das verhindert, dass Benutzer von iOS-Geräten auf die Kamera des Geräts zugreifen. 

Dieses Features unterstützt folgende Betriebssysteme:

- Android
- Android Enterprise
- iOS
- macOS
- Windows 10 und höher
- Windows 10 Team

## <a name="delivery-optimization"></a>Übermittlungsoptimierung

[Übermittlungsoptimierung](delivery-optimization-windows.md) macht das Bereitstellen von Softwareupdates benutzerfreundlicher. Diese Einstellungen ersetzen die **Softwareupdates** > **Windows 10-Updatering**-Einstellungen.

Verwenden Sie diese Einstellungen, um zu steuern, wie Softwareupdates auf Geräte in Ihrer Organisation heruntergeladen werden. Beispielsweise können Sie Benutzer ihre eigenen Updates erhalten lassen, oder Updates, die die Übermittlungsoptimierungs-Clouddienste in einem Geräteprofil verwenden.

Dieses Features unterstützt folgende Betriebssysteme:

- Windows 10 und höher

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

Kioskeinstellungen sind auch als Geräteeinschränkungen für [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) und [ios](device-restrictions-ios.md#kiosk-supervised-only) verfügbar.

## <a name="email"></a>E-Mail

Mit [E-Mail-Einstellungen](email-settings-configure.md) können Sie Exchange ActiveSync-E-Mail-Einstellungen auf den Geräten erstellen, zuweisen und überwachen. E-Mail-Profile helfen bei der Einheitlichkeit, beim Reduzieren der Anzahl von Supportanfragen und ermöglichen Endbenutzern den Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten, ohne dass ihrerseits eine Konfiguration erforderlich wäre. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- Windows Phone 8.1
- Windows 10 und höher

## <a name="vpn"></a>VPN

Mit [VPN-Einstellungen](vpn-settings-configure.md) können Sie Benutzern und Geräten in Ihrer Organisation VPN-Profile zuweisen, damit diese einfach eine sichere Verbindung mit dem Netzwerk herstellen können. 

Virtuelle private Netzwerke (Virtual Private Networks, VPNs) ermöglichen Benutzern einen sicheren Remotezugriff auf Ihr Unternehmensnetzwerk. Mit einem VPN-Verbindungsprofil stellen Geräte eine Verbindung mit dem VPN-Server her. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 und höher

## <a name="wi-fi"></a>WLAN

Mit [WLAN-Einstellungen](wi-fi-settings-configure.md) können Sie Benutzern und Geräten WLAN-Einstellungen zuweisen. Wenn Sie ein WLAN-Profil zuweisen, erhalten Benutzer Zugriff auf Ihr Unternehmens-WLAN, ohne es selbst konfigurieren zu müssen. 

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- macOS
- Windows 8.1 (nur Import)
- Windows 10 und höher

## <a name="esim-cellular---public-preview"></a>eSIM-Mobiltelefone: Public Preview

Mit [eSIM-Mobilfunkprofilen](esim-device-configuration.md) können Administratoren Tarife für Mobilfunkdaten auf Ihren verwalteten Geräten für den Zugriff auf das Internet und auf Daten konfigurieren. Sobald Sie Aktivierungscodes von Ihrem Mobilfunkanbieter erhalten haben, verwenden Sie Intune, um diese Codes zu importieren und dann Ihren auf eSIM ausgelegten Geräten zuzuweisen.

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

Informationen zu Updaterichtlinien für Windows-Geräte finden Sie unter [Übermittlungsoptimierung](delivery-optimization-windows.md). 

Dieses Features unterstützt folgende Betriebssysteme:
- iOS

## <a name="certificates"></a>Zertifikate

Mit [Zertifikate](certificates-configure.md) können Sie vertrauenswürdige SCEP- und PKCS-Zertifikate konfigurieren, die Geräten zugewiesen und zum Authentifizieren von WLAN-, VPN- und E-Mail-Profilen verwendet werden.

Dieses Features unterstützt folgende Betriebssysteme: 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 und höher

## <a name="windows-information-protection-profile"></a>WIP-Profil (Windows Information Protection)

[Windows Information Protection](windows-information-protection-configure.md) unterstützt Sie dabei, das Unternehmen vor Datenlecks zu schützen, ohne gleichzeitig die Benutzerfreundlichkeit für die Mitarbeiter einzuschränken. Die Lösung schützt auch Unternehmens-Apps und -daten vor versehentlichen Datenlecks auf unternehmenseigenen sowie auf persönlichen Geräten, die die Mitarbeiter bei der Arbeit verwenden. Die Verwendung von Windows Information Protection setzt keine Änderungen Ihrer Umgebung oder andere Apps voraus.

Dieses Features unterstützt folgende Betriebssysteme:

- Windows 10 und höher

## <a name="shared-multi-user-device"></a>Von mehreren Benutzern gemeinsam verwendetes Gerät

[Windows 10](shared-user-device-settings-windows.md) und [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) umfassen Einstellungen zur Verwaltung von Geräten mit mehreren Benutzern, auch bekannt als freigegebene Geräte oder freigegebene PCs. Wenn sich ein Benutzer bei dem Gerät anmeldet, wählen Sie aus, ob der Benutzer die Optionen des Energiesparmodus ändern oder Dateien auf dem Gerät speichern kann. Ein weiteres Beispiel ist das Erstellen einer Richtlinie, die inaktive Anmeldeinformationen von Windows HoloLens-Geräten löscht, um Speicherplatz zu sparen.

Diese Einstellungen für von mehreren Benutzern gemeinsam verwendete Geräte ermöglichen es einem Administrator, einige der Gerätefunktionen zu steuern und diese freigegebenen Geräte mit Intune zu verwalten.

Dieses Features unterstützt folgende Betriebssysteme:

- Windows 10 und höher
- Windows Holographic for Business

## <a name="custom-profile"></a>Benutzerdefiniertes Profil

Mithilfe von [benutzerdefinierten Einstellungen](custom-settings-configure.md) können Administratoren Geräteeinstellungen zuweisen, die nicht in Intune integriert sind. So können beispielsweise auf Android-Geräten OMA-URI-Werte eingegeben werden. Auf iOS-Geräten können Sie eine Konfigurationsdatei importieren, die Sie in Apple Configurator erstellt haben. 

Dieses Features unterstützt folgende Betriebssysteme:

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>Verwaltung und Problembehandlung

[Verwalten Sie Ihre Profile](device-profile-monitor.md), um den Status von Geräten und die zugewiesenen Profile zu überprüfen. Lösen Sie Konflikte leichter, indem Sie sich die Einstellungen ansehen, die Konflikte verursachen, und die Profile, die diese Einstellungen enthalten. Im Artikel zu [Häufigen Problemen und Lösungen](device-profile-troubleshoot.md) finden Sie eine Liste mit Fragen und Antworten, um Sie bei der Arbeit mit Profilen zu unterstützen. Dort erfahren Sie u.a., was beim Löschen eines Profils passiert und wodurch Benachrichtigungen an Geräte gesendet werden.

## <a name="next-steps"></a>Nächste Schritte
Wählen Sie Ihre Plattform aus, und legen Sie los:

