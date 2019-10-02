---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: fa251a0edd943d566849b138af5cbab0be248a53
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726400"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können. 


### <a name="decreasing-support-for-android-device-administrator"></a>Verringern der Unterstützung für den Android-Geräteadministrator 
Der Android-Geräteadministrator (manchmal auch als „Legacy“-Android-Verwaltung bezeichnet und mit Android 2.2 veröffentlicht) ist eine Möglichkeit zum Verwalten von Android-Geräten. [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (veröffentlicht mit Android 5.0) bietet jetzt jedoch eine verbesserte Verwaltungsfunktionalität. In dem Bestreben, auf eine moderne, umfassendere und sicherere Geräteverwaltung umzusteigen, reduziert Google die Geräteadministratorunterstützung in neuen Android-Releases.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Diese Änderungen von Google haben für Intune-Benutzer diese Folgen: 
- Intune kann nur noch bis zum Sommer 2020 Unterstützung für unter Android 10 und höher (auch als Android Q bekannt) ausgeführte Android-Geräte bieten, die vom Geräteadministrator verwaltet werden. Dieses Datum liegt vor, wenn die nächste Hauptversion von Android veröffentlicht werden soll.  
- Vom Geräteadministrator verwaltete Geräte, auf denen Android 10 oder höher nach dem Sommer 2020 ausgeführt wird, können nicht mehr vollständig verwaltet werden.    
- Vom Geräteadministrator verwaltete Android-Geräte, auf denen Android-Versionen unter 10 ausgeführt werden, sind nicht betroffen und können weiterhin vollständig mit dem Geräteadministrator verwaltet werden.  
- Für alle Geräte mit Android 10 und höher hat Google für Geräteadministratorverwaltung-Agents wie Unternehmensportal die Möglichkeit beschränkt, auf Gerätebezeichnerinformationen zuzugreifen. Dies wirkt sich nach Geräteupdates auf Android 10 oder höher auf die folgenden Intune-Features wie folgt aus: 
    - Die Netzwerkzugriffssteuerung für VPN funktioniert nicht mehr.  
    - Die Identifizierung von Geräten mit IMEI oder Seriennummer als unternehmenseigen kennzeichnet Geräte nicht automatisch als unternehmenseigen. 
    - IMEI und Seriennummer sind für IT-Administratoren in Intune nicht mehr sichtbar. 
        > [!Note]
        > Dies betrifft nur vom Geräteadministrator verwaltete Geräte unter Android 10 und höher und nicht Geräte, die als Android Enterprise verwaltet werden. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Um die im Sommer 2020 kommende Verringerung der Funktionalität zu vermeiden, wird Folgendes empfohlen:
- Integrieren Sie neue Geräte nicht in die Geräteadministratorverwaltung.
- Wenn erwartet wird, dass ein Gerät ein Update auf Android 10 erhält, migrieren Sie es von der Geräteadministratorverwaltung zur Android Enterprise-Verwaltung und/oder zu App-Schutzrichtlinien (App Protection Policies).

#### <a name="additional-information"></a>Zusätzliche Informationen
- [Google-Leitfaden für die Migration vom Geräteadministrator zu Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Google-Dokumentation zum Plan, die Geräteadministrator-API als veraltet zu erklären](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aktualisieren Ihrer Android-Unternehmensportal-App auf die neueste Version <!--4536963-->
Intune veröffentlicht regelmäßig Versionsupdates für die Android-Unternehmensportal-App. Im November 2018 haben wir ein Unternehmensportal-Update veröffentlicht, das einen Back-End-Switch zur Vorbereitung auf den Google-Wechsel von der vorhandenen Benachrichtigungsplattform auf sein Firebase Cloud Messaging (FCM) enthielt. Wenn Google seine vorhandene Benachrichtigungsplattform außer Betrieb nimmt und zu FCM wechselt, müssen Endbenutzer ihre Unternehmensportal-App auf mindestens die Version von November 2018 aktualisiert haben, damit sie mit dem Google Play Store weiterhin kommunizieren können.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Unsere Telemetrie gibt an, dass Sie Geräte mit einer Unternehmensportal-Version vor 5.0.4269.0 haben. Wenn diese Version oder höher der Unternehmensportal-App nicht installiert wird, funktionieren von IT-Profis initiierte Geräteaktionen wie Wischen, Kennwort zurücksetzen, verfügbare und erforderliche App-Installationen und Zertifikatregistrierung möglicherweise nicht wie erwartet. Wenn Ihre Geräte in Intune für die mobile Geräteverwaltung registriert wurden, können Sie die Versionen und Benutzer des Unternehmensportals anzeigen, indem Sie zu „Client-Apps“ – „Ermittelte Apps“ wechseln. Durch Auswählen früherer Versionen des Unternehmensportals können Sie sehen, welche Endbenutzer die Geräte haben, bei denen das Unternehmensportal noch nicht aktualisiert wurde.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Bitten Sie Endbenutzer von Android-Geräten, die noch nicht aktualisiert haben, das Unternehmensportal über Google Play zu aktualisieren. Benachrichtigen Sie Ihren Helpdesk, wenn ein Benutzer die automatische Aktualisierung der Unternehmensportal-App nicht eingehalten hat. Über den Link in „Zusätzliche Informationen“ finden Sie weitere Informationen zur FCM-Plattform und dem Wechsel von Google.

#### <a name="additional-information"></a>Zusätzliche Informationen
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Neue Vollbild-Benutzeroberfläche für Intune <!--4593669-->
Wir führen im Azure-Portal neue Benutzeroberflächen zum Erstellen und Bearbeiten für Intune ein. Diese neuen Benutzeroberflächen vereinfachen die vorhandenen Workflows, indem die Funktionen im Stil eines Assistenten auf einem einzigen Blatt zusammengefasst werden. Dank dieses Updates müssen Sie nicht mehr auf mehreren Blättern arbeiten oder verschiedene Detailinformationen anzeigen, um Erstellungs- oder Bearbeitungsvorgänge durchzuführen. Die Workflows zum Erstellen werden ebenfalls aktualisiert und werden Zuweisungen enthalten (mit Ausnahme von App-Zuweisungen).

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Die Vollbild-Benutzeroberfläche für Intune wird in den kommenden Monaten sowohl in „portal.azure.com“ als auch in „devicemanagement.microsoft.com“ eingeführt. Dieses Update der Benutzeroberfläche wirkt sich nicht auf die Funktionsweise Ihrer vorhandenen Richtlinien und Profile aus, Sie werden aber feststellen, dass der Workflow leicht verändert wurde. Beim Erstellen neuer Richtlinien können Sie beispielsweise einige Zuweisungen bereits im Rahmen dieses Flows statt erst nach dem Erstellen der Richtlinie festlegen. Screenshots der neuen Benutzeroberfläche in der Konsole finden Sie im Blogbeitrag unter „Weitere Informationen“.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie müssen keine Maßnahmen ergreifen, sollten aber eventuell Ihre Leitfäden für IT-Experten aktualisieren. Wir werden unsere Dokumentation aktualisieren, wenn diese Benutzeroberfläche auf den verschiedenen Blättern für Intune im Azure-Portal eingeführt wird.

#### <a name="additional-information"></a>Zusätzliche Informationen 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Stellen Sie sich auf eine Änderung ein: Neue Einstellungen für Windows Updates in Intune <!-- 4464404 -->
Ab der im August veröffentlichten Version von Intune (Version 1908) sind neue Stichtagseinstellungen verfügbar, die Sie anstelle der Einstellungen für „Benutzer (erzwungenen) Neustart ermöglichen“ konfigurieren können. Es ist geplant, die Einstellungen für erzwungenen Neustart in der Benutzeroberfläche der Version 1909 bzw. des Septemberupdates zu deaktivieren und sie dann bis Ende des Oktober vollständig aus der Konsole zu entfernen.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Sie Windows 10-Geräte in Ihrer Umgebung verwalten:

- Im Augustupdate von Intune (Version 1908) werden in der Konsole zusätzlich zu den alten Einstellungen für erzwungenen Neustart neue Stichtagseinstellungen angezeigt.
- Wenn sowohl die alten als auch die neuen Einstellungen konfiguriert werden, überschreiben die Stichtagseinstellungen die Werte für erzwungenen Neustart.
- Im Update 1910 wird in der Konsole die Option „Benutzer (erzwungenen) Neustart ermöglichen“ durch die Stichtagseinstellungen ersetzt.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Beginnen Sie in Version 1908 mit der Verwendung der Stichtagseinstellungen, indem Sie sie mit den gewünschten Werten konfigurieren. Nachdem Sie dies eingerichtet haben, können Sie die Einstellung für erzwungenen Neustart auf „Nicht konfiguriert“ festlegen, da diese Einstellungen im Oktober aus der Konsole entfernt werden.

Aktualisieren Sie ggf. Ihre Dokumentation und möglicherweise vorhandene Automatisierungsskripts.

Wir halten Sie auf dem Laufenden und veröffentlichen im Nachrichtencenter eine Erinnerung, bevor die Einstellungen für erzwungenen Neustart entfernt werden.

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Stellen Sie sich auf eine Änderung ein: Intune App SDK und App-Schutzrichtlinien für Android unterstützen Android 5.0 und höher im Oktober. <!--4911065 -->
Intune wird Android 5.x (Lollipop) und höher im Oktober unterstützen. Aktualisieren Sie alle umschließenden Apps mit dem neuesten Intune App SDK, und aktualisieren Sie Ihre Geräte.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Sie weder das SDK noch die APP für Android verwenden noch deren Verwendung planen, wirkt sich diese Änderung nicht auf Sie aus. Wenn Sie das Intune App SDK verwenden, stellen Sie sicher, dass Sie auf die neueste Version aktualisieren, und aktualisieren Sie Ihre Geräte auch auf Android 5.x und höher. Wenn Sie nicht aktualisieren, erhalten Apps keine Updates, und die Qualität ihrer Benutzung wird mit der Zeit abnehmen.

Unten finden Sie eine Liste der gängigen in Intune registrierten Geräte, auf denen Android Version 4.x ausgeführt wird. Wenn Sie über eines dieser Geräte verfügen, führen Sie die entsprechenden Schritte aus, um sicherzustellen, dass dieses Gerät Android-Version 5.0 oder höher unterstützt, oder dass es durch ein Gerät ersetzt wird, das Android-Version 5.0 oder höher unterstützt. Diese Liste enthält nicht alle Geräte, die möglicherweise ausgewertet werden müssen:

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Intune – Planen für Änderungen: Support für Windows 7 endet bald <!-- 3042987 -->
Wie wir im September 2018 in MC148476 sowie erneut im März 2019 in MC176794 angekündigt haben, endet der Support für Windows 7 am 14. Januar 2020. Zu diesem Zeitpunkt stellt Intune die Unterstützung für Geräte unter Windows 7 ein, damit wir unsere Investitionen auf die Unterstützung neuerer Technologien und die Bereitstellung herausragender neuer Endbenutzerfunktionen fokussieren können. Nach diesem Datum sind technische Unterstützung und automatische Updates für den Schutz von Windows 7-PCs über Intune nicht mehr verfügbar. Microsoft empfiehlt dringend, vor Januar 2020 zu Windows 10 zu wechseln, um eine Situation zu vermeiden, in der Sie Service- oder Supportleistungen benötigen, die nicht mehr zur Verfügung stehen. [Hier](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) erfahren Sie mehr über den Windows-Supportlebenszyklus.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Sie erhalten diese Nachricht, weil Sie zurzeit Windows 7-PCs über den veralteten Intune-PC-Software-Agent verwalten. Da bis zum Ende des erweiterten Windows 7-Supports weniger als ein Jahr Zeit bleibt, empfehlen wir Ihrer Organisation dringend, so bald wie möglich mit dem Upgrade auf Windows 10 zu beginnen. PC-Verwaltungsfunktionen sind direkt in das Windows 10-Betriebssystem integriert, und es ist nicht mehr notwendig, einen Client-Agent wie den Intune-Softwareclient für Windows 7 zu installieren. Seit Windows 8.1 verwendet Microsoft die MDM-Architektur (Mobile Device Management, mobile Geräteverwaltung) zum Bereitstellen, Konfigurieren, Aktualisieren und Verwalten von Windows-PCs. Sobald Sie Intune eingerichtet haben, können Sie die Windows-Registrierung vereinfachen, indem Sie den MDM-Kanal verwenden, um [Windows 10-PCs in Intune zu registrieren](..\windows-enroll.md). Wir empfehlen die Verwendung dieser MDM-Verwaltungslösung ohne Agent zum Verwalten Ihrer Windows 10-PCs.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wir empfehlen Ihrer Organisation, so schnell wie möglich folgenden Aktionsplan zu berücksichtigen:

- Sie sollten das Upgrade aller Windows 7-Geräte auf Windows 10 vor dem 14. Januar 2020 planen und durchführen.
- Erkunden Sie die [Unterstützung für die Windows 10-Bereitstellung](https://docs.microsoft.com/windows/deployment/), um mehr über das Upgrade der vorhandenen Geräte von Windows 7 auf Windows 10 zu erfahren.
- Informieren Sie sich über das Angebot [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1), das über Fast Track zur Verfügung steht und beim Microsoft-Versprechen der Anwendungskompatibilität hilft.
- Übertragen Sie vorhandene ältere Geräte, die über den Intune-Softwareclient verwaltet werden, in die von Microsoft empfohlene Lösung, um Windows 10 über MDM zu verwalten. Registrieren Sie alle neuen Windows 10-PCs über MDM für Intune im Azure-Portal.
- Weitere Informationen finden Sie in [diesem Blogbeitrag](https://aka.ms/Windows7_Intune).
