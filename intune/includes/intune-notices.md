---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: d907c5256469e86410c9916d117d3e322d43cfc3
ms.sourcegitcommit: 2614d1b08b8a78cd792aebd2ca9848f391df8550
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67812567"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können. 

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

### <a name="plan-for-change-intune-moving-to-support-ios-11-and-higher-in-september----4665342--"></a>Stellen Sie sich auf eine Änderung ein: Intune wird iOS 11 und höher im September unterstützen <!-- 4665342-->
Im September erwarten wir, dass iOS 13 von Apple veröffentlicht wird. Kurz nach Veröffentlichung der Version iOS 13 wird die Unterstützung von iOS 11 und höher für die Registrierung bei Intune, das Unternehmensportal und den verwalteten Browser eingeführt.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Vorausgesetzt, dass mobile Office 365-Apps unter iOS 11.0 und höher unterstützt werden, sind Sie möglicherweise nicht betroffen, weil Sie Ihr Betriebssystem oder Ihre Geräte wahrscheinlich bereits aktualisiert haben. Wenn Sie aber eines der unten aufgelisteten Geräte haben oder beschließen, eines der unten aufgeführten Geräte zu registrieren, müssen Sie wissen, dass diese Geräte ein Betriebssystem von maximal iOS 10 unterstützen. Diese Geräte müssen auf ein Gerät aktualisiert werden, das iOS 11 oder höher unterstützt:

- iPhone 5
- iPhone 5c
- iPad (4. Generation)

Ab Juli erhalten mit MDM registrierte Geräte mit iOS 10 und dem Unternehmensportal eine Aufforderung, ihr Betriebssystem oder Gerät upzugraden. Wenn Sie Anwendungsschutzrichtlinien (Application Protection Policies, APP) verwenden, können Sie auch die Zugriffseinstellung „iOS-Mindestbetriebssystem anfordern (nur Warnung)“ festlegen.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Überprüfen Sie Ihre Intune-Berichte, um zu sehen, welche Geräte oder Benutzer möglicherweise betroffen sind. Wechseln Sie zu **Geräte** > **Alle Geräte**, und filtern Sie nach „Betriebssystem“. Sie können weitere Spalten hinzufügen, um besser bestimmen zu können, welche Benutzer in Ihrer Organisation Geräte mit iOS 10 verwenden. Fordern Sie Ihre Endbenutzer dazu auf, Ihre Geräte vor September auf eine unterstützte Betriebssystemversion upzugraden.

### <a name="plan-for-change-support-for-version-811-and-higher-of-intune-app-sdk-for-ios----3586942--"></a>Stellen Sie sich auf eine Änderung ein: Unterstützung für Version 8.1.1 und höher des Intune App SDK für iOS <!-- 3586942-->
Ab September 2019 wird Intune iOS-Apps mit Intune App SDK 8.1.1 und höher unterstützen. Apps, die mit SDK-Versionen vor 8.1.1. erstellt wurden, werden nicht mehr unterstützt. Diese Änderung wird mit der Apple-Veröffentlichung von iOS 13 wirksam, die für kommenden September erwartet wird und auch in MC181399 angekündigt wurde.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Mit der Integration von Intune App SDK oder App Wrapping können Sie Unternehmensdaten vor nicht genehmigten Anwendungen und Benutzern über Datenverschlüsselung schützen. Das Intune App SDK für iOS wird standardmäßig 256-Bit-Verschlüsselungsschlüssel verwenden, wenn die Verschlüsselung durch Intune App-Schutzrichtlinien (App Protection Policies, APP) aktiviert wurde. Nach dieser Änderung können iOS-Apps unter SDK-Versionen vor 8.1.1, die 128-Bit-Verschlüsselungsschlüssel verwenden, Daten mit Anwendungen nicht mehr freigeben, die in SDK 8.1.1 integriert sind oder die 256-Bit-Schlüssel verwenden. Alle iOS-Apps müssen eine SDK-Version 8.1.1. oder höher haben, um die geschützte Datenfreigabe zuzulassen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Überprüfen Sie Ihre Microsoft-Apps, Apps von Drittanbietern und branchenspezifischen Apps. Sie sollten sicherstellen, dass alle Ihre mit Intune APP geschützten Anwendungen die SDK-Version 8.1.1 oder höher verwenden.

- Für branchenspezifische Apps: Möglicherweise müssen Sie Ihre in SDK-Version 8.1.1 oder höher integrierten Apps erneut veröffentlichen. Wir empfehlen die neueste SDK-Version. Informationen zum Vorbereiten Ihrer branchenspezifischen Apps auf App-Schutzrichtlinien finden Sie unter [Vorbereiten von branchenspezifischen Apps für App-Schutzrichtlinien](../apps-prepare-mobile-application-management.md).
- Für Microsoft-Apps/Apps von Drittanbietern: Sorgen Sie dafür, dass Sie die neueste Version dieser Apps für Ihre Benutzer bereitstellen.

Sie sollten auch ggf. Ihre Dokumentation oder Ihren Entwicklerleitfaden aktualisieren, damit darin diese Änderung zur Unterstützung für das SDK enthalten ist.

#### <a name="additional-information"></a>Zusätzliche Informationen
https://docs.microsoft.com/intune/apps-prepare-mobile-application-management

### <a name="plan-for-change-new-windows-updates-settings-in-intune----4464404---"></a>Stellen Sie sich auf eine Änderung ein: Neue Einstellungen für Windows Updates in Intune <!-- 4464404 -->
Ab der im August veröffentlichten Version von Intune (Version 1908) sind neue Stichtagseinstellungen verfügbar, die Sie anstelle der Einstellungen für „Benutzer (erzwungenen) Neustart ermöglichen“ konfigurieren können. Es ist geplant, die Einstellungen für erzwungenen Neustart in der Benutzeroberfläche der Version 1909 bzw. des Septemberupdates zu deaktivieren und sie dann bis Ende des Oktober vollständig aus der Konsole zu entfernen. 

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Wenn Sie Windows 10-Geräte in Ihrer Umgebung verwalten: 
- Im Augustupdate von Intune (Version 1908) werden in der Konsole zusätzlich zu den alten Einstellungen für erzwungenen Neustart neue Stichtagseinstellungen angezeigt.
- Wenn sowohl die alten als auch die neuen Einstellungen konfiguriert werden, überschreiben die Stichtagseinstellungen die Werte für erzwungenen Neustart.
- Im Update 1910 wird in der Konsole die Option „Benutzer (erzwungenen) Neustart ermöglichen“ durch die Stichtagseinstellungen ersetzt.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Beginnen Sie in Version 1908 mit der Verwendung der Stichtagseinstellungen, indem Sie sie mit den gewünschten Werten konfigurieren. Nachdem Sie dies eingerichtet haben, können Sie die Einstellung für erzwungenen Neustart auf „Nicht konfiguriert“ festlegen, da sie im Oktober aus der Konsole entfernt wird.

Aktualisieren Sie ggf. Ihre Dokumentation und möglicherweise vorhandene Automatisierungsskripts. 

Wir halten Sie auf dem Laufenden und veröffentlichen im Nachrichtencenter eine Erinnerung, bevor die Einstellungen für erzwungenen Neustart entfernt werden.