---
title: Includedatei
description: Includedatei
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454127"
---
Diese Hinweise enthalten wichtige Informationen, die Ihnen bei der Vorbereitung auf künftige Änderungen und Features im Zusammenhang mit Intune helfen können. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aktualisieren Ihrer Android-Unternehmensportal-App auf die neueste Version <!--4536963-->
Intune veröffentlicht regelmäßig Versionsupdates für die Android-Unternehmensportal-App. Im November 2018 haben wir ein Unternehmensportal-Update veröffentlicht, das einen Back-End-Switch zur Vorbereitung auf den Google-Wechsel von der vorhandenen Benachrichtigungsplattform auf sein Firebase Cloud Messaging (FCM) enthielt. Wenn Google seine vorhandene Benachrichtigungsplattform außer Betrieb nimmt und zu FCM wechselt, müssen Endbenutzer ihre Unternehmensportal-App auf mindestens die Version von November 2018 aktualisiert haben, damit sie mit dem Google Play Store weiterhin kommunizieren können.

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Unsere Telemetrie gibt an, dass Sie Geräte mit einer Unternehmensportal-Version vor 5.0.4269.0 haben. Wenn diese Version oder höher der Unternehmensportal-App nicht installiert wird, funktionieren von IT-Profis initiierte Geräteaktionen wie Wischen, Kennwort zurücksetzen, verfügbare und erforderliche App-Installationen und Zertifikatregistrierung möglicherweise nicht wie erwartet. Wenn Ihre Geräte in Intune für die mobile Geräteverwaltung registriert wurden, können Sie die Versionen und Benutzer des Unternehmensportals anzeigen, indem Sie zu „Client-Apps“ – „Ermittelte Apps“ wechseln. Durch Auswählen früherer Versionen des Unternehmensportals können Sie sehen, welche Endbenutzer die Geräte haben, bei denen das Unternehmensportal noch nicht aktualisiert wurde.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Wie sollte ich mich für die Änderung vorbereiten?
Bitten Sie Endbenutzer von Android-Geräten, die noch nicht aktualisiert haben, das Unternehmensportal über Google Play zu aktualisieren. Benachrichtigen Sie Ihren Helpdesk, wenn ein Benutzer die automatische Aktualisierung der Unternehmensportal-App nicht eingehalten hat. Über den Link in „Zusätzliche Informationen“ finden Sie weitere Informationen zur FCM-Plattform und dem Wechsel von Google.

#### <a name="additional-information"></a>Weitere Informationen
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Neue Vollbild-Benutzeroberfläche für Intune <!--4593669-->
Wir führen im Azure-Portal neue Benutzeroberflächen zum Erstellen und Bearbeiten für Intune ein. Diese neuen Benutzeroberflächen vereinfachen die vorhandenen Workflows, indem die Funktionen im Stil eines Assistenten auf einem einzigen Blatt zusammengefasst werden. Dank dieses Updates müssen Sie nicht mehr auf mehreren Blättern arbeiten oder verschiedene Detailinformationen anzeigen, um Erstellungs- oder Bearbeitungsvorgänge durchzuführen. Die Workflows zum Erstellen werden ebenfalls aktualisiert und werden Zuweisungen enthalten (mit Ausnahme von App-Zuweisungen).

#### <a name="how-does-this-affect-me"></a>Inwiefern betrifft das mich?
Die Vollbild-Benutzeroberfläche für Intune wird in den kommenden Monaten sowohl in „portal.azure.com“ als auch in „devicemanagement.microsoft.com“ eingeführt. Dieses Update der Benutzeroberfläche wirkt sich nicht auf die Funktionsweise Ihrer vorhandenen Richtlinien und Profile aus, Sie werden aber feststellen, dass der Workflow leicht verändert wurde. Beim Erstellen neuer Richtlinien können Sie beispielsweise einige Zuweisungen bereits im Rahmen dieses Flows statt erst nach dem Erstellen der Richtlinie festlegen. Screenshots der neuen Benutzeroberfläche in der Konsole finden Sie im Blogbeitrag unter „Weitere Informationen“.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Wie kann ich mich auf die Änderung vorbereiten?
Sie müssen keine Maßnahmen ergreifen, sollten aber eventuell Ihre Leitfäden für IT-Experten aktualisieren. Wir werden unsere Dokumentation aktualisieren, wenn diese Benutzeroberfläche auf den verschiedenen Blättern für Intune im Azure-Portal eingeführt wird.

#### <a name="additional-information"></a>Weitere Informationen 
https://aka.ms/intune_fullscreen
