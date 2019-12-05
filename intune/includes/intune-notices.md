---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 8db05399c4a880d72d24cde885976309bf9a4fa7
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74549417"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können.

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Aktualisierte Unterstützungsanweisung für die mobile Adobe Acrobat Reader Intune-App<!--5746776-->
Ende August haben wir in MC188653 mitgeteilt, dass die mobile Adobe Acrobat Reader Intune-App am 1. Dezember 2019 eingestellt wird, und dass Adobe plant, die App-Schutzrichtlinien von Intune innerhalb ihrer Acrobat Reader-Haupt-App zu unterstützen. Seitdem haben wir Feedback der Kunden erhalten, dass die IT-Administratoren mehr Zeit benötigen, sich auf die Änderungen einzustellen, und dass die Endbenutzer mehr Zeit benötigen, Adobe Acrobat Reader für Intune zu verwenden. Angesichts der hohen Nutzung der Adobe Acrobat Reader Intune-App auf Endgeräten und deren Bedeutung für Unternehmensszenarios möchten wir sicherstellen, dass jede Funktion den Anforderungen Ihres Unternehmens an den App-Schutz entspricht. 

Während wir weiterhin empfehlen, die allgemeine mobile Acrobat Reader-App in Ihren Richtlinien zu verwenden, da diese App-Schutzrichtlinien unterstützt und das SDK für Intune integriert hat, wird die Adobe Acrobat Reader Intune-App bis zum 31. März 2020 weiterhin unterstützt. 

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Sie erhalten diese Nachricht, weil unsere Berichterstellung anzeigt, dass eine oder mehrere Richtlinien in Ihrer Organisation auf die Adobe Acrobat Reader Intune-App ausgerichtet sind und/oder Sie möglicherweise unsere vorherige EOL-Kommunikation erhalten haben. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Informieren Sie Ihre Endbenutzer und Ihren Helpdesk über diese Änderung. Sie können die [Funktion der Unterstützungsfunktionalität des Unternehmensportals](../apps/company-portal-app.md#support-information) nutzen, um einen Kanal für Intune-bezogene Fragen einzurichten.

#### <a name="additional-information"></a>Weitere Informationen
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Einstellung der Unterstützung für Windows Phone 8.1<!--3544909-->
Die grundlegende Unterstützung von Microsoft für Windows Phone 8.1 wurde im Juli 2017 eingestellt, die erweiterte Unterstützung im Juni 2019. Die Unternehmensportal-App für Windows Phone 8.1 befindet sich seit Oktober 2017 im Unterstützungsmodus. Microsoft Intune wird nun am 20. Februar 2020 die Unterstützung für Windows Phone 8.1 einstellen.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Nach dem 20. Februar 2020 erhalten diese Geräte keine Sicherheitsupdates mehr, und Sie können keine neuen Geräte mehr registrieren. Bestehende Windows Phone 8.1-Geräte bleiben weiterhin registriert (Richtlinien, Apps, Berichterstellung), aber beachten Sie, dass die Problembehandlung bei einer bestehenden Registrierung nach diesem Datum nicht mehr unterstützt wird, da viele Komponenten, wie z. B. Zertifikate von Drittanbietern, die Unterstützung für die Plattform nicht mehr verwenden. Intune stellt die Kompatibilitätsprüfung mit Intune und Windows Phone 8.1 ein.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Sie können Ihre Intune-Berichterstellung überprüfen, um zu sehen, welche Geräte oder Benutzer möglicherweise betroffen sind. Navigieren Sie zu „Geräte“ > „Alle Geräte“, und filtern Sie nach Betriebssystem. Sie können weitere Spalten hinzufügen, um besser bestimmen zu können, welche Benutzer in Ihrer Organisation Geräte mit Windows Phone 8.1 verwenden. Fordern Sie Ihre Endbenutzer dazu auf, Ihre Geräte auf eine unterstützte Betriebssystemversion upzugraden.

### <a name="update-your-intune-outlook-app-protection-policies-app--2576686--"></a>Aktualisieren Ihrer Intune Outlook-App-Schutzrichtlinien (APP)<!--2576686-->
Sie sollten Maßnahmen ergreifen, wenn Sie MC195618 über Ihr Nachrichtencenter erhalten haben. Wie in den Feature IDs 56325 und 56326 der Microsoft 365-Roadmap geteilt, stellen Intune und Outlook für iOS und Android Unterstützung zur Einschränkung sensibler Daten in E-Mail-Benachrichtigungen und Kalendererinnerungen bereit. Als Folge dieser Verbesserungen entfernt Outlook für iOS und Android die Unterstützung für einige Konfigurationsschlüssel von Datenschutz-Apps, die Sie aktuell zum Verwalten von Benachrichtigungen nutzen.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Die neuen Features wurden noch nicht übermittelt. Wenn dies jedoch der Fall ist, funktionieren die folgenden App-Konfigurationsschlüssel nicht länger in Outlook für iOS und Android:
- com.microsoft.outlook.Mail.NotificationsEnabled
- com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed
- com.microsoft.outlook.Calendar.NotificationsEnabled
- com.microsoft.outlook.Calendar.NotificationsEnabled.UserChangeAllowed

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Es wird als Vorbereitung für dieses Feature empfohlen, die Datenschutzeinstellung „Benachrichtigungen zu Organisationsdaten“ für die Intune-App-Schutzrichtlinie mit dem Wert „Organisationsdaten blockieren“ zu konfigurieren. Ab 16. Dezember 2019 respektiert Outlook für iOS und Android die Datenschutzeinstellung „Benachrichtigungen zu Organisationsdaten“ und unterstützt nicht länger die oben genannten Schlüssel. Durch Konfiguration dieser neuen Einstellung wird sichergestellt, dass sensible Daten nicht kompromittiert werden, wenn die oben genannten Konfigurationsschlüssel nicht länger unterstützt werden. Zusätzlich stellt Outlook zusätzliche Granularität bereit, wenn die Datenschutzeinstellung „Benachrichtigungen zu Organisationsdaten“ auf „Organisationsdaten blockieren“ mit der zusätzlichen App-Konfigurationseinstellung „Kalenderbenachrichtigungen“ festgelegt wird. Die Konfiguration aus der Einstellung für die App-Schutzrichtlinie und der App-Konfigurationseinstellung reduziert sensible Informationen in E-Mail-Benachrichtigungen, während sensible Informationen in Kalenderbenachrichtigung verfügbar gemacht werden. So können Benutzer Ihre Termine auf einem Blick auf die Benachrichtigung oder in die Mitteilungszentrale sehen.

#### <a name="additional-information"></a>Zusätzliche Informationen
Weitere Informationen zu APP-Einstellungen und Outlook-Einstellungen finden Sie hier:
- [Einstellungen für App-Schutzrichtlinien für Android](../apps/app-protection-policy-settings-android.md)
- [Einstellungen für die App-Schutzrichtlinie für iOS](../apps/app-protection-policy-settings-ios.md)
- [Bereitstellen von Outlook für iOS- und Android-App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)


### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Intune-Plan für die Änderung: Windows 10, Version 1703: für das Unternehmensportal wird die Unterstützung entfernt<!--5026679-->
Windows 10, Version 1703 (auch als Windows 10 RS2 bekannt) wurde am 8. Oktober 2019 für Enterprise- und EDU-Editionen aus dem Betrieb genommen. Intune beendet die Unterstützung für die entsprechende Unternehmensportal-App für RS2/RS1 ab dem 26. Dezember 2019.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Des Weiteren werden in dieser bestimmten Version der Unternehmensportal-App keine neuen Features angezeigt, obwohl diese Version weiterhin bis zum 26. Dezember 2019 unterstützt wird. Zudem werden Sicherheitsupdates nach Bedarf für die Unternehmensportal-App bereitgestellt. Da die Windows 10 Version 1703 jedoch keine Sicherheitsupdates empfängt, sobald sie außer Betrieb genommen wird, wird dringend empfohlen, dass Sie Ihre Windows-Geräte auf eine neuere Windows-Version aktualisieren und sicherstellen, dass Sie die neueste Unternehmensportal-App besitzen, damit Sie weiterhin neue Features und zusätzliche Funktionen erhalten können.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Die Schritte, die Sie ausführen, hängen von der Konfiguration Ihrer Umgebung ab. Im Allgemeinen sollten Sie das Gerät identifizieren und aktualisieren, das die ältere Betriebssystemversion und/oder das Unternehmensportal auf dem Gerät besitzen. Zum Festlegen Ihrer Windows 10-Updateringe, melden Sie sich bei Intune an, wechseln Sie zu den Softwareupdates und anschließend zu „Windows 10-Updateringe“. Die neueste Version der Unternehmensportal-App lautet 10.3.5601.0. Weisen Sie Ihre Benutzer an, diese Version über den Microsoft Store herunterzuladen und somit für zukünftige Releases auf dem neuesten Stand zu bleiben. Sie können Intune auch zum Installieren der neuesten Version über [Microsoft Store für Unternehmen](https://docs.microsoft.com/intune/windows-store-for-business) auf Ihren Windows-Geräten verwenden.

#### <a name="additional-information"></a>Zusätzliche Informationen
[Manuelles Hinzufügen der Windows 10-Unternehmensportal-App mithilfe von Microsoft Intune](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Maßnahme erforderlich: Verwenden von Microsoft Edge für Ihre geschützte Intune-Browserumgebung<!--5728447-->
Wie wir schon im letzten Jahr bekanntgemacht haben, unterstützt Microsoft Edge für mobile Geräte die gleichen Verwaltungsfeatures wie Managed Browser, bietet jedoch trotzdem eine verbesserte Endbenutzererfahrung. Um Platz für die robusten Microsoft Edge-Funktonen zu schaffen, stellen wir Intune Managed Browser ein. Ab dem 27. Januar 2020 wird Intune Managed Browser nicht länger von Intune unterstützt.  

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich? 
Ab dem 1. Februar 2020 wird Intune Managed Browser nicht länger im Google Play Store oder im iOS App Store verfügbar sein. Zu diesem Zeitpunkt haben Sie noch immer die Möglichkeit, neue App-Schutzrichtlinien für Intune Managed Browser zu verwenden, obwohl neue Benutzer die Intune Managed Browser-App nicht mehr herunterladen können. Zusätzliche werden unter iOS neue Webclips, die per Push auf mit MDM registrierte Geräte übertragen werden, in Microsoft Edge und nicht in Intune Managed Browser geöffnet.  

Am 31. März 2020 wird Intune Managed Browser aus der Azure-Konsole entfernt. Das heißt, dass Sie keine neuen Richtlinien für Intune Managed Browser mehr erstellen können. Wenn Sie noch vorhandene Intune Managed Browser-Richtlinien besitzen, sind diese nicht davon betroffen. Intune Managed Browser wird in der Konsole als Branchenanwendung ohne Symbol angezeigt, und vorhandene Richtlinien werden weiterhin auf die App bezogen angezeigt. An diesem Punkt wird auch die Option zum Umleiten von Webinhalt an Intune Managed Browser innerhalb des Abschnitts „Datenschutz“ der App-Schutzrichtlinien entfernt.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten? 
Um einen reibungslosen Übergang vom Intune Managed Browser zu Microsoft Edge sicherzustellen, empfiehlt es sich, die folgenden Schritte proaktiv auszuführen: 

1. Legen Sie für Microsoft Edge für iOS und Android App-Schutzrichtlinien (auch als MAM bezeichnet) sowie Konfigurationseinstellungen für Apps fest. Sie können Intune Managed Browser-Richtlinien für Microsoft Edge nochmals verwenden, indem Sie die vorhandenen Richtlinien auch auf Microsoft Edge ausrichten.  
2. Stellen Sie sicher, dass alle mit MAM geschützten Apps in Ihrer Umgebung über die gleiche App-Schutzrichtlinieneinstellung verfügen „Übertragung von Webinhalten mit anderen Apps einschränken:“ muss auf „Mit Richtlinien verwaltete Browser“ festgelegt sein. 
3. Legen Sie für alle mit MAM geschützten Apps die Konfigurationseinstellung „com.microsoft.intune.useEdge“ für verwaltete Apps auf „true“ (wahr) fest. Mit dem Release von Version 1911 nächsten Monat können Sie die Schritte 2 und 3 leicht durchführen, indem Sie für die Einstellung „Übertragung von Webinhalten mit anderen Apps einschränken“ die Option „Microsoft Edge“ über den Bereich „Datenschutz“ in Ihren App-Schutzrichtlinien festlegen. 

Die Unterstützung für Webclips unter iOS und Android ist bald verfügbar. Wenn diese Unterstützung veröffentlich müssen Sie bereits vorhandene Webclips neu zuweisen, um sicherzustellen, dass sie in Microsoft Edge und nicht mehr in Managed Browser geöffnet werden. 

#### <a name="additional-information"></a>Zusätzliche Informationen
Weitere Informationen finden Sie in unserer Dokumentation zur [Verwendung von Microsoft Edge mit App-Schutzrichtlinien](../apps/manage-microsoft-edge.md) oder in unserem [Blogbeitrag zur Unterstützung](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Stellen Sie sich auf eine Änderung ein: Aktualisierte Registrierung von dedizierten Android Enterprise-Geräten in Intune<!--5198878-->
Mit dem Novemberrelease (1911-Release) in Intune erhalten dedizierte Android Enterprise-Geräte mehr Unterstützung für die Bereitstellung von SCEP-Gerätezertifikaten, um den zertifikatbasierten Zugriff auf WLAN-Profile zu ermöglichen. Diese Änderung umfasst auch einige geringfügige Änderungen am Flow bei der Registrierung von dedizierten Android Enterprise-Geräten.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Sie in Ihrer Umgebung dedizierte Android Enterprise-Geräte verwalten, werden Sie ab November einige Änderungen bemerken.

- Für neue Registrierungen von dedizierten Android Enterprise-Geräten: Endbenutzern werden während der Registrierung andere Schritte auf den Geräten angezeigt. Die Registrierung wird weiterhin gleich beginnen (mit QR, NFC, Zero Touch oder einem Gerätebezeichner), mit der Veröffentlichung der Dienstversion vom November wird jedoch ein obligatorischer App-Installationsschritt eingeführt.
- Für vorhandene Android-Geräte, die als dedizierte Geräte registriert sind: Intune startet die automatische Installation der Microsoft Intune-App auf Geräten ab Anfang November. Sie müssen also keine Maßnahmen ergreifen. Die App wird automatisch auf Geräte heruntergeladen und installiert. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Planen Sie die Aktualisierung Ihres Endbenutzer-Leitfadens, und informieren Sie Ihren Helpdesk über diese Änderung. Klicken Sie für weitere Details und Screenshots auf „Zusätzliche Informationen“. Wir werden die Seite zu den Neuerungen aktualisieren, wenn die Einführung dieser Änderung beginnt.

#### <a name="additional-information"></a>Zusätzliche Informationen
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="end-of-support-for-legacy-pc-management"></a>Ende der Unterstützung für die Legacy-PC-Verwaltung

Legacy-PC-Verwaltungsfunktionen werden ab 15. Oktober 2020 nicht mehr unterstützt. Führen Sie ein Upgrade der Geräte auf Windows 10 aus, und registrieren Sie die Geräte neu als Geräte der Verwaltung mobiler Geräte (MDM), um diese weiterhin in Intune zu verwalten.

[Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Verringern der Unterstützung für den Android-Geräteadministrator 
Der Android-Geräteadministrator (mit Android 2.2 veröffentlicht und manchmal auch als „Legacy“-Android-Verwaltung bezeichnet) ist eine Möglichkeit zum Verwalten von Android-Geräten. [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (veröffentlicht mit Android 5.0) bietet jetzt jedoch eine verbesserte Verwaltungsfunktionalität. In dem Bestreben, auf eine moderne, umfassendere und sicherere Geräteverwaltung umzusteigen, reduziert Google die Geräteadministratorunterstützung in neuen Android-Releases.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Diese Änderungen von Google haben für Intune-Benutzer diese Folgen:  
- Intune kann nur noch bis einschließlich Sommer 2020 Unterstützung für vom Geräteadministrator verwaltete Android-Geräte bieten, die unter Android 10 und höher (auch als Android Q bekannt) ausgeführt werden. Der Stichtag ist das Datum, an dem die nächste Hauptversion von Android veröffentlicht werden soll.   
- Vom Geräteadministrator verwaltete Geräte, auf denen nach dem Sommer 2020 Android 10 oder höher ausgeführt wird, können nicht mehr vollständig verwaltet werden.       
- Vom Geräteadministrator verwaltete Android-Geräte, auf denen Android-Versionen unter 10 ausgeführt werden, sind nicht betroffen und können weiterhin vollständig mit dem Geräteadministrator verwaltet werden.    
- Für alle Geräte unter Android 10 und höher hat Google für Geräteadministratorverwaltung-Agents – wie z. B. das Unternehmensportal – die Möglichkeit beschränkt, auf Gerätebezeichnerinformationen zuzugreifen. Diese Einschränkung wirkt sich nach Geräteupdates auf Android 10 oder höher auf die folgenden Intune-Features wie folgt aus:  
    - Die Netzwerkzugriffssteuerung für VPN funktioniert nicht mehr.   
    - Die Identifizierung von Geräten mit IMEI oder Seriennummer als unternehmenseigen kennzeichnet Geräte nicht automatisch als unternehmenseigen.  
    - IMEI und Seriennummer sind für IT-Administratoren in Intune nicht mehr sichtbar. 
        > [!NOTE]
        > Dies betrifft nur vom Geräteadministrator verwaltete Geräte unter Android 10 und höher, nicht jedoch Geräte, die im Rahmen von Android Enterprise verwaltet werden. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Um Einschränkungen der Funktionalität zu vermeiden, die ab Sommer 2020 eintreten werden, empfehlen wir Folgendes:
- Binden Sie neue Geräte nicht in die Geräteadministratorverwaltung ein.
- Wenn zu erwarten ist, dass ein Gerät ein Update auf Android 10 erhalten wird, migrieren Sie es von der Geräteadministratorverwaltung zur Android Enterprise-Verwaltung und/oder zu App-Schutzrichtlinien.

#### <a name="additional-information"></a>Zusätzliche Informationen
- [Google-Leitfaden für die Migration vom Geräteadministrator zu Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Google-Dokumentation zum Plan, die Geräteadministrator-API als veraltet zu kennzeichnen](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Stellen Sie sich auf eine Änderung ein: Intune App SDK und App-Schutzrichtlinien für Android werden Android 5.0 und höher in einem zukünftigen Release unterstützen. <!--4911065 -->
Intune wird Android 5.x (Lollipop) und höher in einem zukünftigen Release unterstützen. Aktualisieren Sie alle umschließenden Apps mit dem neuesten Intune App SDK, und aktualisieren Sie Ihre Geräte.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Sie weder das SDK noch App-Schutzrichtlinien für Android verwenden noch deren Verwendung planen, sind Sie von dieser Änderung nicht betroffen. Wenn Sie das Intune App SDK verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren, und aktualisieren Sie Ihre Geräte auch auf Android 5.x und höher. Wenn Sie nicht aktualisieren, erhalten Apps keine Updates, und das Benutzererlebnis wird sich mit der Zeit verschlechtern.

Unten finden Sie eine Liste der gängigen in Intune registrierten Geräte, auf denen Android Version 4.x ausgeführt wird. Wenn Sie über eines dieser Geräte verfügen, führen Sie die entsprechenden Schritte aus, um sicherzustellen, dass dieses Gerät Android-Version 5.0 oder höher unterstützt oder dass es durch ein Gerät ersetzt wird, das Android-Version 5.0 oder höher unterstützt. Diese Liste enthält nicht alle Geräte, die möglicherweise ausgewertet werden müssen:

- Samsung SM-T561  
- Samsung SM-T365
- Samsung gt-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Umschließen Sie Ihre Apps mit dem neuesten Intune App SDK. Sie können auch die Startbedingungseinstellung „Minimale Betriebssystemversion erforderlich (nur Warnung)“ festlegen, um die Endbenutzer auf persönlichen Geräten aufzufordern, das Upgrade durchzuführen.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune-Plan für die Änderung: Ende des Supports für Windows 7<!-- 3042987 -->
Wie wir im September 2018 in MC148476 sowie erneut im März 2019 in MC176794 angekündigt haben, endet der erweiterte Support für Windows 7 am 14. Januar 2020. Zu diesem Zeitpunkt stellt Intune die Unterstützung für Geräte unter Windows 7 ein, damit wir unsere Investitionen auf die Unterstützung neuerer Technologien und die Bereitstellung herausragender neuer Endbenutzerfunktionen fokussieren können. Nach diesem Datum sind technische Unterstützung und automatische Updates für den Schutz von Windows 7-PCs über Intune nicht mehr verfügbar. Microsoft empfiehlt dringend, vor Januar 2020 zu Windows 10 zu wechseln, um eine Situation zu vermeiden, in der Sie Service- oder Supportleistungen benötigen, die nicht mehr zur Verfügung stehen. [Hier](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) erfahren Sie mehr über den Windows-Supportlebenszyklus.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Sie erhalten diese Nachricht, weil Sie zurzeit Windows 7-PCs über den veralteten Intune-PC-Software-Agent verwalten. Da bis zum Ende des erweiterten Windows 7-Supports weniger als ein Jahr Zeit bleibt, empfehlen wir Ihrer Organisation dringend, so bald wie möglich mit dem Upgrade auf Windows 10 zu beginnen.  

PC-Verwaltungsfunktionen sind direkt in das Windows 10-Betriebssystem integriert, und es ist nicht mehr notwendig, einen Client-Agent wie den Intune-Softwareclient für Windows 7 zu installieren. Seit Windows 8.1 verwendet Microsoft die MDM-Architektur (Mobile Device Management, mobile Geräteverwaltung) zum Bereitstellen, Konfigurieren, Aktualisieren und Verwalten von Windows-PCs. Wenn Sie Intune eingerichtet haben, können Sie die Windows-Registrierung vereinfachen, indem Sie den MDM-Kanal verwenden, um [Windows 10-PCs in Intune zu registrieren](..\windows-enroll.md). Wir empfehlen die Verwendung dieser MDM-Verwaltungslösung ohne Agent zum Verwalten Ihrer Windows 10-PCs.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wir empfehlen Ihrer Organisation, so schnell wie möglich folgenden Aktionsplan zu berücksichtigen:

- Sie sollten das Upgrade aller Windows 7-Geräte auf Windows 10 vor dem 14. Januar 2020 planen und durchführen.
- Erkunden Sie die [Unterstützung für die Windows 10-Bereitstellung](https://docs.microsoft.com/windows/deployment/), um mehr über das Upgrade vorhandener Geräte von Windows 7 auf Windows 10 zu erfahren.
- Informieren Sie sich über das Angebot [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1), das über Fast Track zur Verfügung steht und beim Microsoft-Versprechen der Anwendungskompatibilität hilft.
- Übertragen Sie vorhandene ältere Geräte, die über den Intune-Softwareclient verwaltet werden, in die von Microsoft empfohlene Lösung, um Windows 10 über MDM zu verwalten. Registrieren Sie alle neuen Windows 10-PCs über MDM für Intune im Azure-Portal.

Weitere Informationen finden Sie in [diesem Blogbeitrag](https://aka.ms/Windows7_Intune).


