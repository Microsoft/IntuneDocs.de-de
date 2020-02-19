---
title: Datei einfügen
description: Datei einfügen
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: d360fa5efe2deba2d19cd67e6ed9f8cbb7f864d9
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415071"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können.

### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Stellen Sie sich auf eine Änderung ein: Änderung bei der Registrierung von dedizierten Android Enterprise-Geräten in Intune<!--6114580-->
Mit dem Novemberrelease in Intune erhalten dedizierte Android Enterprise-Geräte mehr Unterstützung für die Bereitstellung von SCEP-Zertifikaten, um den zertifikatbasierten Zugriff auf WLAN-Profile zu ermöglichen. Diese Änderung umfasste einige geringfügige Änderungen des Registrierungsflows für dedizierte Android Enterprise-Geräte. Wir bitten Sie, einige weitere Änderungen im Zusammenhang mit dem bevorstehenden Dienstupdate von März oder 2003 zu beachten.

#### <a name="how-does-this-affect-me"></a>Wie wirkt sich das auf mich aus?
Wenn Sie in Ihrer Umgebung dedizierte Android Enterprise-Geräte verwalten, werden Sie ab März einige Änderungen bemerken.
- Für vorhandene dedizierte Android-Geräte, die vor dem 22. November 2019 oder dem 1911-Dienstupdate registriert wurden, gilt: Auf diesen Geräten ist die Microsoft Intune-App installiert. Nach der Einführung der Back-End-Änderungen im Intune-Dienst im März werden die SCEP-Zertifikate angewendet, die für Geräte bereitgestellt werden und mit WLAN-Profilen verknüpft sind.
- Für Geräte, die nach dem 22. November 2019 und vor dem Rollout dieser Änderung im März registriert wurden, gilt: Auf diesen Geräten ist die Microsoft Intune-App installiert. SCEP-Zertifikate, die für Geräte bereitgestellt werden und mit WLAN-Profilen verknüpft sind, werden weiterhin angewendet.
- Für neue Registrierungen von dedizierten Android Enterprise-Geräten nach dem Rollout der Änderungen im März gilt: Endbenutzern werden während der Registrierung andere Schritte auf den Geräten angezeigt. Die Registrierung wird weiterhin genauso beginnen wie jetzt (mit QR, NFC, Zero Touch oder einem Gerätebezeichner), es gibt jedoch keinen obligatorischen App-Installationsschritt. Stattdessen wird die Microsoft Intune-App automatisch auf Geräten installiert. Außerdem müssen Endbenutzer während des Flows nicht auf „Intune-Agent aktivieren“ tippen. Mit WLAN-Profilen verknüpfte SCEP-Zertifikate können auf diesen Geräten bereitgestellt werden.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf diese Änderung vorbereiten?
Sie können Ihren Endbenutzer-Leitfaden aktualisieren und Ihren Helpdesk über diese Änderung informieren. Wir aktualisieren unsere Seite „Neuigkeiten“ und benachrichtigen Sie über das Nachrichtencenter, wenn diese Änderung eingeführt wird.

#### <a name="additional-information"></a>Zusätzliche Informationen
[Support for SCEP certificates in Android Enterprise dedicated devices](https://aka.ms/Dedicated_devices_enrollment) (Unterstützung von SCEP-Zertifikaten durch dedizierte Android Enterprise-Geräte)

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


