---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675492"
---
Diese Hinweise bieten wichtige Informationen, die Ihnen helfen kann für zukünftige Änderungen von Intune und Features vorbereiten. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Ändern Sie im registrierungsworkflow mit Intune-Unternehmensportal auf unternehmenseigene iOS-Geräten, die die Authentifizierung mit Setup-Assistenten <!-- 1927359 -->
Beim Setup mit besteht eine Anstehende Änderung der Workflow für die Registrierung von iOS-Geräte über eine Apple Unternehmens geräteregistrierungsmethoden – Apple Configurator, Apple Business Manager, Apple School Manager oder das Apple Device Enrollment Program (DEP), Assistent für die Authentifizierung. Diese Änderung gilt nur für Geräte mit benutzeraffinität registriert.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn diese Änderung im ~~März~~ April eingeführt wird, werden Registrierungsprofile in Intune im Azure-Portal aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Es fallen ein verbesserter Workflow zum Registrieren von iOS-Geräte über die oben aufgeführten Methoden. 

- Wenn neue Geräte registrieren und Authentifizieren mit Setup-Assistent, Sie auswählen, ob die Unternehmensportal-app automatisch bereitgestellt werden. Endbenutzer wird nicht mehr auf dem Bildschirm "Gerät identifizieren" und der "Bestätigen, dass Ihr Gerät"-Bildschirm in der Registrierungsvorgang angezeigt.  
- Auf Geräten, die bereits über den Setup-Assistenten über eine der Methoden für die Registrierung von Apple Gerät des Unternehmens registriert werden müssen Sie Maßnahmen ergreifen, wenn Sie den bedingten Zugriff aktivieren möchten. Sie müssen zum Konfigurieren einer app-Konfigurationsrichtlinie mit einer bestimmten XML-die Unternehmensportal-App bis hin zu diesen Geräten mithilfe von Push übertragen. Anweisungen hierzu sind im Blogbeitrag unter dem Link für zusätzliche Informationen. Wenn Sie die Unternehmensportal-App auf diese Weise mithilfe von Push übertragen möchten, sehen Endbenutzer nicht mehr dem Bildschirm "Gerät identifizieren" und der "Bestätigen, dass Ihr Gerät"-Bildschirm in den Registrierungsvorgang. 
- Nachdem diese Änderung eingeführt wird, wenn Sie mit der Unternehmensportal-App bereitgestellt haben die app-Konfigurationsprofil erwähnt und Endbenutzer-Download, die Unternehmensportal-app aus der App zu speichern, können sie sich anmelden, aber sie müssen eine Fehlermeldung erhalten. Sie wird nicht die app für den bedingten Zugriff verwenden können. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wenn Sie den geänderten Workflow verwenden möchten, müssen Sie Ihre Endbenutzer-Leitfaden, um anzugeben, dass aktualisieren möchten:

- Endbenutzer wird die beiden Bildschirme, die oben genannten, in der Registrierungsvorgang nicht mehr angezeigt werden. 
- Sie müssen für die Anmeldung auf der Unternehmensportal-App, wenn es automatisch bereitgestellt wird und nicht aus dem appstore herunterladen. 

Sie können auch eine app-Konfigurationsrichtlinie erstellen nun bei Bedarf als Vorbereitung für diese Änderung. Wenn dieses neue Workflows bereitgestellt wird, sehen Sie die aktualisierte registrierungsprofile in der Konsole. Wir werden auch der Durchführung der Bereitstellung über das Nachrichtencenter informiert. Danach müssen Sie die Maßnahmen ergreifen, damit Ihre Endbenutzer über DEP registrieren können, durch die Authentifizierung mit dem Setup-Assistenten, und Sie können die Unternehmensportal-App für den bedingten Zugriff verwenden.

Finden Sie unsere Unterstützung Blogbeitrag unter dem Link für zusätzliche Informationen Weitere Informationen zu dieser Änderung.

#### <a name="additional-information"></a>Weitere Informationen 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Geplante Änderung: Update der Benutzeroberfläche für die Intune-Unternehmensportal-App für iOS
Wir freuen uns, Ihnen mitteilen zu können, dass Intune in Kürze ein wichtiges Update für die iOS-Unternehmensportal-App veröffentlichen wird. Das Update wird ein visuelles Neugestaltung der Homepage mit erweiterten Filtern und schnellerem Zugriff auf Apps und Bücher beinhalten.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Dieses Update für die Benutzeroberfläche bietet weiterhin die aktuellen iOS-Unternehmensportal-Funktionalität und zudem:
- Eine Homepage mit nativem iOS-Layout 
- Filtermöglichkeiten für Inhaltslisten und -suche, einschließlich der Möglichkeit, nach Inhaltsart (Apps oder E-Books) und Verfügbarkeit („Geräteverwaltung erforderlich“ oder „Verfügbar ohne Registrierung“) zu filtern
- Möglichkeit, E-Books zu suchen
- Suchverlauf für apps und -e-Books

Wenn Sie am Apple TestFlight-Programm teilnehmen, werden Sie über die Vorabversion der aktualisierten iOS-Unternehmensportal-App von Intune informiert, sobald diese verfügbar ist. Wenn Sie nicht Teil des Apple TestFlight-Programms sind, können Sie sich immer noch registrieren. Durch eine Registrierung können Sie die aktualisierte Unternehmensportal-App verwenden, bevor sie Ihren Endbenutzern zur Verfügung steht. Sie können auch direkt dem Intune-Team Feedback bereitstellen.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie müssen keine Maßnahmen ergreifen. Diese Änderungen werden in einem kommenden Release der iOS-CP-App veröffentlicht. 

#### <a name="additional-information"></a>Weitere Informationen
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Überprüfen Sie die Einstellung "Verzögerung der Sichtbarkeit von Softwareupdates" in Intune 

Wir freigegebene in MC171466, die wir einige Einstellungen in der Konsole verschoben wurden. Mit dem März-Update zu Intune entfernen wir die Einstellung "Verzögerung Sichtbarkeit der Software updates" vollständig aus dem iOS-Blatt "Update-Richtlinie". Dies ändert sich nicht die Möglichkeit, Ihre geplante Softwareupdates angewendet werden sollen, aber es beeinträchtigen, wie lange die Sichtbarkeit eines Updates für Endbenutzer verzögert wird. Sie müssen möglicherweise Aktion vor dem Ende März, wenn Sie diese Einstellung verwenden. 

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Nach dem Update vom Februar Intune-Dienst werden Sie feststellen, dass die Einstellung angezeigt wird, dass beide in geräteeinschränkungsprofile in der Konsole und in iOS-Richtlinien auf dem Blatt der Software Update zu aktualisieren. Wenn Sie diese Änderung in der Konsole angezeigt wird, so sieht möglicherweise was Sie tun müssen.

- Für die vorhandenen Richtlinien für iOS: Wenn Sie benutzerdefinierte haben konfiguriert, diese Einstellung auf einen anderen als der Standardwert 30 Tage, und Ihre vorhandenen Konfigurationen für die Verzögerung sichtbarkeitseinstellung weiter nach dem Ende März angewendet werden soll, müssen Sie zum Erstellen eines neuen iOS-geräteeinschränkungsprofil. Hier wird die sichtbarkeitseinstellung Verzögerung müssen dieselben Werte wie in der vorhandenen iOS-updaterichtlinie aufweisen und denselben Gruppen angewendet werden. Nach dem Update März-Dienst werden nicht mehr Sie Werte für diese Einstellung in vorhandenen iOS-Updaterichtlinien bearbeiten, da es nicht mehr auf diesem Blatt angezeigt werden können. Sie werden stattdessen diese Einstellung in die neuen Profile konfigurieren.
  Wenn der Wert für die Anzahl von Tagen verzögert werden, kann Sichtbarkeit entspricht nicht an beiden Speicherorten für benutzerdefinierte konfigurierte Einstellungswerte, die Verzögerung Sichtbarkeit, die Einstellung nicht funktionieren, und Endbenutzer wird das Update auf ihren Geräten sehen, sobald diese verfügbar ist. Dies möglicherweise minimale Auswirkungen auf die für die meisten Kunden, da die anderen Einstellungen auf dem Blatt die Softwareupdaterichtlinie immer Vorrang vor über diese Einstellung in der Konsole erstellt haben.
- Neue Update-Richtlinien für iOS: Wenn Sie versuchen, neue Richtlinien auf dem Blatt des Software Updates nach dem Update des Intune-Februar-Dienst zu erstellen, sehen Sie diese Einstellung abgeblendet. Sehen Sie sich in der Konsole, die Sie zum Konfigurationsblatt Gerät umgeleitet werden, wenn Sie die Sichtbarkeit der Updates verzögern möchten.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie müssen keine Maßnahmen ergreifen, wenn Sie Sie diese Einstellung nicht verwenden oder nicht die Sichtbarkeit von Software-Updates für Ihre Endbenutzer zu verzögern möchten.

Wenn Sie die Sichtbarkeit der Updates verzögern möchten, beginnen, konfigurieren die Einstellung in neue Profile auf dem Blatt "Konfiguration" unter Geräteeinschränkungen > Allgemein. Wenn Sie dieser benutzerdefinierten Einstellung konfiguriert in vorhandenen iOS-Updaterichtlinien, erstellen eine neue entsprechende geräteeinschränkungsprofil mit den gleichen Wert für "Tage", um die Sichtbarkeit von Updates für Ihre Benutzer zu verzögern, nach das Februar aktualisieren, und aktualisieren Sie vor der Bereitstellung des März bereitgestellt wird. 

Möglicherweise möchten Ihre IT-Experten Anleitungen zu aktualisieren, und informieren Ihren Helpdesk.

Finden Sie unsere Unterstützung Blogbeitrag unter zusätzliche Informationen Weitere Informationen zum Konfigurieren dieser Einstellung.

#### <a name="additional-information"></a>Weitere Informationen 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>Planen der Änderung: bevorstehenden Fix für Windows 10-e-Mail-Profile in Intune <!--3904031-->
Wir aktualisieren die Möglichkeit, die Intune-e-Mail, die Profile für Windows 10 in der April zu, auf die Intune-Dienst ebenfalls einen Fehler zu beheben schreibt aktualisieren, stellen Sie sicher, dass Ihre e-Mail-Profile, die in zukünftigen Versionen von Windows 10 funktioniert weiterhin. Es sind Aktionen müssen Sie nach Abschluss dieses Updates bereitgestellt wird.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Diese Änderung wirkt sich auf Sie bei Verwendung von Windows 10-e-Mail-Profilen mit
- Der native E-Mail-Client unter Windows 10-Desktops oder
- Der Outlook-e-Mail-Client auf Windows 10 Mobile

Dies wirkt sich auf beide Kunden Intune Standalone und hybrider Verwaltung mobiler Geräte (MDM) aus.

Nachdem das Update von April bereitgestellt wird, müssen Sie diese Profile in der Intune-Verwaltungskonsole (in der Configuration Manager-Verwaltungskonsole, bei Verwendung einer MDM-hybridlösung) neu zu erstellen.

Wenn Sie keine Maßnahmen ergreifen, ist hier für die Profile erstellt wurden, vor dem Update von April angezeigt:

- Vorhandene e-Mail-Profile werden in den Status "Fehler" in der Intune-Verwaltungskonsole oder der Configuration Manager-Verwaltungskonsole angezeigt, aber Benutzer haben weiterhin Zugriff auf e-Mail-Adresse. Allerdings nach ein späteren Update von Windows bereitgestellt wird, funktioniert diese Profile nicht. Benutzern mit diesen Profilen Geräte verlieren den Zugriff auf e-Mails.
- Änderungen, die an diese Profile nach April in nicht angezeigt wird, als Ziel festgelegten Geräten.
- Selektives Zurücksetzen funktioniert nicht für das Entfernen dieser Profile, auch nachdem die Lösung im April eingeführt wird.

Wenn Sie Maßnahmen ergreifen und die e-Mail-Profile neu erstellen, müssen Endbenutzer Schritte ähneln denen durchlaufen zu lassen, wenn zum ersten Mal eine e-Mail-Profil bereitgestellt wird. Ihre e-Mails werden synchronisiert, bis sie das Update akzeptieren, das das neue Profil gilt blockiert.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Sie müssen Maßnahmen ergreifen, nachdem die Lösung mit dem Update von April eingeführt wird. Wir erreichen Sie Sie über das Nachrichtencenter, wenn diese Änderung online geschaltet wird, damit Sie beginnen können, um Ihre Profile in Intune neu zu erstellen.

Wenn Sie Windows 10-e-Mail-Profile in Intune verwenden, müssen Sie die folgenden Schritte ausführen:

1. Vorhandene Win 10-Profil-Einstellungen erfassen
2. Aufheben der Zuweisung bzw. löschen Sie vorhandene Profile
3. Neue Profile, die mit den erfassten Einstellungen erstellen und die neuen Profile denselben Gruppen zuweisen

Sie müssen Ihre Endbenutzer zu benachrichtigen, und lassen Ihren Helpdesk über diese Änderung kennen. Finden Sie im Blogbeitrag "Support" auf zusätzliche Informationen Fehlerdetails und Anweisungen für diese Profile neu zu erstellen.

#### <a name="additional-information"></a>Weitere Informationen
https://aka.ms/Win10EmailProfiles

