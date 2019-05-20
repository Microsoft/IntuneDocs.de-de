---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732604"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Änderung beim Registrierungsworkflow im Zusammenhang mit Intune-Unternehmensportal auf unternehmenseigenen iOS-Geräten, die sich mithilfe des Setup-Assistenten authentifizieren <!-- 1927359 -->
Es wird eine Änderung beim Workflow für die Registrierung von iOS-Geräten mit einer der Apple-Methoden für die Registrierung unternehmenseigener Geräte – Apple Configurator, Apple Business Manager, Apple School Manager oder das Apple-Programm zur Geräteregistrierung – geben, wenn der Setup-Assistent zur Authentifizierung verwendet wird. Diese Änderung gilt nur für Geräte, die mit Benutzeraffinität registriert wurden.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn diese Änderung eingeführt wird, werden Registrierungsprofile in Intune im Azure-Portal aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren und ob sie die Unternehmensportal-App erhalten sollen. Es wird einen verbesserten Workflow zum Registrieren von iOS-Geräten mit den oben aufgeführten Methoden geben. 

- Wenn Sie neue Geräte registrieren und sich mithilfe des Setup-Assistenten authentifizieren, können Sie auswählen, ob die Unternehmensportal-App automatisch bereitgestellt werden soll oder nicht. Endbenutzern werden die Bildschirme „Gerät identifizieren“ und „Gerät bestätigen“ im Registrierungsflow nicht mehr angezeigt.  
- Auf Geräten, die über den Setup-Assistenten bereits mit einer der Apple-Methoden für die Registrierung unternehmenseigener Geräte registriert wurden, müssen Sie entsprechende Maßnahmen ergreifen, wenn Sie den bedingten Zugriff aktivieren möchten. Sie müssen [eine App-Konfigurationsrichtlinie mit einem bestimmten XML konfigurieren](https://aka.ms/enrollment_setup_assistant), um das Unternehmensportal per Push auf diese Geräte zu übertragen.  Wenn Sie wählen, dass das Unternehmensportal auf diese Weise übertragen werden soll, werden Endbenutzern die Bildschirme „Gerät identifizieren“ und „Gerät bestätigen“ im Registrierungsflow nicht mehr angezeigt. 
- Nach Einführung dieser Änderung gilt Folgendes: Wenn Sie das Unternehmensportal mit dem oben genannten App-Konfigurationsprofil nicht bereitgestellt haben und wenn Endbenutzer die Unternehmensportal-App aus dem App Store herunterladen, können sie sich zwar anmelden, erhalten aber eine Fehlermeldung. Die Endbenutzer können die App nicht mehr für bedingten Zugriff verwenden. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Wenn Sie die Verwendung des geänderten Workflows planen, sollten Sie Ihre Anleitungen für Endbenutzer aktualisieren und darin auf Folgendes hinweisen:

- Für Endbenutzer werden die beiden oben genannten Bildschirme im Registrierungsflow nicht mehr angezeigt. 
- Sie müssen sich beim Unternehmensportal anmelden, wenn es automatisch bereitgestellt wird, und können es nicht aus dem App Store herunterladen. 

In Vorbereitung auf diese Änderung können Sie bei Bedarf jetzt wählen, dass eine Konfigurationsrichtlinie für die App erstellt werden soll. Wenn dieser neue Workflow eingeführt wird, werden Ihnen in der Konsole aktualisierte Registrierungsprofile angezeigt. Außerdem werden wir Sie über das Nachrichtencenter im Hinblick auf diese Einführung informieren. Dann müssen Sie die entsprechenden Maßnahmen ergreifen, damit sich Ihre Endbenutzer über das Programm zur Geräteregistrierung registrieren können, indem Sie sich mithilfe des Setup-Assistenten authentifizieren. Sie können auch das Unternehmensportal für bedingten Zugriff nutzen.

#### <a name="additional-information"></a>Weitere Informationen 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aktualisieren Ihrer Android-Unternehmensportal-App auf die neueste Version <!--4536963-->
Intune veröffentlicht regelmäßig Versionsupdates für die Android-Unternehmensportal-App. Im November 2018 haben wir ein Unternehmensportal-Update veröffentlicht, das einen Back-End-Switch zur Vorbereitung auf den Google-Wechsel von der vorhandenen Benachrichtigungsplattform auf sein Firebase Cloud Messaging (FCM) enthielt. Wenn Google seine vorhandene Benachrichtigungsplattform außer Betrieb nimmt und zu FCM wechselt, müssen Endbenutzer ihre Unternehmensportal-App auf mindestens die Version von November 2018 aktualisiert haben, damit sie mit dem Google Play Store weiterhin kommunizieren können.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Unsere Telemetrie gibt an, dass Sie Geräte mit einer Unternehmensportal-Version vor 5.0.4269.0 haben. Wenn diese Version oder höher der Unternehmensportal-App nicht installiert wird, funktionieren von IT-Profis initiierte Geräteaktionen wie Wischen, Kennwort zurücksetzen, verfügbare und erforderliche App-Installationen und Zertifikatregistrierung möglicherweise nicht wie erwartet. Wenn Ihre Geräte in Intune für die mobile Geräteverwaltung registriert wurden, können Sie die Versionen und Benutzer des Unternehmensportals anzeigen, indem Sie zu „Client-Apps“ – „Ermittelte Apps“ wechseln. Durch Auswählen früherer Versionen des Unternehmensportals können Sie sehen, welche Endbenutzer die Geräte haben, bei denen das Unternehmensportal noch nicht aktualisiert wurde.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Bitten Sie Endbenutzer von Android-Geräten, die noch nicht aktualisiert haben, das Unternehmensportal über Google Play zu aktualisieren. Benachrichtigen Sie Ihren Helpdesk, wenn ein Benutzer die automatische Aktualisierung der Unternehmensportal-App nicht eingehalten hat. Über den Link in „Zusätzliche Informationen“ finden Sie weitere Informationen zur FCM-Plattform und dem Wechsel von Google.

#### <a name="additional-information"></a>Weitere Informationen
https://firebase.google.com/docs/cloud-messaging/