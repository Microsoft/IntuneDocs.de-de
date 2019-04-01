---
ms.openlocfilehash: dc86f2c22410236368753acd4dd3b66698037241
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57736856"
---

Diese Hinweise bieten wichtige Informationen, die Ihnen helfen kann für zukünftige Änderungen von Intune und Features vorbereiten. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Ändern Sie im registrierungsworkflow mit Intune-Unternehmensportal auf unternehmenseigene iOS-Geräten, die die Authentifizierung mit Setup-Assistenten <!-- 1927359 -->
Beim Setup mit besteht eine Anstehende Änderung der Workflow für die Registrierung von iOS-Geräte über eine Apple Unternehmens geräteregistrierungsmethoden – Apple Configurator, Apple Business Manager, Apple School Manager oder das Apple Device Enrollment Program (DEP), Assistent für die Authentifizierung. Diese Änderung gilt nur für Geräte mit benutzeraffinität registriert.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn diese Änderung im ~~März~~ April eingeführt wird, werden Registrierungsprofile in Intune im Azure-Portal aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Es fallen ein verbesserter Workflow zum Registrieren von iOS-Geräte über die oben aufgeführten Methoden. Hinweis:

- Wenn neue Geräte registrieren und Authentifizieren mit Setup-Assistent, Sie auswählen, ob die Unternehmensportal-app automatisch bereitgestellt werden. Endbenutzer wird nicht mehr auf dem Bildschirm "Gerät identifizieren" und der "Bestätigen, dass Ihr Gerät"-Bildschirm in der Registrierungsvorgang angezeigt.  
- Auf Geräten, die bereits über den Setup-Assistenten über eine der Methoden für die Registrierung von Apple Gerät des Unternehmens registriert werden müssen Sie Maßnahmen ergreifen, wenn Sie den bedingten Zugriff aktivieren möchten. Sie müssen zum Konfigurieren einer app-Konfigurationsrichtlinie mit einer bestimmten XML-die Unternehmensportal-App bis hin zu diesen Geräten mithilfe von Push übertragen. Anweisungen hierzu sind im Blogbeitrag unter dem Link für zusätzliche Informationen. Wenn Sie die Unternehmensportal-App auf diese Weise mithilfe von Push übertragen möchten, sehen Endbenutzer nicht mehr dem Bildschirm "Gerät identifizieren" und der "Bestätigen, dass Ihr Gerät"-Bildschirm in den Registrierungsvorgang. 
- Nachdem diese Änderung eingeführt wird, wenn Sie mit der Unternehmensportal-App bereitgestellt haben die app-Konfigurationsprofil erwähnt und Endbenutzer-Download, die Unternehmensportal-app aus der App zu speichern, sie müssen sich anmelden können, aber sie müssen eine Fehlermeldung erhalten. Sie wird nicht die app für den bedingten Zugriff verwenden können. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wenn Sie den geänderten Workflow verwenden möchten, müssen Sie Ihre Endbenutzer-Leitfaden, um anzugeben, dass aktualisieren möchten:

- Endbenutzer wird die beiden Bildschirme, die oben genannten, in der Registrierungsvorgang nicht mehr angezeigt werden. 
- Sie müssen für die Anmeldung auf der Unternehmensportal-App, wenn es automatisch bereitgestellt wird und nicht aus dem appstore herunterladen. 

Sie können auch eine app-Konfigurationsrichtlinie erstellen nun bei Bedarf als Vorbereitung für diese Änderung. Wenn dieses neue Workflows bereitgestellt wird, sehen Sie die aktualisierte registrierungsprofile in der Konsole. Wir werden auch der Durchführung der Bereitstellung über das Nachrichtencenter informiert. Danach müssen Sie die Maßnahmen ergreifen, damit Ihre Endbenutzer über DEP registrieren können, durch die Authentifizierung mit dem Setup-Assistenten, und Sie können die Unternehmensportal-App für den bedingten Zugriff verwenden.

Finden Sie unsere Unterstützung Blogbeitrag unter dem Link für zusätzliche Informationen Weitere Informationen zu dieser Änderung.

#### <a name="additional-information"></a>Weitere Informationen 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>Unternehmens-Portal-Änderungen für die iOS 12.2-Registrierung in Intune
In MC172534 wurde mitgeteilt, dass Apple einige Änderungen für die Registrierung von iOS-Geräten bei MDM-Diensten (mobile Geräteverwaltung) angekündigt hat. In der Veröffentlichung von iOS in der März-2019 stattfindende als auch für alle zukünftigen iOS-Versionen werden wahrscheinlich die Änderung angezeigt. Machen wir einige Updates in der Unternehmensportal-App, um Apple Änderungen widerzuspiegeln. 
 
#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Ihre Endbenutzer ihre Geräte für iOS 12.2 und höher aktualisieren, wissen Sie, dass ein geänderter Workflow vorhanden ist und sie zusätzliche Schritte, um vollständige Registrierung bei Intune ausführen müssen. Nach dem März-Update zu Intune ist hier was sie tun müssen:  

- Registrierung in der Unternehmensportal-app ein verwaltungsprofil herunterladen
- Wechseln Sie zu Einstellungen > Allgemein > Profile und suchen Sie nach einer roten signalbenachrichtigung
- Wählen Sie das richtige Profil aus, und klicken Sie auf Installieren
- Zurück zu der Unternehmensportal-App, um die Registrierung abschließen

Klicken Sie auf zusätzliche Informationen, ausführliche Informationen zu den Registrierungsvorgang.

Es sei denn, sie die Registrierung aufgehoben können und benötigen eine neue Registrierung, Geräte, die bereits registriert und ein Upgrade auf iOS 12.2 sind und höher sollten nicht beeinträchtigt werden. Die Benutzeroberfläche für die Registrierung von Geräten mit iOS 12.1 und früheren Versionen ist von diesem neuen Release von Apple nicht betroffen. Geräte, die durch mindestens einen Apple Registrierung beim Unternehmen Methoden (Device Enrollment Program, Apple School Manager oder Apple-Geschäftsleiter) registriert sind nicht betroffen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie sollten ein Upgrade für Ihre Dokumentation und Endbenutzeranleitung planen. Sie sollten auch Ihre Helpdesk-Mitarbeiter über diese Änderungen informieren. Wir halten Sie die informiert über unsere neue Seite neuerungen bei der diese Änderung online geschaltet wird. 

Wenn Sie die Unternehmensportal-App-Änderungen nutzen wir einführen möchten, stellen Sie Ihre Endbenutzer, aktualisieren Sie ihr Gerät auf die neue iOS-Version, nachdem das März-Update im Intune-Dienst beim Unternehmensportal-app-Version 3.9.0 zu. wird veröffentlicht.

Klicken Sie auf zusätzliche Informationen für einen Support-Blogbeitrag mit Vorschau Screenshots der Unternehmensportal-App-Änderungen ein.

Weitere Informationen [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Planen der Änderung: workflowänderungen für iOS-12-Registrierung in Intune
Apple hat einige Änderungen für die Registrierung von iOS-Geräten bei MDM-Diensten (mobile Geräteverwaltung) angekündigt. Die Änderungen werden vermutlich im iOS-Release für den Frühling 2019 und in den weiteren, zukünftigen iOS-Releases veröffentlicht.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Ihre Benutzer im Frühling ein Upgrade für ihre Geräte auf diese neue Version von iOS 12 durchführen, sollten Sie wissen, dass der Workflow geändert wurde und Ihre Benutzer zusätzliche Schritte vornehmen müssen, um die Registrierung bei Intune abzuschließen. Wenn Apple diese Änderungen eingeführt werden, müssen sich Endbenutzer auf:

- Registrierung in der Unternehmensportal-app ein verwaltungsprofil herunterladen
- Wechseln Sie zu Einstellungen > Allgemein > Profile
- Wählen Sie das richtige Profil aus, und klicken Sie auf Installieren
- Zurück zu der Unternehmensportal-App, um die Registrierung abschließen 

Geräte, die bereits registriert sind und für die ein Upgrade auf das neue iOS-Release durchgeführt wird, sollten von dieser Änderung nicht betroffen sein. Eine Ausnahme stellen Geräte dar, deren Registrierung aufgehoben wurde, wodurch eine neue Registrierung erforderlich wird.

Die Benutzeroberfläche für die Registrierung von Geräten mit iOS 12.1 und früheren Versionen ist von diesem neuen Release von Apple nicht betroffen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie sollten ein Upgrade für Ihre Dokumentation und Endbenutzeranleitung planen. Sie sollten auch Ihre Helpdesk-Mitarbeiter über diese Änderungen informieren. Weitere Informationen erhalten Sie über das Nachrichtencenter und die Seite zu den Neuerungen, sobald diese Änderung eingeführt wird.

#### <a name="additional-information"></a>Weitere Informationen
[Blogbeitrag mit Screenshots und Videos von der erwarteten Registrierungsvorgang unterstützen](https://aka.ms/iOS_enrollment_changes).

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Geplante Änderung: Update der Benutzeroberfläche für die Intune-Unternehmensportal-App für iOS
Wir freuen uns, Ihnen mitteilen zu können, dass Intune in Kürze ein wichtiges Update für die iOS-Unternehmensportal-App veröffentlichen wird. Das Update wird ein visuelles Neugestaltung der Homepage mit erweiterten Filtern und schnellerem Zugriff auf Apps und Bücher beinhalten.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Dieses Update für die Benutzeroberfläche bietet weiterhin die aktuellen iOS-Unternehmensportal-Funktionalität und zudem:
- Eine Homepage mit nativem iOS-Layout 
- Filtermöglichkeiten für Inhaltslisten und -suche, einschließlich der Möglichkeit, nach Inhaltsart (Apps oder E-Books) und Verfügbarkeit („Geräteverwaltung erforderlich“ oder „Verfügbar ohne Registrierung“) zu filtern
- Möglichkeit, E-Books zu suchen
- Suchverlauf für apps und -e-Books

Wenn Sie am Apple TestFlight-Programm teilnehmen, werden Sie über die Vorabversion der aktualisierten iOS-Unternehmensportal-App von Intune informiert, sobald diese verfügbar ist. Wenn Sie nicht Teil des Apple TestFlight-Programms sind, können Sie sich immer noch registrieren. Durch eine Registrierung können Sie die aktualisierte Unternehmensportal-App verwenden, bevor sie Ihren Endbenutzern zur Verfügung steht. Sie müssen auch das Intune-Team direkt Feedback bereitstellen können.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie müssen keine Maßnahmen ergreifen. Diese Änderungen werden in einem kommenden Release der iOS-CP-App veröffentlicht. 

#### <a name="additional-information"></a>Weitere Informationen
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>Erinnerung: Entfernen der vorhandenen Exchange Online, um Intune-connectors <!-- 3105122 -->
In MC165575 haben wir bekannt gegeben, dass wir die Exchange Online, um Intune "Service to Service"-Connector-Funktionalität in einem zukünftigen Update entfernt werden würde. Mit dem Update vom Februar an der Intune-Dienst werden deaktivieren wir die Schaltfläche, um neue Connectors einzurichten. Wir planen, entfernen Sie alle vorhandenen Exchange Online, um Intune-Connectors im März 2019.
 
#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Sie erhalten diese Nachricht, da Sie unseren Unterlagen zufolge die „Dienst-zu-Dienst“-Connectorfunktionalität in Ihrer Umgebung verwenden. Der Service to Service Connector unterstützt die Intune-Verwaltung von Exchange Active Sync Only-Geräten für Exchange Online und nicht die lokale Infrastruktur. Dieser Connector scheint aufgrund der Art, wie er in der Konsole angezeigt wird, für den bedingten Zugriff erforderlich zu sein, ist es in der Praxis jedoch nicht. Sie können diesen Connector bereits verwenden, um die Verwendung von Exchange Online zu verstehen, bevor Sie den bedingten Zugriff anwenden. Diese Informationen werden von Microsoft 365 Admin Center bereits bereitgestellt. Hier finden Sie Nutzungsberichte enthält, für Exchange Online, einschließlich der app ein, die für die zwischen 7 und 180 Tagen verwendet wird. Weitere Informationen finden Sie unter [Office 365-Berichte im Admin Center – Nutzung der-e-Mail-apps](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide).  
 
Wenn Sie diesen Connector in Ihrer Umgebung verwenden, können Sie nach dem Deaktivieren der Connectors im Februar keine Exchange Active Sync Only-Geräte in Intune mehr überwachen oder zurücksetzen. Während dieser Änderung werden keine Auswirkungen für Ihre Benutzer erwartet.
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Wenn Sie den „Dienst-zu-Dienst“-Connector eingerichtet haben und über Exchange Active Sync Only-Geräte verfügen, wechseln Sie zu anderen Methoden zum Verwalten Ihrer Geräte. Hierzu stehen Ihnen folgende Optionen zur Verfügung:

- Registrieren von Geräten in der mobilen Geräteverwaltung (Mobile Device Management, MDM) 
- Verwenden von App-Schutzrichtlinien zum Verwalten Ihrer Geräte 
- Verwenden Sie Exchange-Steuerelemente wie [hier](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) in der Dokumentation beschrieben. 

#### <a name="additional-information"></a>Weitere Informationen  
https://docs.microsoft.com/intune/exchange-service-connector-configure




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
