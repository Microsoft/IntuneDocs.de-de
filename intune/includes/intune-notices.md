---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: a2675b1b601261e673923ab5e3ac41d0f3d83264
ms.sourcegitcommit: 71b0cd7b81178e2f9e9f80830fa9a7985781628b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73057317"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können.

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>Stellen Sie sich auf eine Änderung ein: Die Einstellung „Serverseitige Protokollierung für Siri-Befehle“ wird aus der Intune-Konsole entfernt. <!-- 5468501-->

Wir planen, mit dem November-Update für den Intune-Dienst die Einstellung „Serverseitige Protokollierung für Siri-Befehle“ aus der Intune-Konsole zu entfernen. Diese Änderung erfolgt in Übereinstimmung mit Apple, da diese Einstellung seitens Apple bereits entfernt wurde.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Mitte November das November-Update (1911) bereitgestellt wird, werden Sie feststellen, dass diese Einstellung aus dem Intune-Konsolenmenü „Geräteeinschränkungen (integrierte Apps)“ für iOS-Konfigurationsprofile entfernt wurde. Die Einstellung wird möglicherweise noch in Ihren Richtlinien und im Verwaltungsprofil des Zielgeräts angezeigt, wird aber nicht auf das Gerät angewendet. Wir erwarten keine größeren Auswirkungen auf die Funktionalität, da die Einstellung auf Geräten derzeit nicht funktioniert, auch wenn sie im Verwaltungsprofil angezeigt wird.

Sie können aus zwei Möglichkeiten auswählen:
- Wenn Sie diese Einstellung aus Ihren Richtlinien löschen möchten, wechseln Sie zu dem Profil, in dem die Einstellung vorhanden ist, nehmen eine kleine Änderung vor und speichern das Profil. Die Richtlinie wird im Back-End neu berechnet, und die Einstellung wird aus der Richtlinie gelöscht.
- Wenn Sie diese Maßnahme nicht durchführen, wird diese Einstellung den Endbenutzern im Verwaltungsprofil auf ihren Geräten angezeigt, hat jedoch keine Auswirkungen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie können entsprechend dem obigen Abschnitt Maßnahmen ergreifen oder Ihre Richtlinie unverändert beibehalten. Wir werden die Seite mit Neuerungen und die Dokumentation aktualisieren, wenn das Rollout dieser Änderung erfolgt.

### <a name="end-of-support-for-legacy-pc-management"></a>Ende der Unterstützung für die Legacy-PC-Verwaltung

Legacy-PC-Verwaltungsfunktionen werden ab 15. Oktober 2020 nicht mehr unterstützt. Führen Sie ein Upgrade der Geräte auf Windows 10 aus, und registrieren Sie die Geräte neu als MDM-Geräte, um diese weiterhin in Intune zu verwalten.

[Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Verringern der Unterstützung für den Android-Geräteadministrator 
Der Android-Geräteadministrator (mit Android 2.2 veröffentlicht und manchmal auch als „Legacy“-Android-Verwaltung bezeichnet) ist eine Möglichkeit zum Verwalten von Android-Geräten. [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (veröffentlicht mit Android 5.0) bietet jetzt jedoch eine verbesserte Verwaltungsfunktionalität. In dem Bestreben, auf eine moderne, umfassendere und sicherere Geräteverwaltung umzusteigen, reduziert Google die Geräteadministratorunterstützung in neuen Android-Releases.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Diese Änderungen von Google haben für Intune-Benutzer diese Folgen:  
- Intune kann nur noch bis einschließlich Sommer 2020 Unterstützung für vom Geräteadministrator verwaltete Android-Geräte bieten, die unter Android 10 und höher (auch als Android Q bekannt) ausgeführt werden. Der Stichtag ist das Datum, an dem die nächste Hauptversion von Android veröffentlicht werden soll.   
- Vom Geräteadministrator verwaltete Geräte, auf denen nach dem Sommer 2020 Android 10 oder höher ausgeführt wird, können nicht mehr vollständig verwaltet werden.       
- Vom Geräteadministrator verwaltete Android-Geräte, auf denen Android-Versionen unter 10 ausgeführt werden, sind nicht betroffen und können weiterhin vollständig mit dem Geräteadministrator verwaltet werden.    
- Für alle Geräte unter Android 10 und höher hat Google für Geräteadministratorverwaltung-Agents – wie z. B. das Unternehmensportal – die Möglichkeit beschränkt, auf Gerätebezeichnerinformationen zuzugreifen. Dies wirkt sich nach Geräteupdates auf Android 10 oder höher auf die folgenden Intune-Features wie folgt aus:  
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

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aktualisieren Ihrer Android-Unternehmensportal-App auf die neueste Version <!--4536963-->
Intune veröffentlicht regelmäßig Versionsupdates für die Android-Unternehmensportal-App. Im November 2018 haben wir ein Unternehmensportal-Update veröffentlicht, das einen Back-End-Switch zur Vorbereitung auf den Wechsel von Google von der vorhandenen Benachrichtigungsplattform zum Google Firebase Cloud Messaging (FCM) enthielt. Wenn Google seine vorhandene Benachrichtigungsplattform außer Betrieb nimmt und zu FCM wechselt, müssen Endbenutzer ihre Unternehmensportal-App mindestens auf die Version von November 2018 aktualisiert haben, damit sie weiterhin mit dem Google Play Store kommunizieren können.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Unsere Telemetrie gibt an, dass Sie Geräte mit einer Unternehmensportal-Version vor 5.0.4269.0 haben. Wenn die Unternehmensportal-App nicht in dieser oder einer höheren Version installiert ist, funktionieren von IT-Experten initiierte Geräteaktionen wie Zurücksetzen des Geräts, Zurücksetzen von Kennwörtern, verfügbare und erforderliche App-Installationen sowie Zertifikatregistrierung möglicherweise nicht wie erwartet. Wenn Ihre Geräte in Intune für die mobile Geräteverwaltung registriert wurden, können Sie die Versionen und Benutzer des Unternehmensportals anzeigen, indem Sie zu „Client-Apps“ > „Ermittelte Apps“ wechseln. Durch Auswählen früherer Versionen der Unternehmensportal-App können Sie sehen, welche Endbenutzer über Geräte verfügen, bei denen die Unternehmensportal-App noch nicht aktualisiert wurde.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Bitten Sie Endbenutzer von Android-Geräten, die noch kein Update ausgeführt haben, die Unternehmensportal-App über Google Play zu aktualisieren. Benachrichtigen Sie Ihren Helpdesk, wenn ein Benutzer die automatische Aktualisierung der Unternehmensportal-App nicht durchgeführt hat. Über den Link in *Zusätzliche Informationen* finden Sie weitere Informationen zur FCM-Plattform und dem Wechsel von Google.

#### <a name="additional-information"></a>Zusätzliche Informationen
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Neue Vollbild-Benutzeroberfläche für Intune <!--4593669-->
Wir führen im Azure-Portal aktualisierte Benutzeroberflächen für Intune zum Erstellen und Bearbeiten ein. Diese neuen Oberflächen vereinfachen die vorhandenen Workflows, indem die Funktionen im Stil eines Assistenten auf einem einzigen Blatt zusammengefasst werden. Dank dieses Updates müssen Sie nicht mehr auf mehreren Blättern arbeiten und verschiedene Detailinformationen anzeigen, um Erstellungs- oder Bearbeitungsvorgänge durchzuführen. Die Workflows zum Erstellen werden ebenfalls aktualisiert und enthalten Zuweisungen (mit Ausnahme von App-Zuweisungen).

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Die Vollbild-Benutzeroberfläche für Intune wird in den kommenden Monaten sowohl in „portal.azure.com“ als auch in „devicemanagement.microsoft.com“ eingeführt. Dieses Update der Benutzeroberfläche wirkt sich nicht auf die Funktionsweise Ihrer vorhandenen Richtlinien und Profile aus, Sie werden aber feststellen, dass der Workflow leicht verändert wurde. Beim Erstellen neuer Richtlinien können Sie beispielsweise einige Zuweisungen bereits im Rahmen dieses Flows statt erst nach dem Erstellen der Richtlinie festlegen. Screenshots der neuen Benutzeroberfläche in der Konsole finden Sie im Blogbeitrag unter *Weitere Informationen*.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie müssen keine Maßnahmen ergreifen, sollten aber bei Bedarf Ihre Leitfäden für IT-Experten aktualisieren. Wir werden unsere Dokumentation aktualisieren, wenn diese Benutzeroberfläche auf den verschiedenen Blättern für Intune im Azure-Portal eingeführt wird.

#### <a name="additional-information"></a>Zusätzliche Informationen 
https://aka.ms/intune_fullscreen

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune-Plan für die Änderung: Ende des Supports für Windows 7 <!-- 3042987 -->
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
