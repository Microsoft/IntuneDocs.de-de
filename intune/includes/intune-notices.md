---
title: Datei einfügen
description: Datei einfügen
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: e745290991da4d80c7e3839250edbfdd64ef1b7a
ms.sourcegitcommit: 01c57ac880dcb5f474908977c89810f5bedaf326
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760964"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können.

### <a name="updated-feature-new-rbac-role-coming-to-intune--4253397--"></a>Aktualisiertes Feature: Neue RBAC-Rolle für Intune geplant<!--4253397-->
Im Januar-Update für den Intune-Dienst ist die Veröffentlichung einer neuen Sicherheitsrolle in Intune geplant. Diese Rolle wird in Intune als „Sicherheits-Manager für Endpunkte“ angezeigt und ist eine Erweiterung der Azure AD-Rolle „Sicherheitsadministrator“.
 
#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Aktuell stehen in Azure AD für Sicherheitsbeauftragte drei Rollen zur Verfügung:
- Mit der Rolle „Sicherheitsleseberechtigter“ in Azure AD wird Lesezugriff auf Intune erteilt.
- Mit der Rolle „Sicherheitsoperator“ in Azure AD wird Lesezugriff auf Intune erteilt.
- „Sicherheitsadministrator“ in Azure AD. Mit Veröffentlichung des Januar-Updates von Intune werden neben den Leseberechtigungen für Intune über die Rolle „Sicherheits-Manager für Endpunkte“ die folgenden neuen Berechtigungen erteilt:
    - Richtlinien zur Gerätekonformität: Lesen, Erstellen, Aktualisieren, Löschen, Zuweisen
    - Verwaltete Geräte: Lesen, Löschen, Aktualisieren
    - Sicherheitsbaselines: Lesen, Erstellen, Aktualisieren, Löschen, Zuweisen
    - Sicherheitsaufgaben: Lesen, Aktualisieren
 
### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun?
Überprüfen Sie noch heute Ihre Intune-RBAC-Rollen. Wenn Sie aktuell nur über die Rolle „Globale Administratoren“ verfügen, sind keine Änderungen erforderlich. Wenn Sie Rollen verwenden und die Granularität der Rolle „Sicherheits-Manager für Endpunkte“ nutzen möchten, weisen Sie diese Rolle zu, wenn Sie verfügbar ist. Auf der Intune-Seite [Neuerungen](../fundamentals/whats-new.md) finden Sie aktuelle Informationen zur Intune-Version. 

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Aktualisierte Unterstützungsanweisung für die mobile Adobe Acrobat Reader Intune-App<!--5746776-->
Ende August haben wir in MC188653 mitgeteilt, dass die mobile Adobe Acrobat Reader Intune-App am 1. Dezember 2019 eingestellt wird, und dass Adobe plant, die App-Schutzrichtlinien von Intune innerhalb ihrer Acrobat Reader-Haupt-App zu unterstützen. Seitdem haben wir Feedback der Kunden erhalten, dass die IT-Administratoren mehr Zeit benötigen, sich auf die Änderungen einzustellen, und dass die Endbenutzer mehr Zeit benötigen, Adobe Acrobat Reader für Intune zu verwenden. Angesichts der hohen Nutzung der Adobe Acrobat Reader Intune-App auf Endgeräten und deren Bedeutung für Unternehmensszenarios möchten wir sicherstellen, dass jede Funktion den Anforderungen Ihres Unternehmens an den App-Schutz entspricht. 

Während wir weiterhin empfehlen, die allgemeine mobile Acrobat Reader-App in Ihren Richtlinien zu verwenden, da diese App-Schutzrichtlinien unterstützt und das SDK für Intune integriert hat, wird die Adobe Acrobat Reader Intune-App bis zum 31. März 2020 weiterhin unterstützt. 

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Sie erhalten diese Nachricht, weil unsere Berichterstellung anzeigt, dass eine oder mehrere Richtlinien in Ihrer Organisation auf die Adobe Acrobat Reader Intune-App ausgerichtet sind und/oder Sie möglicherweise unsere vorherige EOL-Kommunikation erhalten haben. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun?
Informieren Sie Ihre Endbenutzer und Ihren Helpdesk über diese Änderung. Sie können die [Funktion der Unterstützungsfunktionalität des Unternehmensportals](../apps/company-portal-app.md#support-information) nutzen, um einen Kanal für Intune-bezogene Fragen einzurichten.

#### <a name="additional-information"></a>Weitere Informationen
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Einstellung der Unterstützung für Windows Phone 8.1<!--3544909-->
Die grundlegende Unterstützung von Microsoft für Windows Phone 8.1 wurde im Juli 2017 eingestellt, die erweiterte Unterstützung im Juni 2019. Die Unternehmensportal-App für Windows Phone 8.1 befindet sich seit Oktober 2017 im Unterstützungsmodus. Microsoft Intune wird nun am 20. Februar 2020 die Unterstützung für Windows Phone 8.1 einstellen.

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Nach dem 20. Februar 2020 erhalten diese Geräte keine Sicherheitsupdates mehr, und Sie können keine neuen Geräte mehr registrieren. Bestehende Windows Phone 8.1-Geräte bleiben weiterhin registriert (Richtlinien, Apps, Berichterstellung), aber beachten Sie, dass die Problembehandlung bei einer bestehenden Registrierung nach diesem Datum nicht mehr unterstützt wird, da viele Komponenten, wie z. B. Zertifikate von Drittanbietern, die Unterstützung für die Plattform nicht mehr verwenden. Intune stellt die Kompatibilitätsprüfung mit Intune und Windows Phone 8.1 ein.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun?
Sie können Ihre Intune-Berichterstellung überprüfen, um zu sehen, welche Geräte oder Benutzer möglicherweise betroffen sind. Navigieren Sie zu „Geräte“ > „Alle Geräte“, und filtern Sie nach Betriebssystem. Sie können weitere Spalten hinzufügen, um besser bestimmen zu können, welche Benutzer in Ihrer Organisation Geräte mit Windows Phone 8.1 verwenden. Fordern Sie Ihre Endbenutzer dazu auf, Ihre Geräte auf eine unterstützte Betriebssystemversion upzugraden.


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Maßnahme erforderlich: Verwenden von Microsoft Edge für Ihre geschützte Intune-Browserumgebung<!--5728447-->
Wie wir schon im letzten Jahr bekanntgemacht haben, unterstützt Microsoft Edge für mobile Geräte die gleichen Verwaltungsfeatures wie Managed Browser, bietet jedoch trotzdem eine verbesserte Endbenutzererfahrung. Um Platz für die robusten Microsoft Edge-Funktonen zu schaffen, stellen wir Intune Managed Browser ein. Ab dem 27. Januar 2020 wird Intune Managed Browser nicht länger von Intune unterstützt.  

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus? 
Ab dem 1. Februar 2020 wird Intune Managed Browser nicht länger im Google Play Store oder im iOS App Store verfügbar sein. Zu diesem Zeitpunkt haben Sie noch immer die Möglichkeit, neue App-Schutzrichtlinien für Intune Managed Browser zu verwenden, obwohl neue Benutzer die Intune Managed Browser-App nicht mehr herunterladen können. Zusätzliche werden unter iOS neue Webclips, die per Push auf mit MDM registrierte Geräte übertragen werden, in Microsoft Edge und nicht in Intune Managed Browser geöffnet.  

Am 31. März 2020 wird Intune Managed Browser aus der Azure-Konsole entfernt. Das heißt, dass Sie keine neuen Richtlinien für Intune Managed Browser mehr erstellen können. Wenn Sie noch vorhandene Intune Managed Browser-Richtlinien besitzen, sind diese nicht davon betroffen. Intune Managed Browser wird in der Konsole als Branchenanwendung ohne Symbol angezeigt, und vorhandene Richtlinien werden weiterhin auf die App bezogen angezeigt. An diesem Punkt wird auch die Option zum Umleiten von Webinhalt an Intune Managed Browser innerhalb des Abschnitts „Datenschutz“ der App-Schutzrichtlinien entfernt.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun? 
Um einen reibungslosen Übergang vom Intune Managed Browser zu Microsoft Edge sicherzustellen, empfiehlt es sich, die folgenden Schritte proaktiv auszuführen: 

1. Legen Sie für Microsoft Edge für iOS und Android App-Schutzrichtlinien (auch als MAM bezeichnet) sowie Konfigurationseinstellungen für Apps fest. Sie können Intune Managed Browser-Richtlinien für Microsoft Edge nochmals verwenden, indem Sie die vorhandenen Richtlinien auch auf Microsoft Edge ausrichten.  
2. Stellen Sie sicher, dass alle mit MAM geschützten Apps in Ihrer Umgebung über die gleiche App-Schutzrichtlinieneinstellung verfügen „Übertragung von Webinhalten mit anderen Apps einschränken:“ muss auf „Mit Richtlinien verwaltete Browser“ festgelegt sein. 
3. Legen Sie für alle mit MAM geschützten Apps die Konfigurationseinstellung „com.microsoft.intune.useEdge“ für verwaltete Apps auf „true“ (wahr) fest. Mit dem Release von Version 1911 nächsten Monat können Sie die Schritte 2 und 3 leicht durchführen, indem Sie für die Einstellung „Übertragung von Webinhalten mit anderen Apps einschränken“ die Option „Microsoft Edge“ über den Bereich „Datenschutz“ in Ihren App-Schutzrichtlinien festlegen. 

Die Unterstützung für Webclips unter iOS und Android ist bald verfügbar. Wenn diese Unterstützung veröffentlich müssen Sie bereits vorhandene Webclips neu zuweisen, um sicherzustellen, dass sie in Microsoft Edge und nicht mehr in Managed Browser geöffnet werden. 

#### <a name="additional-information"></a>Zusätzliche Informationen
Weitere Informationen finden Sie in unserer Dokumentation zur [Verwendung von Microsoft Edge mit App-Schutzrichtlinien](../apps/manage-microsoft-edge.md) oder in unserem [Blogbeitrag zur Unterstützung](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Stellen Sie sich auf eine Änderung ein: Aktualisierte Registrierung von dedizierten Android Enterprise-Geräten in Intune<!--5198878-->
Mit dem Novemberrelease (1911-Release) in Intune erhalten dedizierte Android Enterprise-Geräte mehr Unterstützung für die Bereitstellung von SCEP-Gerätezertifikaten, um den zertifikatbasierten Zugriff auf WLAN-Profile zu ermöglichen. Diese Änderung umfasst auch einige geringfügige Änderungen am Flow bei der Registrierung von dedizierten Android Enterprise-Geräten.

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Wenn Sie in Ihrer Umgebung dedizierte Android Enterprise-Geräte verwalten, werden Sie ab November einige Änderungen bemerken.

- Für neue Registrierungen von dedizierten Android Enterprise-Geräten: Endbenutzern werden während der Registrierung andere Schritte auf den Geräten angezeigt. Die Registrierung wird weiterhin gleich beginnen (mit QR, NFC, Zero Touch oder einem Gerätebezeichner), mit der Veröffentlichung der Dienstversion vom November wird jedoch ein obligatorischer App-Installationsschritt eingeführt.
- Für vorhandene Android-Geräte, die als dedizierte Geräte registriert sind: Intune startet die automatische Installation der Microsoft Intune-App auf Geräten ab Anfang November. Sie müssen also keine Maßnahmen ergreifen. Die App wird automatisch auf Geräte heruntergeladen und installiert. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf diese Änderung vorbereiten?
Planen Sie die Aktualisierung Ihres Endbenutzer-Leitfadens, und informieren Sie Ihren Helpdesk über diese Änderung. Klicken Sie für weitere Details und Screenshots auf „Zusätzliche Informationen“. Wir werden die Seite zu den Neuerungen aktualisieren, wenn die Einführung dieser Änderung beginnt.

#### <a name="additional-information"></a>Zusätzliche Informationen
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="end-of-support-for-legacy-pc-management"></a>Ende der Unterstützung für die Legacy-PC-Verwaltung

Legacy-PC-Verwaltungsfunktionen werden ab 15. Oktober 2020 nicht mehr unterstützt. Führen Sie ein Upgrade der Geräte auf Windows 10 aus, und registrieren Sie die Geräte neu als Geräte der Verwaltung mobiler Geräte (MDM), um diese weiterhin in Intune zu verwalten.

[Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Verringern der Unterstützung für den Android-Geräteadministrator 
Der Android-Geräteadministrator (mit Android 2.2 veröffentlicht und manchmal auch als „Legacy“-Android-Verwaltung bezeichnet) ist eine Möglichkeit zum Verwalten von Android-Geräten. [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (veröffentlicht mit Android 5.0) bietet jetzt jedoch eine verbesserte Verwaltungsfunktionalität. In dem Bestreben, auf eine moderne, umfassendere und sicherere Geräteverwaltung umzusteigen, reduziert Google die Geräteadministratorunterstützung in neuen Android-Releases.

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Die Änderungen von Google haben für Intune-Benutzer diese Folgen:  
- Intune bietet vollständige Unterstützung für Geräte, die vom Administrator verwaltet werden und auf denen Android 10 und höher bis zum zweiten Quartal CY2020 ausgeführt wird. Geräte, die vom Geräteadministrator verwaltet werden und nach Ablauf dieser Zeit Android 10 oder höher ausführen, können nicht vollständig verwaltet werden. Insbesondere werden betroffene Geräte keine neuen Kennwortanforderungen erhalten.
    - Samsung Knox-Geräte werden in diesem Zeitraum nicht betroffen sein, da Intune durch die Integration mit der Knox-Plattform erweiterte Unterstützung bietet. Dies gibt Ihnen mehr Zeit für die Planung des Übergangs von der Geräteadministratorverwaltung.    
- Vom Geräteadministrator verwaltete Android-Geräte, auf denen Android-Versionen unter 10 ausgeführt werden, sind nicht betroffen und können weiterhin vollständig mit dem Geräteadministrator verwaltet werden.    
- Für alle Geräte unter Android 10 und höher hat Google für Geräteadministratorverwaltung-Agents – wie z. B. das Unternehmensportal – die Möglichkeit beschränkt, auf Gerätebezeichnerinformationen zuzugreifen. Diese Einschränkung wirkt sich nach Geräteupdates auf Android 10 oder höher auf die folgenden Intune-Features wie folgt aus:  
    - Die Netzwerkzugriffssteuerung für VPN funktioniert nicht mehr.   
    - Die Identifizierung von Geräten mit IMEI oder Seriennummer als unternehmenseigen kennzeichnet Geräte nicht automatisch als unternehmenseigen.  
    - IMEI und Seriennummer sind für IT-Administratoren in Intune nicht mehr sichtbar. 
        > [!NOTE]
        > Dies betrifft nur vom Geräteadministrator verwaltete Geräte unter Android 10 und höher, nicht jedoch Geräte, die im Rahmen von Android Enterprise verwaltet werden. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun?
Wir empfehlen Folgendes, um die im dritten Quartal CY2020 auftretende Einschränkung der Funktionalität zu vermeiden:
- Binden Sie neue Geräte nicht in die Geräteadministratorverwaltung ein.
- Wenn zu erwarten ist, dass ein Gerät ein Update auf Android 10 erhalten wird, migrieren Sie es von der Geräteadministratorverwaltung zur Android Enterprise-Verwaltung und/oder zu App-Schutzrichtlinien.

#### <a name="additional-information"></a>Zusätzliche Informationen
- [Google-Leitfaden für die Migration vom Geräteadministrator zu Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Google-Dokumentation zum Plan, die Geräteadministrator-API als veraltet zu kennzeichnen](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Stellen Sie sich auf eine Änderung ein: Intune App SDK und App-Schutzrichtlinien für Android werden Android 5.0 und höher in einem zukünftigen Release unterstützen. <!--4911065 -->
Intune wird Android 5.x (Lollipop) und höher in einem zukünftigen Release unterstützen. Aktualisieren Sie alle umschließenden Apps mit dem neuesten Intune App SDK, und aktualisieren Sie Ihre Geräte.

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
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

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun?
Umschließen Sie Ihre Apps mit dem neuesten Intune App SDK. Sie können auch die Startbedingungseinstellung „Minimale Betriebssystemversion erforderlich (nur Warnung)“ festlegen, um die Endbenutzer auf persönlichen Geräten aufzufordern, das Upgrade durchzuführen.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Intune-Plan für die Änderung: Ende des Supports für Windows 7<!-- 3042987 -->
Wie wir im September 2018 in MC148476 sowie erneut im März 2019 in MC176794 angekündigt haben, endet der erweiterte Support für Windows 7 am 14. Januar 2020. Zu diesem Zeitpunkt stellt Intune die Unterstützung für Geräte unter Windows 7 ein, damit wir unsere Investitionen auf die Unterstützung neuerer Technologien und die Bereitstellung herausragender neuer Endbenutzerfunktionen fokussieren können. Nach diesem Datum sind technische Unterstützung und automatische Updates für den Schutz von Windows 7-PCs über Intune nicht mehr verfügbar. Microsoft empfiehlt dringend, vor Januar 2020 zu Windows 10 zu wechseln, um eine Situation zu vermeiden, in der Sie Service- oder Supportleistungen benötigen, die nicht mehr zur Verfügung stehen. [Hier](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) erfahren Sie mehr über den Windows-Supportlebenszyklus.

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Sie erhalten diese Nachricht, weil Sie zurzeit Windows 7-PCs über den veralteten Intune-PC-Software-Agent verwalten. Da bis zum Ende des erweiterten Windows 7-Supports weniger als ein Jahr Zeit bleibt, empfehlen wir Ihrer Organisation dringend, so bald wie möglich mit dem Upgrade auf Windows 10 zu beginnen.  

PC-Verwaltungsfunktionen sind direkt in das Windows 10-Betriebssystem integriert, und es ist nicht mehr notwendig, einen Client-Agent wie den Intune-Softwareclient für Windows 7 zu installieren. Seit Windows 8.1 verwendet Microsoft die MDM-Architektur (Mobile Device Management, mobile Geräteverwaltung) zum Bereitstellen, Konfigurieren, Aktualisieren und Verwalten von Windows-PCs. Wenn Sie Intune eingerichtet haben, können Sie die Windows-Registrierung vereinfachen, indem Sie den MDM-Kanal verwenden, um [Windows 10-PCs in Intune zu registrieren](..\windows-enroll.md). Wir empfehlen die Verwendung dieser MDM-Verwaltungslösung ohne Agent zum Verwalten Ihrer Windows 10-PCs.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Was muss ich als Vorbereitung auf diese Veränderung tun?
Wir empfehlen Ihrer Organisation, so schnell wie möglich folgenden Aktionsplan zu berücksichtigen:

- Sie sollten das Upgrade aller Windows 7-Geräte auf Windows 10 vor dem 14. Januar 2020 planen und durchführen.
- Erkunden Sie die [Unterstützung für die Windows 10-Bereitstellung](https://docs.microsoft.com/windows/deployment/), um mehr über das Upgrade vorhandener Geräte von Windows 7 auf Windows 10 zu erfahren.
- Informieren Sie sich über das Angebot [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1), das über Fast Track zur Verfügung steht und beim Microsoft-Versprechen der Anwendungskompatibilität hilft.
- Übertragen Sie vorhandene ältere Geräte, die über den Intune-Softwareclient verwaltet werden, in die von Microsoft empfohlene Lösung, um Windows 10 über MDM zu verwalten. Registrieren Sie alle neuen Windows 10-PCs über MDM für Intune im Azure-Portal.

Weitere Informationen finden Sie in [diesem Blogbeitrag](https://aka.ms/Windows7_Intune).


