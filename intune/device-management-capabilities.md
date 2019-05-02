---
title: Verwaltungsfunktionen für Geräte in Microsoft Intune
description: In diesem Thema erfahren Sie, wie Intune Sie bei der Verwaltung registrierter Geräte unterstützen kann.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 293fa40b59d0005f60aad45a3fc42d3dd790857d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61510145"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Verwaltungsfunktionen für registrierte Geräte in Microsoft Intune

Mit Microsoft Intune können Sie eine Vielzahl von Geräten verwalten, indem Sie diese beim Dienst *registrieren*. Sie können einige Gerätetypen selbst registrieren, oder Benutzer können die Registrierung über die *Unternehmensportal*-App vornehmen. Durch die Registrierung können sie Apps durchsuchen und installieren, sicherstellen, dass ihre Geräte konform mit den Unternehmensrichtlinien sind und ihren IT-Support kontaktieren.

Dieser Artikel umfasst eine vollständige Liste der Funktionen, die Ihnen nach der Registrierung Ihrer Geräte zur Verfügung stehen.

Verwaltung, Bestandserfassung, App-Bereitstellung und Außerbetriebnahme erfolgen über Intune im Azure-Portal.

Benutzer erhalten Zugriff auf das Unternehmensportal, das es ihnen ermöglicht, Apps zu installieren, Geräte zu registrieren und zu entfernen und ihre IT-Abteilung oder ihren Helpdesk zu kontaktieren.



## <a name="device-security-and-configuration"></a>Gerätesicherheit und Konfiguration

|Funktion|Details|Weitere Informationen|
|--------------|-----------|--------------------|
|Konfigurationsrichtlinien<br><br>Benutzerdefinierte Richtlinien| Ermöglicht die Verwaltung vieler Einstellungen und Features auf mobilen Geräten in Ihrer Organisation. Beispielsweise kann das Anfordern eines Kennworts, das Beschränken der Anzahl misslungener Anmeldeversuche, das Begrenzen des Zeitraums bis zur Sperrung des Bildschirms, das Festlegen eines Zeitraums für den Kennwortablauf und das Unterbinden der erneuten Verwendung zuvor bereits verwendeter Kennwörter festgelegt werden. Sie können auch die Verwendung von Hardware- und Softwarefunktionen steuern, z.B. die Verwendung der Gerätekamera oder des Webbrowsers.<br><br>Verwenden Sie benutzerdefinierte Richtlinien, wenn Konfigurationsrichtlinien nicht die Einstellungen enthalten, die Sie benötigen. Bei iOS-Geräten können Sie die Einstellungen importieren, die Sie aus dem Apple Configurator-Tool exportiert haben. Bei anderen Geräten können Sie OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) verwenden, um Einstellungen und Features auf dem Gerät zu konfigurieren.|[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](device-compliance-get-started.md)|
|Remotezurücksetzen, Remotesperre und Kennungsrückstellung|Löscht sensible Daten, wenn ein Gerät verloren geht oder gestohlen wird. Beispielsweise können Sie das Gerät remote sperren, die Werkseinstellungen wiederherstellen oder nur Unternehmensdaten zurücksetzen.<br><br>Sie können Passcodes zurücksetzen, wenn Benutzer nicht mehr auf ihr Gerät zugreifen können, und verlorene oder gestohlene Geräte sperren oder alle darauf vorhandenen Daten zurücksetzen.|Geräteschutz durch [Remotesperre](device-remote-lock.md) und [Zurücksetzen der Kennung](device-passcode-reset.md)|
|Kioskmodus|Ermöglicht das Sperren bestimmter Features mobiler Geräte, z.B. der Bildschirmaufnahme und Netzschaltern. Außerdem können Sie Geräte auf die Ausführung einer einzigen, von Ihnen angegebenen App beschränken. |[Einstellungen für iOS-Konfigurationsrichtlinien in Microsoft Intune](device-restrictions-ios.md)|

## <a name="app-management"></a>App-Verwaltung

|Funktion|Details|Weitere Informationen|
|--------------|-----------|--------------------|
|App-Bereitstellung und -Verwaltung|Bietet eine Reihe von Tools zum Verwalten von mobilen Apps während deren Lebenszyklus, einschließlich der App-Bereitstellung von Installationsdateien und App Stores sowie eine detaillierte Überwachung des Status der App und App-Entfernung.|[Bereitstellen von Apps in Microsoft Intune](apps-deploy.md)|
|Konforme und nicht konforme Apps|Ermöglicht das Angeben von Listen der konformen Apps (die Benutzer installieren dürfen) und nicht konformen Apps (die Benutzer nicht installieren dürfen).|[iOS-Richtlinieneinstellungen in Microsoft Intune](device-restrictions-ios.md)|
|Mobile Anwendungsverwaltung|Konfiguriert die Einschränkungen für Apps, indem die mobile Anwendungsverwaltung für alle Geräte verwendet wird, die über Intune verwaltet oder nicht über Intune verwaltet werden. Sie können die Sicherheit Ihrer Unternehmensdaten erhöhen, indem Sie Vorgänge wie das Kopieren und Einfügen, die externe Sicherung von Daten und die Übertragung von Daten zwischen Apps einschränken.|[Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](app-wrapper-prepare-android.md)|
|Konfiguration mobiler iOS-Apps|Verwendet Konfigurationsrichtlinien für mobile Apps, um Einstellungen für iOS-Apps anzugeben, die beim Ausführen der App durch den Benutzer erforderlich sein können. Beispielsweise kann eine App erfordern, dass der Benutzer eine Portnummer oder Anmeldeinformationen angibt. Sie können die Konfiguration der App optimieren und die Anzahl von Anrufen beim Support verringern.|[Konfigurieren von iOS-Apps mit Konfigurationsrichtlinien für mobile Apps in Microsoft Intune](app-configuration-policies-use-ios.md)|
|Bereitstellungsprofile für mobile iOS-Apps|Hilft Ihnen, Bereitstellungsprofile für iOS-Apps bereitzustellen, die demnächst ablaufen. |[Verwenden von Richtlinien für mobile iOS-Bereitstellungsprofile, um zu verhindern, dass Apps ablaufen](app-provisioning-profile-ios.md)|
|Managed Browser|Konfiguriert die Richtlinien für verwaltete Browser zur Kontrolle der Websites, die Gerätebenutzer aufrufen können. Darüber hinaus können Sie Richtlinien zur mobilen Anwendungsverwaltung auf den Managed Browser anwenden.|[Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](app-configuration-managed-browser.md)|
|Windows Hello for Business|Ermöglicht die Integration in Windows Hello for Business. Dies ist eine alternative Anmeldemethode für Windows 10, die Active Directory (lokal) oder Azure Active Directory verwendet, um Kennwörter, Smartcards oder virtuelle Smartcards zu ersetzen.|[Steuern der Einstellungen von Windows Hello for Business auf Geräten mit Microsoft Intune](windows-hello.md)|
|Per Volumenlizenz erworbene Apps|Unterstützt Sie bei der Verwaltung von Apps, die über ein Volume Purchase Program erworben wurden. Dazu werden die Lizenzinformationen aus dem App Store importiert, es wird nachverfolgt, wie viele Lizenzen Sie verwendet haben, und verhindert, dass mehr App-Kopien installiert werden, als Sie erworben haben.|[Verwalten von Apps, die über ein Volumenprogramm erworben wurden, mithilfe von Microsoft Intune](vpp-apps.md)|

## <a name="company-resource-access"></a>Zugriff auf Unternehmensressourcen

|Funktion|Details|Weitere Informationen|
|--------------|-----------|--------------------|
|Zertifikatprofile|Erstellt vertrauenswürdige Zertifikatprofile und Simple Certificate Enrollment Protocol-Zertifikate (SCEP), die zum Sichern und Authentifizieren von WLAN-, VPN- und E-Mail-Profilen verwendet werden können, und stellt diese bereit.|[Sicherer Ressourcenzugriff mit Zertifikatprofilen in Microsoft Intune](certificates-configure.md)|
|WLAN-Profile|Stellt Einstellungen für drahtlose Netzwerke für Ihre Benutzer bereit. Durch das Bereitstellen dieser Einstellungen erleichtern Sie dem Benutzer das Herstellen einer Verbindung mit dem Unternehmensnetzwerk.|[WLAN-Verbindungen in Microsoft Intune](wi-fi-settings-configure.md)|
|E-Mail-Profile|Erstellt E-Mail-Einstellungen und stellt sie für Geräte bereit, sodass Benutzer geschäftliche E-Mails auf ihren privaten Geräten abrufen können, ohne diese Geräte zuvor einrichten zu müssen.|[Konfigurieren des Zugriffs auf Unternehmens-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](email-settings-configure.md)|
|VPN-Profile|Stellt VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation bereit. Durch das Bereitstellen dieser Einstellungen erleichtern Sie dem Benutzer das Verbinden mit Ressourcen im Unternehmensnetzwerk.|[VPN-Verbindungen in Microsoft Intune](device-profiles.md#vpn)|
|Bedingte Zugriffsrichtlinien|Verwaltet den Zugriff auf Microsoft Exchange-E-Mail und SharePoint Online auf Geräten, die nicht von Intune verwaltet werden.|[Beschränken des Zugriffs auf E-Mail und SharePoint mit Microsoft Intune](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Liste mit Geräten, die Sie verwalten können](device-management.md).
