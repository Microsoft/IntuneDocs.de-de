---
title: Verwaltungsfunktionen für registrierte Geräte
description: In diesem Thema erfahren Sie, wie Intune Sie bei der Verwaltung registrierter Geräte unterstützen kann.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/12/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 48b9650a8f0d6a79b3abab542148acf0a57c0e41
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Verwaltungsfunktionen für registrierte Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Mit Microsoft Intune können Sie eine Vielzahl von Geräten verwalten, indem Sie diese beim Dienst *registrieren*. Sie können einige Gerätetypen selbst registrieren, oder Benutzer können die Registrierung über die *Unternehmensportal*-App vornehmen. Diese ermöglicht Benutzern auch Vorgänge wie das Durchsuchen und Installieren von Apps, wobei sichergestellt wird, dass ihre Geräte mit den Unternehmensrichtlinien kompatibel sind, sowie das Kontaktieren des IT-Supports.

Dieses Thema bietet eine vollständige Liste der Funktionen, die Ihnen nach der Registrierung Ihrer Geräte zur Verfügung stehen.

Verwaltung, Bestandserfassung, Bereitstellung und Außerbetriebnahme von Geräten und Apps erfolgen über die Intune-Verwaltungskonsole. Benutzer erhalten Zugriff auf das Unternehmensportal, das es ihnen ermöglicht, Apps zu installieren, Geräte zu registrieren und zu entfernen und ihre IT-Abteilung oder ihren Helpdesk zu kontaktieren.



## <a name="device-security-and-configuration"></a>Gerätesicherheit und Konfiguration

|Funktion|Details|Weitere Informationen|
|--------------|-----------|--------------------|
|Konfigurationsrichtlinien<br><br>Benutzerdefinierte Richtlinien| Ermöglicht die Verwaltung vieler Einstellungen und Features auf mobilen Geräten in Ihrer Organisation. Beispielsweise kann das Anfordern eines Kennworts, das Beschränken der Anzahl misslungener Anmeldeversuche, das Begrenzen des Zeitraums bis zur Sperrung des Bildschirms, das Festlegen eines Zeitraums für den Kennwortablauf und das Unterbinden der erneuten Verwendung zuvor bereits verwendeter Kennwörter festgelegt werden. Sie können auch die Verwendung von Hardware- und Softwarefunktionen steuern, z.B. die Verwendung der Gerätekamera oder des Webbrowsers.<br><br>Verwenden Sie benutzerdefinierte Richtlinien, wenn Konfigurationsrichtlinien nicht die Einstellungen enthalten, die Sie benötigen. Bei iOS-Geräten können Sie die Einstellungen importieren, die Sie aus dem Apple Configurator-Tool exportiert haben. Bei anderen Geräten können Sie OMA-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) verwenden, um Einstellungen und Features auf dem Gerät zu konfigurieren.|[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)|
|Remotezurücksetzen, Remotesperre und Kennungsrückstellung|Löscht sensible Daten, wenn ein Gerät verloren geht oder gestohlen wird. Beispielsweise können Sie das Gerät remote sperren, die Werkseinstellungen wiederherstellen oder nur Unternehmensdaten zurücksetzen.<br><br>Sie können Passcodes zurücksetzen, wenn Benutzer nicht mehr auf ihr Gerät zugreifen können, und verlorene oder gestohlene Geräte sperren oder alle darauf vorhandenen Daten zurücksetzen.|[Geräteschutz durch Remotesperre und Zurücksetzen der Kennung](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)|
|Kioskmodus|Ermöglicht das Sperren bestimmter Features mobiler Geräte, z.B. der Bildschirmaufnahme und Netzschaltern. Außerdem können Sie Geräte auf die Ausführung einer einzigen, von Ihnen angegebenen App beschränken.|[Einstellungen für iOS-Konfigurationsrichtlinien in Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|

## <a name="app-management"></a>App-Verwaltung

|Funktion|Details|Weitere Informationen|
|--------------|-----------|--------------------|
|App-Bereitstellung und -Verwaltung|Bietet eine Reihe von Tools zum Verwalten von mobilen Apps während deren Lebenszyklus, einschließlich der App-Bereitstellung von Installationsdateien und App Stores sowie eine detaillierte Überwachung des Status der App und App-Entfernung.|[Bereitstellen von Apps in Microsoft Intune](/intune-classic/deploy-use/deploy-apps)|
|Konforme und nicht konforme Apps|Ermöglicht das Angeben von Listen der konformen Apps (die Benutzer installieren dürfen) und nicht konformen Apps (die Benutzer nicht installieren dürfen).|[iOS-Richtlinieneinstellungen in Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Mobile Anwendungsverwaltung|Konfiguriert die Einschränkungen für Apps, indem die mobile Anwendungsverwaltung für alle Geräte verwendet wird, die über Intune verwaltet oder nicht über Intune verwaltet werden. Dadurch können Sie die Sicherheit Ihrer Unternehmensdaten erhöhen, indem Sie Vorgänge wie das Kopieren und Einfügen, die externe Sicherung von Daten und die Übertragung von Daten zwischen Apps einschränken.|[Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/app-wrapper-prepare-android)|
|Konfiguration mobiler iOS-Apps|Verwendet Konfigurationsrichtlinien für mobile Apps, um Einstellungen für iOS-Apps anzugeben, die beim Ausführen der App durch den Benutzer erforderlich sein können. Beispielsweise kann eine App erfordern, dass der Benutzer eine Portnummer oder Anmeldeinformationen angibt. Dies kann helfen, die Konfiguration der App zu optimieren und die Anzahl von Anrufen beim Support zu verringern.|[Konfigurieren von iOS-Apps mit Konfigurationsrichtlinien für mobile Apps in Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Bereitstellungsprofile für mobile iOS-Apps|Hilft Ihnen, Bereitstellungsprofile für iOS-Apps bereitzustellen, die demnächst ablaufen. |[Verwenden von Richtlinien für mobile iOS-Bereitstellungsprofile, um zu verhindern, dass Apps ablaufen](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)|
|Managed Browser|Konfiguriert die Richtlinien für verwaltete Browser zur Kontrolle der Websites, die Gerätebenutzer aufrufen können. Darüber hinaus können Sie Richtlinien zur mobilen Anwendungsverwaltung auf den Managed Browser anwenden.|[Verwalten des Internetzugriffs mittels Richtlinien für Managed Browser mit Microsoft Intune](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello for Business|Ermöglicht die Integration in Windows Hello for Business. Dies ist eine alternative Anmeldemethode für Windows 10, die Active Directory (lokal) oder Azure Active Directory verwendet, um Kennwörter, Smartcards oder virtuelle Smartcards zu ersetzen.|[Steuern der Einstellungen von Windows Hello for Business auf Geräten mit Microsoft Intune](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|Per Volumenlizenz erworbene Apps|Unterstützt Sie bei der Verwaltung von Apps, die über ein Volume Purchase Program erworben wurden. Dazu werden die Lizenzinformationen aus dem App Store importiert, es wird nachverfolgt, wie viele Lizenzen Sie verwendet haben, und verhindert, dass mehr App-Kopien installiert werden, als Sie erworben haben.|[Verwalten von Apps, die über ein Volumenprogramm erworben wurden, mithilfe von Microsoft Intune](/intune-classic/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## <a name="company-resource-access"></a>Zugriff auf Unternehmensressourcen

|Funktion|Details|Weitere Informationen|
|--------------|-----------|--------------------|
|Zertifikatprofile|Erstellt vertrauenswürdige Zertifikatprofile und Simple Certificate Enrollment Protocol-Zertifikate (SCEP), die zum Sichern und Authentifizieren von WLAN-, VPN- und E-Mail-Profilen verwendet werden können, und stellt diese bereit.|[Sicherer Ressourcenzugriff mit Zertifikatprofilen in Microsoft Intune](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)|
|WLAN-Profile|Stellt Einstellungen für drahtlose Netzwerke für Ihre Benutzer bereit. Durch das Bereitstellen dieser Einstellungen erleichtern Sie dem Benutzer das Herstellen einer Verbindung mit dem Unternehmensnetzwerk.|[WLAN-Verbindungen in Microsoft Intune](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)|
|E-Mail-Profile|Erstellt E-Mail-Einstellungen für Geräte und stellt diese bereit. Dies bedeutet, dass Benutzer Zugriff auf Unternehmens-E-Mails auf ihren persönlichen Geräten erhalten, ohne dafür ein Setup vornehmen zu müssen.|[Konfigurieren des Zugriffs auf Unternehmens-E-Mail mithilfe von E-Mail-Profilen in Microsoft Intune](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN-Profile|Stellt VPN-Einstellungen für Benutzer und Geräte in Ihrer Organisation bereit. Durch das Bereitstellen dieser Einstellungen erleichtern Sie dem Benutzer das Verbinden mit Ressourcen im Unternehmensnetzwerk.|[VPN-Verbindungen in Microsoft Intune](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)|
|Bedingte Zugriffsrichtlinien|Verwaltet den Zugriff auf Microsoft Exchange-E-Mail und SharePoint Online auf Geräten, die nicht von Intune verwaltet werden.|[Beschränken des Zugriffs auf E-Mail und SharePoint mit Microsoft Intune](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## <a name="inventory-and-reporting"></a>Inventar und Berichterstellung

|       Funktion        |                                             Details                                              |                                                                  Weitere Informationen                                                                   |
|-------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Inventar und Berichterstellung | Sucht nach Informationen zu den Geräten, die Sie verwalten, und der Software, die die Geräte verwenden. | [Verstehen Sie Ihre Geräte mithilfe des Inventars in Microsoft Intune](/intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune) |

