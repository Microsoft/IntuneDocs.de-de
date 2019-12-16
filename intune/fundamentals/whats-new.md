---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77cf4745262346ec2f8bfb5d4d7e67e1ee5c5e07
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000379"
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Hier finden Sie auch [wichtige Hinweise](#notices), [frühere Releases](whats-new-archive.md) und Informationen zur [Veröffentlichung von Intune-Dienstupdates](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728).

> [!Note]
> Bei jedem [monatlichen Update](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kann das Rollout bis zu drei Tage dauern und erfolgt in dieser Reihenfolge:
>
> - 1\. Tag: Asien-Pazifik (APAC)
> - 2\. Tag: Europa, Naher Osten und Afrika (EMEA)
> - 3\. Tag: Nordamerika
>
> Einige Features werden im Laufe mehrerer Wochen bereitgestellt und sind in der ersten Woche möglicherweise nicht für alle Kunden verfügbar.
>
> Auf der Seite [Features in der Entwicklung](in-development.md) finden Sie eine Liste der neuen Features in einem Release.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-december-9-2019"></a>Woche des 9. Dezember 2019

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrieren zu Microsoft Edge für das verwaltete Durchsuchen<!-- 5173762 -->

Im Hinblick auf die Einstellung von Intune Managed Browser wurden Änderungen an den App-Schutzrichtlinien vorgenommen, um die erforderlichen Schritte zu vereinfachen, die für die Umstellung Ihrer Benutzer auf Edge nötig sind. Die Optionen für die App-Schutzrichtlinieneinstellung **Übertragung von Webinhalt in andere Apps einschränken** wurden aktualisiert, sodass die folgenden Optionen verfügbar sind:

- Jede App
- Intune Managed Browser
- Microsoft Edge
- Nicht verwalteter Browser 

Wenn Sie **Microsoft Edge** auswählen, wird Ihren Endbenutzern Messaging für bedingten Zugriff angezeigt, das sie darüber benachrichtigt, dass Microsoft Edge für das verwaltete Durchsuchen erforderlich ist. Sie werden dazu aufgefordert, Microsoft Edge herunterzuladen und sich mit ihren AAD-Konten anzumelden, wenn sie dies noch nicht getan haben.  Dies entspricht einer Anwendung der App-Konfigurationseinstellung `com.microsoft.intune.useEdge`, die auf **True** festgelegt ist, auf Ihre MAM-fähigen Apps. In den vorhandenen App-Schutzrichtlinien, die die Einstellung **Mit Richtlinien verwaltete Browser** verwendet haben, ist jetzt **Intune Managed Browser** ausgewählt. Dabei ist keine Verhaltensänderung erkennbar. Das bedeutet, dass Ihren Benutzern Messaging zur Verwendung von Microsoft Edge angezeigt wird, wenn Sie die App-Konfigurationseinstellung **useEdge** auf **True** festgelegt haben. Wir empfehlen allen Kunden, die verwalteten Browserszenarios nutzen, ihre App-Schutzrichtlinien mit der Einstellung **Übertragung von Webinhalt in andere Apps einschränken** zu aktualisieren, um sicherzustellen, dass Benutzer die richtigen Anleitungen für den Übergang zu Microsoft Edge sehen, unabhängig davon, welche App sie verwenden. 

<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Woche des 2. Dezember 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Neue Lizenzierung der Co-Verwaltung von Microsoft Endpoint Configuration Manager<!--5027281-->
Es ist jetzt eine neue Lizenz verfügbar, mit der Configuration Manager-Kunden mit Software Assurance eine Co-Verwaltung von Intune für Windows 10-PCs erhalten können, ohne eine zusätzliche Intune-Lizenz für die Co-Verwaltung erwerben zu müssen. Kunden müssen ihren Endbenutzern nicht mehr einzelne Intune-/EMS-Lizenzen für die Co-Verwaltung von Windows 10 zuweisen.
- Geräte, die von Configuration Manager verwaltet und bei der Co-Verwaltung registriert werden, verfügen über fast die gleichen Rechte wie eigenständige MDM-verwaltete Intune-PCs. Nach dem Zurücksetzen können sie jedoch nicht mithilfe von Autopilot nochmals bereitgestellt werden.
- Windows 10-Geräte, die anderweitig bei Intune registriert sind, benötigen vollständige Intune-Lizenzen.
- Geräte auf anderen Plattformen benötigen weiterhin vollständige Intune-Lizenzen.

Weitere Informationen finden Sie unter [Lizenzierungsbestimmungen](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Woche vom 18. November 2019 (1911 Dienstrelease)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="smime-support-with-microsoft-outlook-for-ios---2669398-idready---"></a>S/MIME-Unterstützung mit Microsoft Outlook für iOS<!-- 2669398 idready -->

   > [!NOTE]
   > Diese Funktion hat sich verzögert, wird aber bald veröffentlicht.

Intune unterstützt die Bereitstellung von S/MIME-Signatur- und Verschlüsselungszertifikaten, die mit Outlook für iOS auf iOS-Geräten verwendet werden können. Weitere Informationen finden Sie unter [Konfigurieren von S/MIME für Outlook für iOS](~/apps/app-configuration-policies-outlook-smime.md).

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Benutzeroberflächenupdate beim selektiven Löschen von App-Daten<!-- 4102028 -->
Die Benutzeroberfläche zum selektiven Löschen von App-Daten in Intune wurde aktualisiert. Die Änderungen der Benutzeroberfläche umfassen:
- eine vereinfachte Funktion mithilfe eines Formats im Assistentenstil in einem einzigen Bereich
- Ein Update für den Erstellungsflow zum Einschließen von Zuweisungen.
- Eine zusammengefasste Seite aller festgelegten Einstellungen beim Anzeigen der Eigenschaften, bevor eine neue Richtlinie erstellt wird oder bei der Bearbeitung einer Eigenschaft. Beim Bearbeiten von Eigenschaften zeigt die Zusammenfassung nur eine Liste der Elemente aus der Kategorie der Eigenschaften an, die bearbeitet werden.

Weitere Informationen finden Sie unter [Zurücksetzen nur von Unternehmensdaten in einer in Intune verwalteten App](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Unterstützung von Tastaturen von Drittanbietern für iOS und iPadOS<!-- 4922950 -->
Im März 2019 haben wir angekündigt, dass die Unterstützung für die App-Schutzrichtlinie „Tastaturen von Drittanbietern“ für iOS aufgehoben wurde. Das Feature kehrt sowohl mit iOS- als auch mit iPadOS-Unterstützung zu Intune zurück. Wählen Sie die Registerkarte **Datenschutz** einer neuen oder bestehenden iOS/iPadOS-App-Schutzrichtlinie aus, um diese Einstellung zu aktivieren, und suchen Sie die Einstellung **Tastaturen von Drittanbietern** unter **Datenübertragung**.

Das Verhalten dieser Richtlinieneinstellung unterscheidet sich leicht von der vorherigen Implementierung. In Apps mit mehreren Identitäten mit SDK Version 12.0.16 und höher, die von App-Schutzrichtlinien mit dieser Einstellung auf **Blockieren** konfiguriert sind, können sich Endbenutzer sowohl in ihrer Organisation als auch in ihren persönlichen Konten nicht für Tastaturen von Drittanbietern entscheiden. Apps, die SDK-Versionen 12.0.12 und früher verwenden, zeigen weiterhin das Verhalten, das in unserem Blogbeitrag mit dem Titel [Bekanntes Problem: Tastaturen von Drittanbietern werden in iOS für persönliche Konten nicht blockiert](https://aka.ms/3rdparty_iOS_Intune) dokumentiert ist.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Erzwingen der Jamf-Verwaltung für macOS-Benutzergruppen<!-- 4061739  --> 
Sie können festlegen, dass für bestimmte Benutzergruppen [macOS-Geräte von Jamf verwaltet werden](../protect/conditional-access-integrate-jamf.md). Auf diese Weise können Sie die Integration der Jamf-Konformität auf eine Teilmenge von macOS-Geräten anwenden, während andere Geräte von Intune verwaltet werden. Wenn Sie bereits die Jamf-Integration verwenden, werden standardmäßig alle Benutzer für die Integration festgelegt.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Neue Exchange ActiveSync-Einstellungen beim Erstellen eines E-Mail-Gerätekonfigurationsprofils auf iOS-Geräten<!-- 4892824   --> 
Sie können auf iOS- und iPadOS-Geräten die E-Mail-Konnektivität in einem Gerätekonfigurationsprofil konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS** für Plattform > **E-Mail** für den Profiltyp). 

Es sind neue Exchange ActiveSync-Einstellungen verfügbar, einschließlich:
- **Zu synchronisierende Exchange-Daten:** Wählen Sie die zu synchronisierenden (oder zu blockierenden) Exchange-Dienste für Kalender, Kontakte, Erinnerungen und E-Mail aus.
- **Benutzern das Ändern der Synchronisierungseinstellungen erlauben:** Erlauben Sie Benutzern, die Synchronisierungseinstellungen für diese Dienste auf ihren Geräten zu ändern (oder blockieren Sie sie).  

Weitere Informationen zu diesen Einstellungen finden Sie unter [E-Mail-Profileinstellungen für iOS-Geräte in Intune](../configuration/email-settings-ios.md). 

Gilt für:
- iOS 13.0 und neuer
- iOS 13.0 und höher

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Verhindern, dass Benutzer persönliche Google-Konten zu vollständig verwalteten und dedizierten Geräten von Android Enterprise hinzufügen<!-- 5353228   -->
Auf vollständig verwalteten und dedizierten Geräten von Android Enterprise gibt es eine neue Einstellung, die Benutzer daran hindert, persönliche Google-Konten zu erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Nur Gerätebesitzer > Geräteeinschränkungen** für Profiltyp > **Benutzer- und Konteneinstellungen** > **Persönliche Google-Konten**).

Sie finden die konfigurierbaren Einstellungen unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Vollständig verwaltete Android Enterprise-Geräte
- Dedizierte Android Enterprise-Geräte

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Entfernung der serverseitigen Protokollierung für die Einstellung der Siri-Befehle im iOS/iPadOS-Profil zur Geräteeinschränkung <!-- 5468501   -->
Auf iOS- und iPadOS-Geräten wird die Einstellung **Serverseitige Protokollierung für Siri-Befehle** aus der Microsoft Endpoint Manager-Verwaltungskonsole entfernt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS** für Plattform > **Geräteeinschränkungen** für Profiltyp > **integrierte Apps**). 

Diese Einstellung hat keinen Einfluss auf die Geräte. Öffnen Sie das Profil, nehmen Sie alle Änderungen vor, und speichern Sie das Profil, um die Einstellung aus bestehenden Profilen zu entfernen. Das Profil wird aktualisiert, und die Einstellung wird von den Geräten gelöscht.

Sie finden alle konfigurierbaren Einstellungen unter [iOS- und iPadOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:
- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10-Featureupdates (öffentliche Vorschau)<!-- 2384877 -->
Sie können [Windows 10-Featureupdates](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) nun auf Windows 10-Geräten bereitstellen. Windows 10-Featureupdates stellen eine neue Softwareupdaterichtlinie dar, die die Version von Windows 10 festgelegt, die von Geräten installiert und beibehalten werden soll Sie können diesen neuen Richtlinientyp zusammen mit Ihren vorhandenen Windows 10-Updateringen verwenden.

Geräte, die Windows 10-Featureupdaterichtlinien erhalten, installieren die angegebene Windows-Version und verbleiben anschließend bei dieser Version, bis die Richtlinie geändert oder entfernt wird. Geräte, auf denen eine spätere Version von Windows ausgeführt wird, verbleiben bei ihrer aktuellen Version. Geräte, auf denen eine bestimmte Version von Windows eingerichtet ist, können noch immer Qualitäts- und Sicherheitsupdates für diese Version über die Windows 10-Updateringe installieren.

Dieser neue Richtlinientyp wird diese Woche für Mandanten eingeführt. Wenn diese Richtlinie noch nicht für Ihren Mandanten verfügbar ist, wird sie in Kürze verfügbar sein.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Hinzufügen und Ändern von Schlüsselinformationen in PLIST-Dateien für macOS-Anwendungen<!-- 4736278 -->
Auf macOS-Geräten können Sie nun ein Gerätekonfigurationsprofil erstellen, das eine Datei mit der Eigenschaftenliste (.plist) hochlädt, die einer App oder dem Gerät zugeordnet ist (**Geräte** > **Konfigurationsprofile** > **Profil erstellen** > **macOS** für Plattform > **Einstellungsdatei** für Profiltyp).

Nur einige Apps unterstützen verwaltete Einstellungen, und diese Apps erlauben es Ihnen möglicherweise nicht, alle Einstellungen zu verwalten. Stellen Sie sicher, dass Sie eine Datei mit Eigenschaftenliste hochladen, die die Gerätekanaleinstellungen und nicht die Benutzerkanaleinstellungen konfiguriert.

Weitere Informationen zu diesem Feature finden Sie unter [Hinzufügen einer Datei mit Eigenschaftenliste zu macOS-Geräten mit Microsoft Intune](../configuration/preference-file-settings-macos.md).

Gilt für:
- macOS-Geräte mit Version 10.7 und höher

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Bearbeiten des Werts des Gerätenamens für Autopilot-Geräte<!-- 2640074 -->
Sie können den Wert für den Gerätenamen für in Azure AD eingebundene Autopilot-Geräte bearbeiten.  Weitere Informationen finden Sie unter [Bearbeiten von Attributen für Autopilot-Geräte](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Bearbeiten des Werts des Gruppentags für Autopilot-Geräte<!-- 4816775   -->
Sie können den Wert des Gruppentags für Autopilot-Geräte bearbeiten. Weitere Informationen finden Sie unter [Bearbeiten von Attributen für Autopilot-Geräte](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="updated-support-experience---5012398---"></a>Aktualisierte Benutzeroberfläche für Support<!-- 5012398 -->

Ab heute wird eine aktualisierte und optimierte konsoleninterne Benutzeroberfläche für [Hilfe und Support für Intune](get-support.md) an die Mandanten verteilt. Wenn diese neue Benutzeroberfläche noch nicht für Sie verfügbar ist, wird sie in Kürze verfügbar sein.

Wir haben die konsoleninterne Suche und das Feedback zu häufigen Problemen sowie den Workflow, den Sie zum Kontaktieren des Supports verwenden, verbessert. Wenn Sie ein Supportproblem öffnen, sehen Sie Echtzeitschätzwerte für den Zeitraum, in dem Sie mit einem Rückruf oder einer E-Mail-Antwort rechnen können, und Premier Support- und Unified Support-Kunden können problemlos einen Schweregrad für ihr Problem festlegen, um schneller Support zu erhalten.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Verbesserte Berichterstellungsfunktionen (öffentliche Vorschauversion) in Intune <!-- 3791418 -->
Intune bietet nun verbesserte Berichtserstellungsfunktionen, einschließlich neuer Berichtstypen, besserer Berichtsorganisation, fokussierterer Ansichten, verbesserter Berichtsfunktionen sowie konsistenterer und aktuellerer Daten. Neue Berichtstypen konzentrieren sich auf Folgendes:
- **Operational** (betriebsbedingt): stellt neue Berichte mit einem negativen Integritätsfokus bereit 
- **Organizational** (organisationsbedingt): stellt eine umfassendere Zusammenfassung des Gesamtzustands bereit
- **Historical** (verlaufsbedingt): stellt Muster und Trends über einen bestimmten Zeitraum bereit
- **Specialist** (spezialisiert): ermöglicht die Verwendung von Rohdaten zur Erstellung Ihrer eigenen benutzerdefinierten Berichte

Die ersten neuen Berichte konzentrieren sich auf die Gerätekonformität. Weitere Informationen finden Sie im Blogbeitrag [Neues Berichtserstellungsframework für Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) und unter [Intune-Berichte](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Duplizieren benutzerdefinierter und integrierter Rollen <!-- 1081938   -->
Sie können jetzt integrierte und benutzerdefinierte Rollen kopieren. Weitere Informationen finden Sie unter [Kopieren einer Rolle](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Neue Berechtigungen für die Rolle „Schuladministrator“ <!-- 5621805  -->  
Zwei neue Berechtigungen (**Profil zuweisen** und **Gerät synchronisieren**) wurden der Rolle „Schuladministrator“ hinzugefügt > **Berechtigungen** > **Registrierungsprogramme**. Die Berechtigung für das Synchronisierungsprofil ermöglicht es Gruppenadministratoren, Windows Autopilot-Geräte zu synchronisieren. Mit der Berechtigung zum Zuweisen von Profilen können sie benutzerinitiierte Apple-Registrierungsprofile löschen. Es gibt ihnen auch die Berechtigung, die Zuweisung von Autopilot-Geräten und Autopilot-Bereitstellungsprofilen zu verwalten. Eine Liste aller Schuladministrator-/Gruppenadministratorrechte finden Sie unter [Zuweisen von Gruppenadministratoren](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Sicherheit

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker-Schlüsselrotation<!-- 2564951  -->
Sie können eine Intune-Geräteaktion verwenden, um [BitLocker-Wiederherstellungsschlüssel](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) für verwaltete Geräte, die mit Windows Version 1909 oder höher ausgeführt werden, remote zu rotieren. Geräte müssen so konfiguriert sein, dass sie die Rotation von Wiederherstellungsschlüssel unterstützen, damit sie für die Rotation von Wiederherstellungsschlüsseln qualifiziert sind.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Updates zur Registrierung für dedizierte Geräte zur Unterstützung der Bereitstellung von SCEP-Gerätezertifikaten <!-- 5198878  -->
Intune unterstützt nun die Bereitstellung von SCEP-Gerätezertifikaten auf dedizierten Android Enterprise-Geräten für den zertifikatbasierten Zugriff auf WLAN-Profile. Die Microsoft Intune-App muss auf dem Gerät vorhanden sein, damit die Bereitstellung funktioniert. Aus diesem Grund wurde die Registrierungsfunktion für dedizierte Android Enterprise-Geräte aktualisiert. Der Registrierungsvorgang ist am Anfang gleich (mit QR, NFC, ohne Benutzereingriff oder Gerätebezeichner), aber jetzt ist ein Schritt dazugekommen, der die Installation der Intune-App durch den Benutzer erfordert. Bestehende Geräte werden jetzt die App automatisch und fortlaufend installieren.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Intune-Überwachungsprotokolle für die Business-to-Business Zusammenarbeit<!--5670211 -->
Die Business-to-Business-Zusammenarbeit (B2B) ermöglicht es Ihnen, die Anwendungen und Dienste Ihres Unternehmens sicher mit Gastbenutzern aus anderen Organisationen zu teilen, während Sie die Kontrolle über Ihre eigenen Unternehmensdaten behalten. Intune unterstützt nun Überwachungsprotokolle für B2B-Gastbenutzer. Wenn Gastbenutzer beispielsweise Änderungen vornehmen, kann Intune diese Daten über Überwachungsprotokolle erfassen. Weitere Informationen hierzu finden Sie unter [Was ist der Gastzugriff in Azure Active Directory-B2B?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Woche vom 11. November 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>Verbesserte macOS-Registrierungsoberfläche im Unternehmensportal <!-- 5074349 WNready -->  
Das Unternehmensportal für die macOS-Registrierung verfügt über einen einfacheren Registrierungsprozess, der sich enger an das Unternehmensportal für die iOS-Registrierung ausrichtet. Gerätebenutzer wird jetzt Folgendes angezeigt:  

* Eine schlankere Benutzeroberfläche  
* Eine verbesserte Prüfliste für die Registrierung  
* Deutlichere Anweisungen zum Registrieren ihrer Geräte  
* Verbesserte Optionen zur Problembehandlung  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Web-Apps, die aus der Windows-Unternehmensportal-App gestartet werden<!-- 5030972 -->
Endbenutzer können Web-Apps jetzt direkt aus der Windows-Unternehmensportal-App starten. Endbenutzer können die Web-App auswählen und dann die Option **Im Browser öffnen** auswählen. Die veröffentlichte Web-URL wird direkt einem Webbrowser geöffnet. Diese Funktionalität wird in der nächsten Woche eingeführt. Weitere Informationen über Web-Apps finden Sie unter [Hinzufügen von Web-Apps zu Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950-wnready---"></a>Neue Spalte für den Zuweisungstyp im Unternehmensportal für Windows 10 <!-- 5459950 WNready -->
Die Spalte im Unternehmensportal unter **Installierte Apps** > **Zuweisungstyp** wurde in **Von Ihrer Organisation als erforderlich festgelegt** umbenannt.  Unter dieser Spalte wird den Benutzern der Wert **Yes** (Ja) oder **No** (Nein) angezeigt, um anzugeben, dass eine App entweder erforderlich oder von ihrer Organisation als optional angesehen wird. Diese Änderungen wurden durchgeführt, da Gerätebenutzer über das Konzept der verfügbaren Apps irritiert waren. Ihre Benutzer können weitere Informationen zum Installieren von Apps im Unternehmensportal unter [Installieren und Freigeben von Apps auf Ihrem Gerät](/intune-user-help/install-apps-cpapp-windows) finden. Weitere Informationen zum Konfigurieren der Unternehmensportal-App für Ihre Benutzer finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Woche vom 4. November 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Gerätesicherheit

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Sicherheitsbaselines werden auf Microsoft Azure Government unterstützt.<!-- 4062552 -->

Intune-Instanzen, die auf *Microsoft Azure Government* gehostet werden, können nun [Sicherheitsbaselines](../protect/security-baselines.md) verwenden, mit denen Sie Ihre Benutzer und Geräte sichern und schützen können.

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>Woche vom 28. Oktober 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Verbessertes Prüflistendesign in der Unternehmensportal-App für Android<!-- 5550857 -->  
Die Prüfliste für das Setup in der Unternehmensportal-App für Android wurde mit einem vereinfachten Design und neuen Symbolen aktualisiert. Die Änderungen stimmen mit den neuesten Updates überein, die an der Unternehmensportal-App für iOS vorgenommen wurden. Einen parallelen Vergleich der Änderungen finden Sie unter [Änderungen an der App-UI](whats-new-app-ui.md). Weitere Informationen zu den aktualisierten Registrierungsschritten finden Sie unter [Registrieren bei Android-Arbeitsprofilen](/intune-user-help/enroll-device-android-work-profile) und [Registrieren Ihres Android-Geräts](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Win32-Apps auf Geräten im Windows 10 S Modus<!-- 3747604 --> 
Sie können Win32-Apps auf im Windows 10 S Modus verwalteten Geräten installieren und ausführen. Hierfür können Sie mithilfe der WDAC-PowerShell-Tools (Windows Defender-Anwendungssteuerung) eine oder mehrere ergänzende Richtlinien für Windows im S Modus erstellen. Signieren Sie die ergänzenden Richtlinien mit dem Portal für den Device Guard-Signaturdienst, und laden Sie dann die Richtlinien über Intune hoch, und verteilen Sie diese. Sie finden diese Funktion in Intune, indem Sie auf **Client-Apps** > **Windows 10 S supplemental policies** (Ergänzende Windows 10 S-Richtlinien) klicken. Weitere Informationen finden Sie unter [Aktivieren von Win32-Apps auf Geräten im S Modus](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Festlegen der Verfügbarkeit einer Win32-App basierend auf Datum und Zeit<!-- 3510685 -->
Als Administrator können Sie den Beginn und das Ende der Verfügbarkeit einer erforderlichen Win32-App konfigurieren. Die Intune-Verwaltungserweiterung startet zum Startzeitpunkt den Download der App-Inhalte und sorgt dafür, dass diese zwischengespeichert werden. Die App wird zu einem bestimmten Endzeitpunkt installiert. In Bezug auf verfügbare Apps wird durch den Startzeitpunkt vorgegeben, wann die App im Unternehmensportal sichtbar ist. Weitere Informationen finden Sie unter [Win32-App-Verwaltung in Intune](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Geräteneustart basierend auf der Toleranzperiode nach der Installation der Win32-App<!-- 3136567 -->
Sie können festlegen, dass ein Gerät nach der erfolgreichen Installation einer Win32-App neu gestartet werden muss. Weitere Informationen finden Sie unter [Win32-App-Verwaltung: Installationsdetails zum Konfigurieren von Apps](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Dunkler Modus für iOS-Unternehmensportal<!-- 4911422 -->
Der dunkle Modus ist für das iOS-Unternehmensportal verfügbar. Benutzer können Unternehmens-Apps herunterladen, ihre Geräte verwalten und IT-Support im Farbschema Ihrer Wahl basierend auf den Geräteeinstellungen erhalten. Das iOS-Unternehmensportal passt sich automatisch den Einstellungen des Endbenutzergeräts für den hellen oder dunklen Modus an. Weitere Informationen finden Sie unter [Introducing dark mode on Microsoft Intune Company Portal for iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453) (Einführung des dunklen Modus im Microsoft Intune-Unternehmensportal für iOS). Weitere Informationen zum iOS-Unternehmensportal finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Vom Android-Unternehmensportal erzwungene App-Mindestversion<!-- 2378776 -->
Mithilfe der Einstellung **Mindestversion für Unternehmensportal** einer App-Schutzrichtlinie können Sie eine bestimmte, minimal definierte Version des Unternehmensportals angeben, die auf einem Endbenutzergerät erzwungen wird. Diese Einstellung für den bedingten Start ermöglicht Ihnen **Zugriff blockieren** , **Daten löschen** oder **Warnen** als mögliche Aktionen, wenn der Wert nicht erreicht wird. Die möglichen Formate für diesen Wert folgen dem Muster *[Hauptversion].[Nebenversion]* , *[Hauptversion].[Nebenversion].[Build]* oder *[Hauptversion].[Nebenversion].[Build].[Revision]* .

Wenn die Einstellung **Mindestversion für Unternehmensportal** konfiguriert ist, wirkt sich die Einstellung auf alle Endbenutzer aus, die Version 5.0.4560.0 des Unternehmensportals und zukünftige Versionen des Unternehmensportals erhalten. Diese Einstellung wirkt sich nicht auf Benutzer aus, die eine Version des Unternehmensportals verwenden, die älter als die Version ist, mit der diese Funktion veröffentlicht wurde. Endbenutzer, die automatische App-Updates auf Ihrem Gerät verwenden, werden wahrscheinlich keine Dialoge dieses Features sehen, da sie wahrscheinlich die neueste Unternehmensportalversion verwenden. Diese Einstellung ist nur für Android mit App-Schutz für registrierte und nicht registrierte Geräte vorgesehen. Weitere Informationen finden Sie unter [Bedingter Start](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365-Geräteverwaltung

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Einführung zum Endpunkt-Sicherheitsknoten in der Microsoft 365-Geräteverwaltung<!-- 5630102 -->

Der **Endpunkt-Sicherheitsknoten** ist jetzt allgemein im speziellen Arbeitsbereich der Microsoft 365-Geräteverwaltung unter https://devicemanagement.microsoft.com verfügbar, wo die Funktionen zum Schützen von Endpunkten gruppiert sind wie etwa:

- Sicherheitsbaselines:  Vorkonfigurierte Gruppe von Einstellungen, mit denen Sie eine bekannte Gruppe von Einstellungen und Standardwerten, die von Microsoft empfohlen werden, anwenden können.

- Sicherheitsaufgaben: Nutzen Sie die Microsoft Defender ATPs-Verwaltung für Bedrohungs-und Sicherheitsrisiken (Threat and Vulnerability Management, TVM), und verwenden Sie Intune, um Endpunktschwächen zu beheben.

- Microsoft Defender ATP: Integrierte Microsoft Defender Advanced Threat Protection (ATP), um Sicherheitsverletzungen zu verhindern.

Diese Einstellungen können weiterhin von anderen anwendbaren Knoten wie Geräten aus aufgerufen werden, und der aktuelle konfigurierte Status ist unabhängig davon identisch, wo Sie auf diese Funktionen zugreifen und sie aktivieren.

Weitere Informationen zu diesen Verbesserungen finden Sie im [Blogbeitrag „Intune Customer Success“](https://aka.ms/Endpoint_security_node) (Intune-Kundenerfolg) auf der Microsoft Tech Community-Website.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune unterstützt iOS 11 und höher<!-- 4665324  -->

Intune-Registrierung und Unternehmensportal unterstützen jetzt die iOS-Versionen 11 und höher. Ältere Versionen werden nicht unterstützt.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Gerätesicherheit

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge-Sicherheitsbaseline (Vorschauversion)<!--  3787164  -->

Wir haben eine Vorschauversion der Sicherheitsbaseline für [Microsoft Edge-Einstellungen](../protect/security-baseline-settings-edge.md) hinzugefügt. 

<!-- ########################## -->
## <a name="week-of-october-21-2019-1910-service-release"></a>Woche vom 21. Oktober 2019 (1910 Dienstrelease)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365-Geräteverwaltung

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Verbesserte Verwaltungsbenutzeroberfläche bei der Microsoft 365-Geräteverwaltung<!-- 5551239 -->

Eine aktualisierte und optimierte Verwaltungsbenutzeroberfläche ist nun im Arbeitsbereich für die Microsoft 365-Geräteverwaltung auf [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com) allgemein verfügbar, einschließlich:

- **Aktualisierte Navigation**: Sie finden eine vereinfachte Navigation auf der ersten Ebene, in der Features logisch gruppiert sind.
- **Neue Plattformfilter**: Auf den Seiten „Geräte“ und „Apps“ können Sie eine einzelne Plattform auswählen, auf der nur die Richtlinien und Apps für die ausgewählte Plattform angezeigt werden.
- **Neue Homepage**: Auf der neuen Startseite sehen Sie auf einen Blick schnell die Dienstintegrität, den Status Ihres Mandanten, Neuigkeiten usw.

Weitere Informationen zu diesen Verbesserungen finden Sie im [Blogbeitrag „Enterprise Mobility + Security“](https://go.microsoft.com/fwlink/?linkid=2109094) auf der Microsoft Tech Community-Website.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Hinzufügen von Mobile Threat Defense-Apps zu nicht registrierten Geräten<!-- 3005337 -->
Sie können eine Intune-App-Schutzrichtlinie erstellen, die die Unternehmensdaten des Benutzers basierend auf der Integrität eines Geräts blockieren oder selektiv löschen kann. Die Integrität des Geräts wird mithilfe der Lösung Ihrer Wahl für Mobile Threat Defense (MTD) festgelegt. Heute ist diese Funktion bei Geräten, die bei Intune registriert sind, als Gerätekompatibilitätseinstellung verfügbar. Mit diesem neuen Feature erweitern wir die Bedrohungserkennung eines Mobile Threat Defense-Anbieters zur Funktion auf nicht registrierten Geräten. Unter Android ist für dieses Feature das neueste Unternehmensportal auf dem Gerät erforderlich. Unter iOS kann dieses Feature verwendet werden, wenn Apps die neueste Intune SDK-Version (v 12.0.15 +) integrieren. Wir aktualisieren das Thema „Neuerungen“, wenn die erste App die neueste Intune SDK-Version nutzt. Die verbleibenden Apps werden laufend verfügbar sein. Weitere Informationen finden Sie unter [Erstellen einer Mobile Threat Defense-App-Schutzrichtlinie (MTD) mit Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Neues Schnittstellenprofil zur Konfiguration der Gerätefirmware für Geräte mit Windows 10 oder höher (öffentliche Vorschau)<!-- 2266073  -->

Ab Windows 10 können Sie ein Gerätekonfigurationsprofil zum Steuern der Einstellungen und Features erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** als Plattform). In diesem Update gibt es einen neuen Schnittstellenprofiltyp zur Konfiguration der Gerätefirmware, mit dem Intune UEFI-Einstellungen (BIOS) verwalten kann.

Weitere Informationen zu diesem Feature finden Sie unter [Verwenden von DFCI-Profilen auf Windows-Geräten in Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Gilt für:
- Windows 10 RS5 (1809) und höher auf unterstützter Firmware

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Umschalten zur ausschließlichen Anzeige der Seite zum Registrierungsstatus auf per Eindruck beim ersten Ausführen (Out-of-Box Experience, OOBE) bereitgestellten Geräten<!--3959566-->
Sie können jetzt wahlweise ausschließlich die Seite zum Registrierungsstatus auf Geräten anzeigen, die von Autopilot OOBE bereitgestellt werden.

Um die neue Umschaltfläche anzuzeigen, wählen Sie **Intune** > **Geräteregistrierung** > **Windows-Registrierung** > **Seite zum Registrierungsstatus** > **Profil erstellen** > **Einstellungen** > **Seite nur für Geräte anzeigen, die über die Willkommensseite bereitgestellt wurden**.


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Woche vom 14. Oktober 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Berichterstellung für verfügbare Google Play-Apps für Android-Arbeitsprofile<!-- 3041956   -->
Sie können den App-Installationsstatus sowie die installierte Version verwalteter Google Play-Apps für verfügbare App-Installationen auf Android Enterprise-Arbeitsprofil-, dedizierten und vollständig verwalteten Geräten anzeigen. Weitere Informationen finden Sie unter [Überwachen von App-Schutzrichtlinien](~/apps/app-protection-policies-monitor.md), [Verwalten von Android-Arbeitsprofilgeräten mit Intune](~/enrollment/android-enterprise-overview.md) und [App-Typ „Verwaltetes Google Play“](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge Version 77 und höher für Windows 10 und macOS (Public Preview)<!-- 3872025, 4678761  -->
Version 77 und höher von Microsoft Edge ist jetzt für die Bereitstellung auf Computern unter Windows 10 und macOS verfügbar. 

Die Public Preview bietet **Entwickler**- und **Beta**-Kanäle für Windows 10 und einen **Beta**-Kanal für macOS. Die Bereitstellung ist nur in englischer Sprache verfügbar, Endbenutzer können die Anzeigesprache im Browser jedoch unter **Einstellungen** > **Sprachen** ändern. Microsoft Edge ist eine Win32-App, die im Systemkontext und auf entsprechenden Architekturen (x86-App auf x86-Betriebssystemen und x64-App auf x64-Betriebssystemen) installiert ist. Außerdem sind automatische Updates des Browsers standardmäßig **Aktiviert**, und Microsoft Edge kann nicht deinstalliert werden. Weitere Informationen finden Sie unter [Hinzufügen von Microsoft Edge für Windows 10 zu Microsoft Intune](~/apps/apps-windows-edge.md) und in der [Microsoft Edge-Dokumentation](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Update der Benutzeroberflächen für den App-Schutz und der iOS-App-Bereitstellung<!-- 4102027, 4102029   -->
Die Benutzeroberflächen zum Erstellen und Bearbeiten von App-Schutzrichtlinien und iOS-App-Bereitstellungsprofilen in Intune wurden upgedatet. Die Änderungen der Benutzeroberfläche umfassen:
- Eine vereinfachte Funktion mithilfe eines Formats im Assistentenstil auf einem einzigen Blatt. 
- Ein Update für den Erstellungsflow zum Einschließen von Zuweisungen.
- Eine zusammengefasste Seite aller festgelegten Einstellungen beim Anzeigen der Eigenschaften, bevor eine neue Richtlinie erstellt wird oder bei der Bearbeitung einer Eigenschaft. Beim Bearbeiten von Eigenschaften zeigt die Zusammenfassung nur eine Liste der Elemente aus der Kategorie der Eigenschaften an, die bearbeitet werden.

Weitere Informationen finden Sie unter [Erstellen und Zuweisen von App-Schutzrichtlinien](~/apps/app-protection-policies.md) und [Verwenden von iOS-App-Bereitstellungsprofilen](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Geführte Szenarios in Intune<!-- 4850318, 4831296, 3610611  -->
In Intune werden nun geführte Szenarios bereitgestellt, die Ihnen beim Durchführen bestimmter Aufgaben in Intune helfen. Ein geführtes Szenario beschreibt eine angepasste Reihe von Schritten (Workflow) für einen End-to-End-Anwendungsfall. Gängige Szenarios werden basierend auf der Rolle eines Administrators, Benutzers oder Geräts in Ihrer Organisation definiert. Diese Workflows erfordern in der Regel eine Sammlung sorgfältig orchestrierter Profile, Einstellungen, Anwendungen und Sicherheitskontrollen, um die beste Benutzererfahrung und Sicherheit bereitzustellen. Die folgenden neuen geführten Szenarios sind verfügbar:
- [Bereitstellen von Microsoft Edge für Mobilgeräte](~/fundamentals/guided-scenarios-edge.md)
- [Sichere mobile Microsoft Office-Apps](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Über die Cloud verwalteter moderner Desktop](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Weitere Informationen finden Sie unter [Übersicht über geführte Szenarios in Intune](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Zusätzliche verfügbare App-Konfigurationsvariablen<!-- 4969237   -->
Beim Erstellen einer App-Konfigurationsrichtlinie können Sie die Konfigurationsvariable `AAD Device ID` als Teil Ihrer Konfigurationseinstellungen einfügen. Klicken Sie in Intune auf **Client-Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen**. Geben Sie die Details Ihrer Konfigurationsrichtlinie ein, und klicken Sie auf **Konfigurationseinstellungen**, um das Blatt **Konfigurationseinstellungen** anzuzeigen. Weitere Informationen finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android Enterprise-Geräte: Verwenden des Konfigurations-Designers](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Erstellen von Gruppen von Verwaltungsobjekten namens Richtliniensätze<!-- 3762880  -->
Mit Richtliniensätzen können Sie ein Bündel von Verweisen auf bereits vorhandene Verwaltungsentitäten erstellen, die als einzelne konzeptionelle Einheit identifiziert, ausgerichtet und überwacht werden müssen. Richtliniensätze stellen keinen Ersatz für vorhandene Konzepte oder Objekte dar. Sie können weiterhin individuelle Objekte in Intune zuweisen und als Teil eines Richtliniensatzes referenzieren. Daher werden alle Änderungen an diesen individuellen Objekten im Richtliniensatz berücksichtigt.  Klicken Sie in Intune auf **Richtliniensätze** > **Erstellen**, um einen neuen Richtliniensatz zu erstellen. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Update der Benutzeroberfläche zum Erstellen und Bearbeiten von Windows 10-Updateringen<!-- 4099089         -->
Die Benutzeroberfläche zum [Erstellen und Bearbeiten von Windows 10-Updateringen](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) für Intune wurde upgedatet. Folgende Änderungen wurden an der Benutzeroberfläche vorgenommen:  
- Ein Format im Assistentenstil, das auf einem einzigen Blatt der Konsole zusammengefasst ist, um die vorherige Ausbreitung der Blätter beim Konfigurieren von Updateringen zu vermeiden.   
- Der überarbeitete Workflow umfasst Zuweisungen, bevor die Erstkonfiguration des Rings abgeschlossen wird.
- Eine Zusammenfassungsseite, die Sie zum Überprüfen all Ihrer vorgenommenen Konfigurationen verwenden können, bevor Sie einen neuen Updatering speichern und bereitstellen. Beim Bearbeiten eines Updaterings zeigt die Zusammenfassung nur die Liste der Elemente an, die in der bearbeiteten Kategorie der Eigenschaften festgelegt wurden.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Update der Benutzeroberfläche zum Erstellen und Bearbeiten von iOS-Softwareupdaterichtlinien<!-- 4099090       --> 
Die Benutzeroberfläche zum [Erstellen](../protect/software-updates-ios.md#configure-the-policy) und [Bearbeiten](../protect/software-updates-ios.md#edit-a-policy) von iOS-Softwareupdaterichtlinien für Intune wurden upgedatet.  Folgende Änderungen wurden an der Benutzeroberfläche vorgenommen:  
- Ein Format im Assistentenstil, das auf einem einzigen Blatt der Konsole zusammengefasst ist, um die vorherige Ausbreitung der Blätter beim Konfigurieren von Updaterichtlinien zu vermeiden.   
- Der überarbeitete Workflow umfasst Zuweisungen, bevor die Erstkonfiguration der Richtlinie abgeschlossen wird.
- Eine Zusammenfassungsseite, die Sie zum Überprüfen all Ihrer vorgenommenen Konfigurationen verwenden können, bevor Sie eine neue Richtlinie speichern und bereitstellen. Beim Bearbeiten einer Richtlinie zeigt die Zusammenfassung nur die Liste der Elemente an, die in der bearbeiteten Kategorie der Eigenschaften festgelegt wurden.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Die Einstellungen für erzwungene Neustarts wurden aus Windows-Updateringen entfernt<!--  4464404   WNReady   -->
Wie bereits angekündigt unterstützen Windows 10-Updateringe von Intune nun [Einstellungen für Zeitlimits](../protect/windows-update-settings.md) und unterstützen *erzwungene Neustarts* nicht mehr. Wenn Sie Updateringe in Intune konfigurieren oder verwalten, sind Einstellungen für *erzwungene Neustarts* nicht mehr verfügbar.  

Diese Änderung erfolgt gemäß der jüngsten [Änderungen der Windows-Wartung](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing), und auf Geräten mit Windows 10 Version 1903 oder höher ersetzen *Zeitlimits* die Konfigurationen für *erzwungene Neustarts*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Verhinderung der Installation von Apps aus unbekannten Quellen auf Android Enterprise-Arbeitsprofilgeräten<!-- 4760025   -->
Benutzer können in keinem Fall Apps aus unbekannten Quellen auf Android Enterprise-Arbeitsprofilgeräten installieren. In diesem Update gibt es eine neue Einstellung: **App-Installationen aus unbekannten Quellen im persönlichen Profil verhindern**. Diese Einstellung hindert Benutzer standardmäßig daran, Apps aus unbekannten Quellen in das persönliche Profil auf dem Gerät querzuladen.

Sie finden diese konfigurierbare Einstellung unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Android Enterprise-Arbeitsprofil

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Erstellen eines globalen HTTP-Proxys auf Geräten von Android Enterprise-Gerätebesitzern<!-- 4816339   -->
Sie können einen globalen HTTP-Proxy auf Android Enterprise-Geräten konfigurieren, um die Webbrowserstandards Ihrer Organisation zu erfüllen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** als Plattform > **Gerätebesitzer > Geräteeinschränkungen** als Profiltyp > **Konnektivität**). Nach der Konfiguration wird dieser Proxy für jeglichen HTTP-Datenverkehr genutzt.

Navigieren Sie zum Konfigurieren dieses Features und zum Anzeigen aller konfigurierbaren Einstellungen zu [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Android Enterprise-Gerätebesitzer

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Entfernung der Einstellung zum automatischen Herstellen einer Verbindung wurde aus WLAN-Profilen für Android-Geräteadministratoren und Android Enterprise<!-- 5021055   -->
Auf Android-Geräteadministrator- und Android Enterprise-Geräten können Sie ein WLAN-Profil erstellen, um verschiedene Einstellungen zu konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android-Geräteadministrator** oder **Android Enterprise** als Plattform > **WLAN** als Profiltyp). In diesem Update wurde die Einstellung **Automatisch verbinden** entfernt, da sie [nicht von Android unterstützt wird](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Wenn Sie diese Einstellung in einem WLAN-Profil verwenden ist Ihnen möglicherweise aufgefallen, dass **Automatisch verbinden** nicht funktioniert. Sie müssen keine Maßnahmen ergreifen, beachten Sie jedoch, dass diese Einstellung aus der Benutzeroberfläche von Intune entfernt wurde.

Die aktuellen Einstellungen finden Sie in den [Android-WLAN-Einstellungen](../configuration/wi-fi-settings-android.md) oder den [Android Enterprise-WLAN-Einstellungen](../configuration/wi-fi-settings-android-enterprise.md).

Gilt für:
- Android-Geräteadministrator 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Neue Gerätekonfigurationseinstellungen für überwachte iOS- und iPadOS-Geräte<!-- 5199328   -->
Auf iOS- und iPadOS-Geräten können Sie ein Profil erstellen, um Features und Einstellungen auf Geräten einzuschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). In diesem Update gibt es neue Einstellungen, die Sie steuern können: 
- Zugriff auf Netzlaufwerk in Dateien-App  
- Access to USB drive in Files app (Zugriff auf USB-Laufwerk in Dateien-App) 
- WLAN immer aktiviert 

Diese Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:
- iOS 13.0 und neuer
- iOS 13.0 und höher

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Festlegen der Version des Android-Gerätebetriebssystems, das mit einem Arbeitsprofil oder einer Geräteadministratorregistrierung registriert wird<!-- 4350697   -->
Mithilfe der Intune-Gerätetypeinschränkungen können Sie die Betriebssystemversion des Geräts verwenden, um festzulegen, welche Benutzergeräte die Android Enterprise-Arbeitsprofilregistrierung oder Android-Geräteadministratorregistrierung verwenden.  Weitere Informationen finden Sie unter [Festlegen von Registrierungseinschränkungen](../enrollment/enrollment-restrictions-set.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Neue Einschränkungen zum Umbenennen von Windows-Geräten<!-- 3478938  -->
Beim Umbenennen von Windows-Geräten müssen Sie neue Regeln befolgen:
- Der Name sollte aus 15 Zeichen oder weniger (d. h. weniger als oder gleich 63 Byte ohne nachstehender NULL) bestehen.
- Der Name sollte nicht NULL sein oder aus einer leeren Zeichenfolge bestehen.
- Zulässiger ASCII-Code: Buchstaben (a-z, A-Z), Zahlen (0-9) und Bindestriche
- Zulässige Unicode-Zeichen: Zeichen >= 0x80, muss eine gültige UTF-8-Codierung und die IDN-Zuordnung (RtlIdnToNameprepUnicode erfolgreich, weitere Informationen finden Sie im RFC 3492) aufweisen
- Namen dürfen nicht nur aus Zahlen bestehen.
- Es dürfen keine Leerzeichen im Namen enthalten sein.
- Unzulässige Zeichen: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Weitere Informationen finden Sie unter [Umbenennen von Geräten in Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Neuer Android-Bericht auf der Geräteübersichtseite<!-- 4924364 -->
Auf der Geräteübersichtseite zeigt ein neuer Bericht, wie viele Android-Geräte in jeder Geräteverwaltungslösung registriert wurden. Dieses Diagramm zeigt die Anzahl der Arbeitsprofile, vollständig verwalteten, dedizierten und mit Geräteadministratorregistrierung registrierten Geräte angezeigt. Klicken Sie auf **Intune** > **Geräte** > **Übersicht**, um den Bericht anzuzeigen.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Gerätesicherheit

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>PKCS-Zertifikate für macOS<!-- 1333650       -->
Sie können nun [PKCS-Zertifikate mit macOS verwenden](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). Sie können das PKCS-Zertifikat als Profiltyp für macOS auswählen und Benutzer- und Gerätezertifikate bereitstellen, die [Felder für einen benutzerdefinierten Betreff und alternativen Antragstellernamen](../protect/certficates-pfx-configure.md#subject-name-format-for-macos) besitzen.  

PKCS-Zertifikate für macOS unterstützen ebenfalls eine neue Einstellung: _Allow All Apps Access_ (Allen Apps Zugriff gewähren). Mit dieser Einstellung können Sie alle zugeordneten Apps den Zugriff auf den privaten Schlüssel des Zertifikats gewähren.  Weitere Informationen zu dieser Einstellung finden Sie in der Dokumentation von Apple unter https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Abgeleitete Anmeldeinformationen zum Bereitstellen von iOS-Mobilgeräten mit Zertifikaten<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune unterstützt die Verwendung von [abgeleiteten Anmeldeinformationen](../protect/derived-credentials.md) als Authentifizierungsmethode, für die S/MIME-Signatur und Verschlüsselung von iOS-Geräten. Abgeleitete Anmeldeinformationen sind eine Implementierung der *NIST-Standards 800-157 (National Institute of Standards and Technology)* für die Bereitstellung von Zertifikaten auf Geräten.  

Abgeleitete Anmeldeinformationen stützen sich auf die Verwendung einer PIV- (Personal Identity Verification) oder CAC-Karte (Common Access Card), z. B. eine Smartcard. Zum Abrufen von abgeleiteten Anmeldeinformationen für ihr mobiles Gerät beginnen Benutzer in der Unternehmensportal-App und befolgen einen Workflow für die Registrierung, die für den verwendeten Anbieter eindeutig ist.  Alle Anbieter haben die Voraussetzung zur Verwendung einer Smartcard auf Computern gemein, um den Anbieter der abgeleiteten Anmeldeinformationen zu authentifizieren. Dieser Anbieter gibt dann ein Zertifikat auf dem Gerät aus, das von der Smartcard des Benutzers abgeleitet wird.  

Intune unterstützt die folgenden Anbieter abgeleiteter Anmeldeinformationen:
- DISA Purebred
- Entrust Datacard
- Intercede

Sie verwenden abgeleitete Anmeldeinformationen als Authentifizierungsmethode für Gerätekonfigurationsprofile für VPN, WLAN und E-Mail. Sie können sie auch für die App-Authentifizierung, S/MIME-Signatur und Verschlüsselung verwenden.  

Weitere Informationen zum Standard finden Sie unter [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) (Abgeleitete PIV-Anmeldeinformationen) unter www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Verwendung der Graph-API zum Festlegen eines lokalen Benutzerprinzipalnamen als Variable für SCEP-Zertifikate<!--  5437939        -->  
Wenn Sie die [Intune-Graph-API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) verwenden, können Sie „onPremisesUserPrincipalName“ als Variable für den alternativen Antragstellernamen (SAN) für SCEP-Zertifikate angeben.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Woche vom 23. September 2019

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>iOS-Benutzerregistrierung in der Vorschau<!-- 4817900 -->
Die iOS 13.1-Version von Apple umfasst die Benutzerregistrierung, eine neue Form der kompakten Verwaltung für iOS-Geräte. Sie kann anstelle der Geräteregistrierung oder der automatisierten Geräteregistrierung (früher Programm zur Geräteregistrierung) für private Geräte verwendet werden. Die Intune-Vorschau unterstützt diese Features, indem sie Folgendes ermöglicht:

- Durchführen der Benutzerregistrierung für Benutzergruppen
- Endbenutzer können beim Registrieren ihrer Geräte zwischen der leichten Benutzerregistrierung und der umfassenderen Benutzerregistrierung auswählen.

Diese Updates werden ab dem 24.9.2019 mit der Veröffentlichung von iOS 13.1 für alle Kunden bereitgestellt. Die Bereitstellung soll bis Ende der darauffolgenden Woche abgeschlossen sein.
Gilt für:

iOS 13.1 und höher

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Intune-Unterstützung für iPadOS- und iOS 13.1-Geräte<!--5439574-->
Intune unterstützt jetzt die Verwaltung von iPadOS- und iOS 13.1-Geräten Weitere Informationen finden Sie in [diesem Blogbeitrag](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019-1909-service-release"></a>Woche vom 16. September 2019 (1909 Dienstrelease)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>Verwaltete private LOB-Apps in Google Play<!-- 1464182  -->
Intune ermöglicht es IT-Administratoren jetzt, private branchenspezifische Android-Apps (Line-of-Business-Apps, LOB-Apps) über einen in die Intune-Konsole eingebetteten IFrame im verwalteten Google Play zu veröffentlichen.  Bisher mussten IT-Administratoren LOB-Apps direkt in der Veröffentlichungskonsole von Google Play veröffentlichen – ein Vorgang, der viele Schritte erforderte und recht zeitaufwendig war. Dieses neue Feature ermöglicht die einfache Veröffentlichung von LOB-Apps mit nur wenigen Schritten, ohne die Intune-Konsole verlassen zu müssen.  Administratoren müssen sich nicht mehr als Entwickler bei Google registrieren und die Google-Registrierungsgebühr von 25 US-Dollar bezahlen.  Alle Android Enterprise-Verwaltungsszenarien, bei denen verwaltetes Google Play verwendet wird, können von diesem Feature profitieren (Arbeitsprofil sowie dedizierte, vollständig verwaltete und nicht registrierte Geräte). Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann in der Liste **App-Typ** die Option **Verwaltetes Google Play** aus. Weitere Informationen zu verwalteten Google Play-Apps finden Sie unter [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Das Windows-Unternehmensportal<!-- 1473353, 3598357 -->
Das Windows-Unternehmensportal wird aktualisiert. Sie können demnächst im Windows-Unternehmensportal auf der Seite „Apps“ mehrere Filter verwenden. Die Seite mit Gerätedetails wird ebenfalls mit benutzerfreundlicheren Funktionen aktualisiert. Diese Updates werden zurzeit für alle Kunden bereitgestellt, und wir planen, die Bereitstellung bis Ende nächster Woche abgeschlossen zu haben.

#### <a name="macos-support-for-web-apps---3174427---"></a>macOS-Unterstützung für Web-Apps<!-- 3174427 -->
Web-Apps, mit denen Sie eine Verknüpfung mit einer URL im Web hinzufügen können, können über das macOS-Unternehmensportal im Dock installiert werden. Endbenutzer können im macOS-Unternehmensportal auf der Seite mit den App-Details für eine Web-App auf die Aktion **Installieren** zugreifen. Weitere Informationen zum App-Typ **Weblink** finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](../apps/apps-add.md) und unter [Hinzufügen von Web-Apps zu Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>macOS-Unterstützung für VPP-Apps<!-- 3173501  -->
Über den Apple Business Manager erworbene macOS-Apps werden in der Konsole angezeigt, wenn Apple VPP-Token in Intune synchronisiert werden. Mithilfe der Intune-Konsole können Sie geräte- und benutzerbasierte Lizenzen für Gruppen zuweisen, widerrufen und neu zuweisen. Bei der Verwaltung von VPP-Apps, die zur Verwendung in Ihrem Unternehmen erworben wurden, werden Sie von Microsoft Intune durch folgende Funktionen unterstützt:

- Melden von Lizenzinformationen aus dem App Store
- Nachverfolgen der Anzahl bereits verwendeter Lizenzen
- Verhindern, dass mehr Exemplare der App installiert werden, als Sie besitzen

Weitere Informationen über Intune und VPP finden Sie unter [Verwalten von per Volumenlizenz erworbenen Apps und Büchern mit Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>IFrame-Unterstützung für verwaltetes Google Play<!-- 2871756  -->
Intune bietet jetzt Unterstützung für das Hinzufügen und Verwalten von Weblinks direkt in der Intune-Konsole über den IFrame für verwaltetes Google Play.  So können IT-Administratoren eine URL und eine Symbolgrafik übermitteln und diese Links dann auf Geräten bereitstellen, genauso wie bei normalen Android-Apps. Alle Android Enterprise-Verwaltungsszenarien, bei denen verwaltetes Google Play verwendet wird, können von diesem Feature profitieren (Arbeitsprofil sowie dedizierte, vollständig verwaltete und nicht registrierte Geräte). Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie dann in der Liste **App-Typ** die Option **Verwaltetes Google Play** aus. Weitere Informationen zu verwalteten Google Play-Apps finden Sie unter [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Unbeaufsichtigte Installation von Android-LOB-Apps auf Zebra-Geräten<!-- 4252734  -->
Sie können Android-LOB-Apps (Line-of-Business-Apps, branchenspezifische Apps) unbeaufsichtigt auf [Zebra-Geräten](../configuration/android-zebra-mx-overview.md) installieren, ohne dazu aufgefordert zu werden, die App herunterzuladen und zu installieren. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie im Bereich **App hinzufügen** die Option **Branchenspezifische App** aus. Weitere Informationen finden Sie unter [Hinzufügen von branchenspezifischen Android-Apps zu Microsoft Intune](../apps/lob-apps-android.md).

Zurzeit wird nachdem Herunterladen einer LOB-App eine Benachrichtigung zum **erfolgreichen Download** auf dem Gerät des Benutzers angezeigt. Diese Benachrichtigung kann nur durch Tippen auf **Alle löschen** im Benachrichtigungsbereich verworfen werden. Dieses Problem wird in einem zukünftigen Release behoben, dann erfolgt die Installation vollständig unbeaufsichtigt und ohne visuelle Hinweise.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Lesen und Schreiben von Graph-API-Vorgängen für Intune-Apps<!-- 5031704  -->
Anwendungen können sowohl Lese- als auch Schreibvorgänge für die Intune-Graph-API mithilfe der App-Identität ohne Benutzeranmeldeinformationen aufrufen. Weitere Informationen zum Zugriff auf die Microsoft Graph-API für Intune finden Sie unter [Arbeiten mit Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Geschützte Datenfreigabe und -verschlüsselung für das Intune App SDK für iOS<!-- 3586942  -->
Das Intune App SDK für iOS wird 256-Bit-Verschlüsselungsschlüssel verwenden, wenn die Verschlüsselung von App-Schutzrichtlinien aktiviert ist. Alle Apps müssen die SDK-Version 8.1.1. aufweisen, um die geschützte Datenfreigabe zuzulassen.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Unterstützung für IKEv2-VPN-Profile für iOS<!-- 1943438   -->
Mit diesem Update können Sie VPN-Profile für den nativen iOS-VPN-Client mithilfe des IKEv2-Protokolls erstellen. IKEv2 ist ein neuer Verbindungstyp unter **Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **iOS** > Profiltyp **VPN** > **Verbindungstyp**.

Diese VPN-Profile konfigurieren den nativen VPN-Client, es werden also keine VPN-Client-Apps auf verwalteten Geräten installiert oder per Push auf diese Geräte übertragen. Für dieses Feature müssen Geräte in Intune registriert sein (MDM-Registrierung).

Die derzeit konfigurierbaren VPN-Einstellungen finden Sie unter [Konfigurieren von VPN-Einstellungen auf iOS-Geräten](../configuration/vpn-settings-ios.md).

Gilt für:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Anzeige von Gerätefeatures, Geräteeinschränkungen und Erweiterungsprofilen für iOS- und macOS-Einstellungen nach Registrierungstyp<!-- 4886161   -->

In Intune können Sie Profile für iOS- und macOS-Geräte einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **iOS** oder **macOS** > **Geräteeinschränkungen**, Profiltyp **Geräteeinschränkungen** oder **Erweiterungen**). 

In diesem Update sind die verfügbaren Einstellungen im Intune-Portal nach dem Registrierungstyp kategorisiert, für den sie gelten:

- iOS
  - Benutzerregistrierung
  - Geräteregistrierung
  - Automatisierte Geräteregistrierung (überwacht)
  - Alle Registrierungstypen

- macOS
  - Vom Benutzer genehmigt
  - Geräteregistrierung
  - Automatisierte Geräteregistrierung
  - Alle Registrierungstypen

Gilt für:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Neue Sprachsteuerungseinstellungen für überwachte iOS-Geräte im Kioskmodus<!-- 4892835   -->
In Intune können Sie Richtlinien erstellen, um überwachte iOS-Geräte als Kiosk oder als dediziertes Gerät auszuführen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **iOS** > Profiltyp **Geräteeinschränkungen** > **Kiosk**).

In diesem Update gibt es neue Einstellungen, die Sie steuern können:
- **Sprachsteuerung**: Aktiviert die Sprachsteuerung auf dem Gerät im Kioskmodus.
- **Änderung der Sprachsteuerung**: Ermöglicht es Benutzern, die Sprachsteuerungseinstellung auf dem Gerät zu ändern, während sich dieses im Kioskmodus befindet.

Die aktuellen Einstellungen finden Sie unter [iOS-Kioskeinstellungen](../configuration/device-restrictions-ios.md#kiosk).

Gilt für:
- iOS 13.0 und höher

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Verwenden des einmaligen Anmeldens für Apps und Websites auf iOS- und macOS-Geräten<!-- 4893175   -->
Dieses Update enthält einige neue Einstellungen für das einmalige Anmelden auf iOS- und macOS-Geräten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **iOS** oder **macOS** > Profiltyp **Gerätefeatures**).

Verwenden Sie diese Einstellungen, um das einmalige Anmelden insbesondere für Apps und Websites zu konfigurieren, die eine Kerberos-Authentifizierung verwenden. Sie können zwischen einer allgemeinen App-Erweiterung für das einmalige Anmelden mit Anmeldeinformationen und der integrierten Kerberos-Erweiterung von Apple auswählen.

Um die aktuellen Gerätefeatures anzuzeigen, die Sie konfigurieren können, wechseln Sie zu [iOS-Gerätefeatures](../configuration/ios-device-features-settings.md) oder [macOS-Gerätefeatures](../configuration/macos-device-features-settings.md).

Gilt für:
- iOS 13.0 und neuer
- macOS 10.15 und neuer

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Zuordnen von Domänen zu Apps auf Geräten unter macOS 10.15 und höher<!-- 4898079   -->
Unter macOS können Sie verschiedene Features konfigurieren und diese mithilfe einer Richtlinie per Push auf Ihre macOS-Geräte übertragen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **macOS** > Profiltyp **Gerätefeatures**). Mit diesem Update können Sie Ihren Apps Domänen zuordnen. Dieses Feature unterstützt Sie dabei, Anmeldeinformationen für Websites freizugeben, die mit Ihrer App in Beziehung stehen. Das Feature kann mit der Apple-Erweiterung für einmaliges Anmelden, universellen Links und der AutoAusfüllen-Funktion für Kennwörter verwendet werden. 

Informationen zu den aktuellen Features, die Sie konfigurieren können, finden Sie unter [macOS-Gerätefunktionseinstellungen in Intune](../configuration/macos-device-features-settings.md).

Gilt für:
- macOS 10.15 und neuer

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Verwenden von „iTunes“ und „apps“ in der iTunes App-Store-URL beim Anzeigen oder Ausblenden von Apps auf überwachten iOS-Geräten<!-- 4928474   --> 
In Intune können Sie Richtlinien erstellen, um Apps auf überwachten iOS-Geräten anzuzeigen oder auszublenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **iOS** > Profiltyp **Geräteeinschränkungen** > **Apps anzeigen oder ausblenden**). 

Sie können die iTunes App-Store-URL eingeben, z. B. `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. In diesem Update können sowohl `apps` als auch `itunes` in der URL verwendet werden. Beispiele:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Weitere Informationen zu diesen Einstellungen finden Sie unter [Anzeigen oder Ausblenden von Apps](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Gilt für:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Werte für Kennworttypen gemäß Windows 10-Konformitätsrichtlinie sind eindeutiger und entsprechen dem Konfigurationsdienstanbieter (CSP)<!-- 5138985 -->
Auf Windows 10-Geräten können Sie eine Konformitätsrichtlinie erstellen, die bestimmte Kennwortfeatures erfordert (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > Plattform **Windows 10 und höher** > **Systemsicherheit**). Dieses Update bietet Folgendes:
- Die Werte für den **Kennworttyp** sind eindeutiger und wurden aktualisiert, um dem Wert für den Konfigurationsdienstanbieter [DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired) zu entsprechen.
- Die Einstellung **Kennwortablauf (Tage)** wurde aktualisiert und lässt jetzt Werte zwischen 1 und 730 Tagen zu. 

Weitere Informationen zu Windows 10-Konformitätseinstellungen finden Sie unter [Einstellungen für Windows 10 und höher, um Geräte als konform oder nicht konform zu kennzeichnen](../protect/compliance-policy-create-windows.md). 

Gilt für:
- Windows 10 und höher

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Aktualisierte Benutzeroberfläche zum Konfigurieren des Zugriffs auf Microsoft Exchange lokal<!-- 4092920 -->  
Wir haben die Konsole aktualisiert, mit der Sie [den Zugriff auf Microsoft Exchange lokal konfigurieren](../protect/conditional-access-exchange-create.md). Alle Konfigurationen für den Zugriff auf Exchange lokal sind jetzt im gleichen Konsolenbereich verfügbar, in dem Sie auch die *Zugriffssteuerung für Exchange lokal aktivieren*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Zulassen oder Einschränken des Hinzufügens von App-Widgets zum Startbildschirm auf Geräten mit Android Enterprise-Arbeitsprofilen<!-- 1109650  --> 
Auf Android Enterprise-Geräten können Sie Features im Arbeitsprofil konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > Plattform **Android Enterprise** > Profiltyp **Nur Arbeitsprofil > Geräteeinschränkungen**). Mit diesem Update können Sie es Benutzern ermöglichen, dem Startbildschirm des Geräts Widgets hinzuzufügen, die von Arbeitsprofil-Apps verfügbar gemacht wurden.

Sie finden die konfigurierbaren Einstellungen unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md).

Gilt für:
- Android Enterprise-Arbeitsprofil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Neue Mandanten verwenden nicht mehr standardmäßig die Verwaltung über den Android-Geräteadministrator<!-- 4869790   -->
Die Funktionen des Geräteadministrators von Android wurden durch Android Enterprise ersetzt. Daher wird empfohlen, für neue Registrierungen stattdessen Android Enterprise zu verwenden. In einem zukünftigen Update müssen neue Mandanten bei der Registrierung in Android die folgenden Schritte ausführen, um die Verwaltung über den Geräteadministrator zu verwenden: Wechseln Sie zu **Intune** > **Geräteregistrierung** > **Android-Registrierung** > **Persönliche und unternehmenseigene Geräte mit Geräteverwaltungsrechten** > **Geräteadministrator zum Verwalten von Geräten verwenden**.

Für vorhandene Mandanten ergeben sich keine Änderungen in ihren Umgebungen.

Weitere Informationen zum Android-Geräteadministrator in Intune finden Sie unter [Android-Geräteadministratorregistrierung](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>Liste von DEP-Geräten, die einem Profil zugeordnet sind<!-- 5012045 idmiss -->
Sie können jetzt eine paginierte Liste mit Geräten im Apple-Programm zur automatischen Geräteregistrierung (Apple Automated Device Enrollment Program, DEP) anzeigen, die einem Profil zugeordnet sind. Sie können auf jeder Seite der Liste nach Geräten suchen. Um die Liste anzuzeigen, wechseln Sie zu **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > Token auswählen > **Profile** > Profil auswählen > **Zugewiesene Geräte** (unter **Monitor**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Zusätzliche Unterstützung für vollständig verwaltete Android-Geräte<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Wir haben folgende Unterstützungsfeatures für vollständig verwaltete Android-Geräte hinzugefügt:

- SCEP-Zertifikate für vollständig verwaltetes Android stehen zur Zertifikatauthentifizierung auf Geräten zur Verfügung, die als Gerätebesitzer verwaltet werden. SCEP-Zertifikate werden auf Arbeitsprofilgeräten bereits unterstützt.  SCEP-Zertifikate für Gerätebesitzer ermöglichen Folgendes: <!-- 5227935 -->
    - Erstellen von SCEP-Profilen im Abschnitt „Gerätebesitzer“ (Device Owner, DO) von Android Enterprise
    - Verknüpfen von SCEP-Zertifikaten mit dem WLAN-Profil eines Gerätebesitzers zur Authentifizierung
    - Verknüpfen von SCEP-Zertifikaten mit VPN-Profilen eines Gerätebesitzers zur Authentifizierung
    - Verknüpfen von SCEP-Zertifikaten mit E-Mail-Profilen eines Gerätebesitzers zur Authentifizierung (über AppConfig)
- System-Apps werden auf Android Enterprise-Geräten unterstützt. In Intune fügen Sie eine Android Enterprise-System-App über **Client-Apps** > **Apps** > **Hinzufügen** hinzu. Wählen Sie in der Liste **App-Typ** den Eintrag **Android Enterprise-System-App** aus. Weitere Informationen finden Sie unter [Hinzufügen von Android Enterprise-System-Apps zu Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- Unter **Gerätekonformität** > **Android Enterprise** > **Gerätebesitzer** können Sie eine Konformitätsrichtlinie erstellen, die die Nachweisstufe „Google SafetyNet“ festlegt.   <!-- 4631425 -->
- Auf vollständig verwalteten Android Enterprise-Geräten werden Mobile Threat Defense-Anbieter unterstützt. Unter **Gerätekonformität** > **Android Enterprise** > **Gerätebesitzer** können Sie eine akzeptable Bedrohungsstufe auswählen. <!-- 4631440 --> Unter [Android Enterprise-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen](../protect/compliance-policy-create-android-for-work.md#device-owner) werden die aktuellen Einstellungen aufgelistet.
- Auf vollständig verwalteten Android Enterprise-Geräten kann jetzt die Microsoft Launcher-App über App-Konfigurationsrichtlinien so konfiguriert werden, dass auf dem vollständig verwalteten Gerät standardisierte Endbenutzerfunktionen zugelassen werden. Die Microsoft Launcher-App kann zum Personalisieren von Android-Geräten verwendet werden. Wenn Sie die App in Verbindung mit einem Microsoft-Konto oder einem Geschäfts-, Schul- oder Unikonto verwenden, können Sie in Ihrem personalisierten Feed auf Ihre Kalender, Dokumente und aktuellen Aktivitäten zugreifen. <!-- 5334044 -->

Wir freuen uns, mit diesem Update bekannt geben zu können, dass die Intune-Unterstützung für vollständig verwaltete Android Enterprise-Geräte jetzt allgemein verfügbar ist.

Gilt für:

- Vollständig verwaltete Android Enterprise-Geräte

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Senden von benutzerdefinierten Benachrichtigungen an einzelne Geräte<!-- 4928910 -->
Sie können jetzt ein einzelnes Gerät auswählen und dann eine Remoteaktion verwenden, um [eine benutzerdefinierte Benachrichtigung nur an dieses Gerät zu senden](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Aktionen zum Zurücksetzen von Geräten und Passcodes sind für iOS-Geräte nicht verfügbar, die über die Benutzerregistrierung registriert wurden<!-- 4950491 -->
Die Benutzerregistrierung ist ein neuer Typ der Apple-Geräteregistrierung. Wenn Sie Geräte über die Benutzerregistrierung registrieren, sind die Remoteaktionen zum Zurücksetzen von Geräten und Passcodes für diese Geräte nicht verfügbar.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Intune-Unterstützung für iOS 13- und macOS Catalina-Geräte<!-- 4665317 -->
Intune unterstützt jetzt die Verwaltung sowohl von iOS 13- als auch von macOS Catalina-Geräten.
Weitere Informationen finden Sie im [Blogbeitrag des Microsoft Intune-Supportteams zu iOS 13 und iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Gerätesicherheit

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>BitLocker-Unterstützung für die clientgesteuerte Rotation von Wiederherstellungskennwörtern<!--  3444125 -->
Verwenden Sie Intune Endpoint Protection-Einstellungen, um die [clientgesteuerte Rotation von Wiederherstellungskennwörtern](../protect/endpoint-protection-windows-10.md#windows-encryption) für BitLocker auf Geräten unter Windows-Version 1909 oder höher zu konfigurieren.

Diese Einstellung initiiert die clientgesteuerte Aktualisierung eines Wiederherstellungskennworts nach der Wiederherstellung eines Betriebssystemlaufwerks (durch Verwendung von bootmgr oder WinRE) sowie die Entsperrung eines Wiederherstellungskennworts auf einem festen Datenlaufwerk. Diese Einstellung aktualisiert das verwendete Wiederherstellungskennwort; nicht verwendete Kennwörter auf dem Volume bleiben unverändert. Weitere Informationen finden Sie in der Dokumentation des BitLocker-Konfigurationsdienstanbieters zu [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Manipulationsschutz für Windows Defender Antivirus<!-- 4705448        -->
Verwenden Sie Intune, um den *Manipulationsschutz* für Windows Defender Antivirus zu verwalten. Sie finden die [Einstellung für den Manipulationsschutz](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) in der Microsoft Defender Security Center-Gruppe, wenn Sie Gerätekonfigurationsprofile für den Windows 10-Endpunktschutz verwenden. Legen Sie den Manipulationsschutz auf *Aktiviert* fest, um die Einschränkungen des Manipulationsschutzes zu aktivieren. Durch Festlegen von *Deaktiviert* deaktivieren Sie die Einschränkungen, und durch Festlegen von *Nicht konfiguriert* behalten Sie die aktuelle Konfiguration eines Geräts bei.  

Weitere Informationen zum Manipulationsschutz finden Sie unter [Verhindern von Änderungen an Sicherheitseinstellungen mit dem Manipulationsschutz](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) in der Windows-Dokumentation.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Erweiterte Einstellungen für die Windows Defender-Firewall sind jetzt allgemein verfügbar<!--  5317392       -->  
Die [benutzerdefinierten Windows Defender-Firewallregeln für den Endpunktschutz](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), die Sie im Rahmen eines Gerätekonfigurationsprofils konfigurieren, sind jetzt allgemein verfügbar.  Mit diesen Regeln können Sie das Eingangs- und Ausgangsverhalten für Anwendungen, Netzwerkadressen und Ports festlegen. Diese Regeln wurden im Juli in der öffentlichen Vorschau freigegeben. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>Bereichstags unterstützen jetzt Richtlinien für Nutzungsbedingungen<!-- 2358863 idmiss -->
Sie können jetzt [Bereichstags](scope-tags.md) zu Richtlinien für Nutzungsbedingungen zuweisen. Verwenden Sie dazu folgende Optionen: **Intune** > **Geräteregistrierung** > **Bestimmungen** > Element in der Liste auswählen > **Eigenschaften** > **Bereichstags** > Bereichstag auswählen.

## <a name="week-of-september-9-2019"></a>Woche vom 9. September 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Updates der Microsoft Intune-App<!-- 4997846 -->
Die Microsoft Intune-App für Android wurde mit den folgenden Verbesserungen aktualisiert:
- Das Layout wurde aktualisiert und verbessert, um das unterste Navigationsmenü für die wichtigsten Aktionen einzubeziehen.
- Eine zusätzliche Seite, die das Profil des Benutzers anzeigt, wurde hinzugefügt.
- Die Anzeige von handlungsrelevanten Benachrichtigungen für den Benutzer wurde in der App hinzugefügt, z. B. die Notwendigkeit, die Geräteeinstellungen zu aktualisieren.
- Die Anzeige von benutzerdefinierten Pushbenachrichtigungen wurde hinzugefügt, wodurch die App der Unterstützung angepasst wird, die kürzlich in den Unternehmensportal-Apps für iOS und Android hinzugefügt wurde. Weitere Informationen finden Sie unter [Senden benutzerdefinierter Benachrichtigungen in Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>Für iOS-Geräte: Anpassen des Datenschutzbildschirms für den Registrierungsvorgang im Unternehmensportal<!-- 4394993 -->
Mithilfe von Markdown können Sie den Datenschutzbildschirm im Unternehmensportal anpassen, der den Endbenutzern während der iOS-Registrierung angezeigt wird. Insbesondere können Sie die Liste der Elemente und Vorgänge anpassen, die Ihre Organisation auf dem Gerät nicht anzeigen bzw. ausführen kann. Weitere Informationen finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Woche vom 2. September 2019

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Update der Intune-Benutzeroberfläche – Mandantenstatusdashboard<!-- 5273210  -->
Die Benutzeroberfläche des Mandantenstatusdashboards wurde aktualisiert und den Stilen von Azure-Benutzeroberflächen angepasst. Weitere Informationen finden Sie unter [Mandantenstatus](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Woche vom 26. August 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Konfigurieren von Microsoft Edge-Einstellungen mithilfe administrativer Vorlagen für Windows 10 und höher<!-- 5228061 -->

Auf Geräten mit Windows 10 oder höher können Sie administrative Vorlagen erstellen, um Gruppenrichtlinieneinstellungen in Intune zu konfigurieren. In diesem Update können Sie Einstellungen konfigurieren, die auf Microsoft Edge Version 77 und höher angewendet werden.

Weitere Informationen zu administrativen Vorlagen finden Sie unter [Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Intune](../configuration/administrative-templates-windows.md).

Gilt für:

- Windows 10 und höher (Windows RS4 und höher)

## <a name="week-of-august-12-2019-1908-service-release"></a>Woche vom 12. August 2019 (1908 Dienstrelease)

### <a name="app-management"></a>App-Verwaltung

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Steuern des Deinstallationsverhaltens einer iOS-App bei einer Aufhebung der Registrierung eines Geräts<!-- 3504144   -->
Administratoren können verwalten, ob eine App von einem Gerät entfernt oder auf dem Gerät beibehalten wird, wenn die Registrierung des Geräts auf Benutzer- oder Gerätegruppenebene aufgehoben wird. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Kategorisieren von Apps aus dem Microsoft Store für Unternehmen<!-- 3926922 -->
Sie können Microsoft Store für Unternehmen-Apps kategorisieren. Wählen Sie hierzu **Intune** > **Client-Apps** > **Apps** > eine Microsoft Store für Unternehmen-App auswählen > **App-Informationen** > **Kategorie** aus. Weisen Sie im Dropdownmenü eine Kategorie zu.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Angepasste Benachrichtigungen für Microsoft Intune-App-Benutzer<!-- 4843354  -->
Die Microsoft Intune-App für Android unterstützt jetzt die Anzeige von benutzerdefinierten Pushbenachrichtigungen, wodurch sie an die Unterstützung angepasst ist, die kürzlich in den Unternehmensportal-Apps für iOS und Android hinzugefügt wurde. Weitere Informationen finden Sie unter [Senden benutzerdefinierter Benachrichtigungen in Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Neue Features für dedizierte Android Enterprise-Geräte im Multi-App-Modus<!-- 3755304 3041943 3041946   -->

In Intune können Sie Features und Einstellungen in einer kioskartigen Umgebung auf Ihren dedizierten Android Enterprise-Geräten verwalten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Nur Gerätebesitzer, Geräteeinschränkungen** für Profiltyp).

In diesem Update werden die folgenden Features hinzugefügt:

- **Dedizierte Geräte** > **Multi-App**: Die **Virtuelle Startschaltfläche** kann angezeigt werden, indem auf dem Gerät nach oben gewischt wird oder die Schaltfläche auf dem Bildschirm schwebt, sodass Benutzer sie verschieben können.
- **Dedizierte Geräte** > **Multi-App**: **Flashlight-Zugriff** ermöglicht es Benutzern, die Taschenlampe zu verwenden. 
- **Dedizierte Geräte** > **Multi-App**: **Medienlautstärkeregler** ermöglicht es Benutzern, über einen Schieberegler die Medienlautstärke des Geräts zu steuern. 
- **Dedizierte Geräte** > **Multi-App**:  **Einen Bildschirmschoner aktivieren**, ein benutzerdefiniertes Bild hochladen und steuern, wann der Bildschirmschoner angezeigt wird.

Die aktuellen Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Gilt für:

- Dedizierte Android Enterprise-Geräte

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Neue App- und Konfigurationsprofile für vollständig verwaltete Android Enterprise-Geräte<!-- 3574215 3574238 3574235 3574232   -->
Mithilfe von Profilen können Sie Einstellungen konfigurieren, mit denen VPN-, E-Mail-und WLAN-Einstellungen auf Ihre (vollständig verwalteten) Android Enterprise-Gerätebesitzer-Geräte angewendet werden. In diesem Update haben Sie folgende Möglichkeiten:

- Sie können [App-Konfigurationsrichtlinien](../apps/app-configuration-policies-use-android.md) verwenden, um Outlook-, Gmail- und Nine Work-E-Mail-Einstellungen bereitzustellen.
- Sie können Gerätekonfigurationsprofile verwenden, um [Einstellungen für vertrauenswürdige Stammzertifikate](../protect/certificates-configure.md) bereitzustellen.
- Sie können Gerätekonfigurationsprofile verwenden, um [VPN](../configuration/vpn-settings-android-enterprise.md)- und [WLAN](../configuration/wi-fi-settings-android-enterprise.md)-Einstellungen bereitzustellen.

> [!IMPORTANT]
> Mit diesem Feature authentifizieren sich Benutzer mit Ihrem Benutzernamen und Kennwort für VPN-, WLAN- und E-Mail-Profile. Derzeit ist zertifikatbasierte Authentifizierung nicht verfügbar.

Gilt für:  
- Android Enterprise-Gerätebesitzer (vollständig verwaltet)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Steuern der Apps, Dateien, Dokumente und Ordner, die geöffnet werden, wenn Benutzer sich bei macOS-Geräten anmelden<!--3914202   -->
Sie können Funktionen auf macOS-Geräten aktivieren und konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** für Plattform > **Gerätefunktionen** für Profiltyp). 

In diesem Update gibt es eine neue „Anmeldeelemente“-Einstellung, mit der gesteuert wird, welche Apps, Dateien, Dokumente und Ordner geöffnet werden, wenn sich ein Benutzer am registrierten Gerät anmeldet. 

Informationen zu den aktuellen Einstellungen finden Sie unter [macOS-Gerätefunktionseinstellungen in Intune](../configuration/macos-device-features-settings.md).

Gilt für:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Stichtage ersetzen Einstellungen für erzwungenen Neustart für Windows-Updateringe<!-- 4464404        -->
Um mit den neuesten [Windows-Wartungsänderungen](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing) übereinzustimmen, unterstützen die Windows 10-Updateringe von Intune jetzt [Einstellungen für Stichtage](../protect/windows-update-settings.md). *Stichtage* bestimmen, wann Funktions- und Sicherheitsupdates auf einem Gerät installiert werden.  Auf Geräten, auf denen Windows 10 1903 oder höher ausgeführt wird, ersetzen *Stichtage* die Konfigurationen für *erzwungenen Neustart*.  Zukünftig wird auch in früheren Versionen von Windows 10 *erzwungener Neustart* durch *Stichtage* ersetzt.  

Wenn Sie keine *Zeitlimits* konfigurieren, werden für Geräte weiterhin deren Einstellungen für *erzwungenen Neustart* verwendet. In einem zukünftigen Update wird die Intune-Unterstützung für die Einstellungen für erzwungenen Neustart jedoch eingestellt.  

Sie sollten die Verwendung von *Stichtagen* für sämtliche Ihrer Windows 10-Geräte planen. Sobald Einstellungen für *Stichtage* vorhanden sind, können Sie die Intune-Konfigurationen für *erzwungenen Neustart* auf „Nicht konfiguriert“ festlegen. Sind diese Konfigurationen auf „Nicht konfiguriert“ festgelegt, beendet Intune das Verwalten dieser Einstellungen auf Geräten, ohne die letzten Konfigurationen für die Einstellung vom Gerät zu entfernen. Daher bleiben die letzten Konfigurationen, die für *erzwungenen Neustart* festgelegt wurden, solange auf Geräten aktiv und wirksam, bis diese Einstellungen durch eine andere Methode als Intune geändert werden. Wenn sich später die Geräteversion von Windows ändert oder wenn später die Intune-Unterstützung für *Stichtage* auf die Windows-Version der Geräte erweitert wird, werden auf dem jeweiligen Gerät die neuen Einstellungen verwendet, die bereits vorhanden sind.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Unterstützung für mehrere Microsoft Intune Certificate Connectors<!--   4704642      -->
Intune unterstützt nun die Installation und Verwendung von mehreren [Microsoft Intune Certificate Connectors für PKCS-Vorgänge](../protect/certficates-pfx-configure.md). Diese Änderung unterstützt Lastenausgleich und Hochverfügbarkeit der Connectors. Jede Connectorinstanz kann Zertifikatanforderungen von Intune verarbeiten.  Ist ein Connector nicht verfügbar, übernehmen andere Connectors die Verarbeitung von Anforderungen.

Wenn Sie mehrere Connectors verwenden möchten, müssen Sie kein Upgrade auf die neueste Version der Connector-Software durchführen.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Neue Einstellungen und Änderungen an vorhandenen Einstellungen, um Funktionen auf iOS- und macOS-Geräten einzuschränken<!-- 4867699 4867709   -->
Sie können Profile erstellen, um Einstellungen auf iOS-und macOS-Geräten einzuschränken (**Gerätekonfigurationen** > **Profile** > **Profil erstellen** > **iOS** oder **macOS** für Plattformtyp > **Geräteeinschränkungen**). Dieses Update umfasst folgende Funktionen:

- Unter **macOS** > **Geräteeinschränkungen** > **Cloud und Speicher** verwenden Sie die neue **Handoff**-Einstellung, um Benutzer daran zu hindern, eine Arbeit auf einem macOS-Gerät zu beginnen und diese Arbeit auf einem anderen macOS- oder iOS-Gerät fortzusetzen.

  Die aktuellen Einstellungen finden Sie unter [macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-macos.md).

- Unter **iOS** > **Geräteeinschränkungen** gibt es einige Änderungen:

  - **Integrierte Apps** > **Mein iPhone suchen (nur überwacht)** : Neue Einstellung, die diese Funktion im App-Feature für die Suche blockiert. 
  - **Integrierte Apps** > **Meine Freunde suchen (nur überwacht)** : Neue Einstellung, die diese Funktion im App-Feature für die Suche blockiert. 
  - **Drahtlosnetzwerke** > **Änderung des WLAN-Status (nur überwacht)** : Neue Einstellung, die verhindert, dass Benutzer WLAN auf dem Gerät ein- oder ausschalten können.
  - **Tastatur und Wörterbuch** > **QuickPath (nur überwacht)** : Neue Einstellung, die die QuickPath-Funktion blockiert.
  - **Cloud und Speicher**: **Aktivitätsfortsetzung** wurde in **Handoff** umbenannt.

  Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:  
- macOS 10.15 und neuer
- iOS 13 und neuer

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Einige nicht überwachte iOS-Geräteeinschränkungen werden mit der iOS 13.0-Version zu unbedingt überwachten Einschränkungen<!-- 4867809   -->
In diesem Update gelten einige Einstellungen für unbedingt überwachte Geräte mit der iOS 13.0-Version. Sind diese Einstellungen für nicht überwachte Geräte vor der iOS 13.0-Version konfiguriert und diesen zugewiesen, werden die Einstellungen weiterhin auf diese nicht überwachten Geräte angewendet. Diese Einstellungen gelten auch weiterhin, nachdem die Geräte auf iOS 13.0 aktualisiert wurden. Diese Einschränkungen werden auf nicht überwachten Geräten entfernt, die gesichert und wiederhergestellt werden.

Zu diesen Einstellungen zählen:

- App Store, Dokumentanzeige, Spiele
  - App Store
  - Anstößige iTunes-Musik, Podcasts oder Nachrichteninhalte
  - Hinzufügen von Game Center-Freunden
  - Multiplayerspiele
- Integrierte Apps
  - Kamera
    - FaceTime
  - Safari
    - Automatisch ausfüllen
- Cloud und Speicher
  - In iCloud sichern
  - iCloud-Dokumentsynchronisierung blockieren
  - Synchronisierung zwischen iCloud und Keychain blockieren

Die aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Gilt für:  
- iOS 13.0 und neuer

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Verbesserter Gerätestatus für die macOS FileVault-Verschlüsselung<!-- 4944983         -->
Wir haben einige der [Gerätestatusmeldungen](../protect/encryption-monitor.md#device-encryption-status) für die FileVault-Verschlüsselung auf macOS-Geräten aktualisiert.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Für einige Windows Defender Antivirus-Überprüfungseinstellungen steht in Berichten der Status „Fehlgeschlagen“<!-- 5119229 -->
In Intune können Sie Richtlinien erstellen, um Windows Defender Antivirus zum Überprüfen Ihrer Windows 10-Geräte zu verwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** für Plattform > **Geräteeinschränkungen** für Profiltyp > **Windows Defender Antivirus**). In Berichten steht für **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung** und **Art der durchzuführenden Systemüberprüfung** der Status „Fehlgeschlagen“, obwohl tatsächlich der Status „Erfolgreich“ gemeint ist. 

Dieses Verhalten wurde im vorliegenden Update korrigiert. Daher wird für die Einstellungen **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung** und **Art der durchzuführenden Systemüberprüfung** der Status „Erfolgreich“ mitgeteilt, wenn die Überprüfungen erfolgreich abgeschlossen wurden, und der Status „Fehlgeschlagen“, wenn die Einstellungen nicht angewendet werden konnten.

Weitere Informationen zu den Windows Defender Antivirus-Einstellungen finden Sie unter [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="default-scope-tags---3702875----"></a>Standardbereichsmarkierungen<!-- 3702875  -->
Es ist nun eine neue integrierte Standardbereichsmarkierung verfügbar. Alle nicht markierten Intune-Objekte, die Bereichsmarkierungen unterstützen, werden automatisch der Standardbereichsmarkierung zugewiesen. Die **Standard**-Bereichsmarkierung wird allen vorhandenen Rollenzuweisungen hinzugefügt, um Einklang mit der heutigen Administratorerwartung aufrechtzuerhalten. Wenn Sie nicht möchten, dass ein Administrator Intune-Objekte mit der Standardbereichsmarkierung sehen kann, entfernen Sie die Standardbereichsmarkierung aus der Rollenzuweisung. Dieses Feature ähnelt dem Feature für Sicherheitsbereiche in System Center Configuration Manager. Weitere Informationen finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung und Bereichsmarkierungen für verteilte IT](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Unterstützung für die Registrierung eines Android-Geräteadministrators<!-- 4869749   -->
Die Registrierungsoption „Android-Geräteadministrator“ wurde der Seite „Android-Registrierung“ hinzugefügt (**Intune** > **Geräteregistrierung** > **Android-Registrierung**). „Android-Geräteadministrator“ ist weiterhin standardmäßig für alle Mandanten aktiviert.  Weitere Informationen finden Sie unter [Android-Geräteadministratorregistrierung](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Überspringen weiterer Bildschirme im Setup-Assistenten <!--4877451  -->
Sie können „Programm zur Geräteregistrierung“-Profile so festlegen, dass die folgenden Bildschirme des Setup-Assistenten übersprungen werden:
- Für iOS
    - Darstellung
    - Express-Sprache
    - Bevorzugte Sprache
    - Migration von Gerät zu Gerät
- Für macOS
    - Bildschirmzeit
    - Touch ID-Setup

Weitere Informationen zur Anpassung des Setup-Assistenten finden Sie unter [Erstellen eines Apple-Registrierungsprofils für iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) und [Erstellen eines Apple-Registrierungsprofils für macOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Hinzufügen einer Benutzerspalte zum CSV-Upload für AutoPilot-Geräte<!-- 3823054 -->
Sie können jetzt eine Benutzerspalte zum CSV-Upload für AutoPilot-Geräte hinzufügen. Hiermit können Sie Benutzer massenweise beim Importieren der CSV-Datei zuweisen. Weitere Informationen finden Sie unter [Registrieren von Windows-Geräten in Intune mithilfe von Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Geräteverwaltung

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Konfigurieren des Zeitlimits für automatische Gerätebereinigung auf 30 Tage<!--4231059  -->
Sie können das Zeitlimit für automatische Gerätebereinigung auf 30 Tage als kürzesten Zeitraum (statt des vorherigen Limits von 90 Tagen) nach der letzten Anmeldung festlegen. Navigieren Sie dafür zu **Intune** > **Geräte** > **Setup** > **Gerätebereinigungsregeln**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Buildnummer auf „Hardware“-Seite eines Android-Geräts enthalten<!-- 4461910   -->
Ein neuer Eintrag auf der „Hardware“-Seite für jedes Android-Gerät enthält die Buildnummer des Betriebssystems des Geräts. Weitere Informationen finden Sie unter [Anzeigen von Gerätedetails in Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Woche vom 5. August 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies ist ein unterstützter OEM für OEMConfig auf Android Enterprise-Geräten<!-- 4843713 -->

In Intune können Sie Gerätekonfigurationsprofile erstellen und Einstellungen auf Android Enterprise-Geräte mit OEMConfig anwenden (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **OEMConfig** für Profiltyp).

In diesem Update ist Zebra Technologies ein unterstützter OEM (Original Equipment Manufacturer) für OEMConfig. Weitere Informationen zu OEMConfig finden Sie unter [Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig](../configuration/android-oem-configuration-overview.md).

Gilt für:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019-1907-service-release"></a>Woche vom 22. Juli 2019 (1907 Dienstrelease)

### <a name="app-management"></a>App-Verwaltung

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Angepasste Benachrichtigungen für Benutzer und Gruppen<!-- 16766574          -->
Senden Sie benutzerdefinierte Pushbenachrichtigungen aus der Unternehmensportalanwendung an Benutzer auf iOS- und Android-Geräten, die Sie mit Intune verwalten. Diese mobilen Pushbenachrichtigungen bieten mit Freitext umfassende Anpassungsmöglichkeiten und können für beliebige Zwecke verwendet werden. Sie können Sie auf verschiedene Benutzergruppen in Ihrer Organisation ausrichten. Weitere Informationen finden Sie im Artikel zu [benutzerdefinierte Benachrichtigungen](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>Device Policy Controller-App von Google<!-- 3041950  -->
Mit der App „Managed Home Screen“ ist nun der Zugriff auf die Android Device Policy-App von Google möglich. Die App „Managed Home Screen“ ist ein benutzerdefiniertes Startprogramm, das für Geräte verwendet wird, die bei Intune als dedizierte Android Enterprise-Geräte (AE) registriert sind und den Kioskmodus mit mehreren Apps verwenden. Zu Unterstützungs- und Debugzwecken können Sie auf die Android Device Policy-App zugreifen oder Benutzer auf diese weiterleiten. Diese Startfunktion ist verfügbar, sobald das Gerät registriert wird und sich bei der App „Managed Home Screen“ einloggt. Für diese Funktion sind keine weiteren Installationen nötig.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Outlook-Sicherheitseinstellungen für iOS- und Android-Geräte<!-- 3212619 -->
Sie können jetzt sowohl allgemeine App-Einstellungen als auch Einstellungen für die Datenschutzkonfiguration für Outlook für iOS und Android über einfache Intune-Administratorsteuerung ohne Geräteregistrierung konfigurieren. Die allgemeinen App-Konfigurationseinstellungen sind Einstellungen gleichgestellt, die Administratoren bei der Verwaltung von Outlook für iOS und Android auf registrierten Geräten aktivieren können. Weitere Informationen über Outlook-Einstellungen finden Sie unter [Bereitstellen von Outlook für iOS und Android App-Konfigurationseinstellungen](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Verwenden von „Anwendbarkeitsregeln“ beim Erstellen von Windows 10-Gerätekonfigurationsprofilen <!-- 2549910 eeready   idstaged -->

Sie können Windows 10-Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** (Plattform) > **Anwendbarkeitsregeln**). Mit diesem Update können Sie eine **Anwendbarkeitsregel** so erstellen, dass das Profil nur für eine bestimmte Edition oder Version gilt. Sie können beispielsweise ein Profil erstellen, das einige BitLocker-Einstellungen aktiviert. Sobald Sie das Profil hinzugefügt haben, aktivieren Sie eine Anwendbarkeitsregel, damit das Profil nur für Geräte mit Windows 10 Enterprise gilt.

Informationen zum Hinzufügen einer Anwendbarkeitsregel finden Sie unter [Anwendbarkeitsregeln](../configuration/device-profile-create.md#applicability-rules).

Gilt für: Windows 10 und höher

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Verwenden Sie Token, um gerätespezifische Informationen in benutzerdefinierten Profilen für iOS- und macOS-Geräte hinzuzufügen.<!-- 3330008  -->
Sie können benutzerdefinierte Profile auf iOS- und macOS-Geräten verwenden, um Einstellungen und Funktionen zu konfigurieren, die nicht in Intune integriert sind (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** oder **macOS** (Plattform) > **Benutzerdefiniert** (Profiltyp)). Mit diesem Update können Sie Ihren `.mobileconfig`-Dateien Token hinzufügen, um gerätespezifische Informationen hinzuzufügen. Sie können beispielsweise `Serial Number: {{serialnumber}}` zu Ihrer Konfigurationsdatei hinzufügen, um die Seriennummer des Geräts anzuzeigen.

Informationen zum Erstellen eines benutzerdefinierten Profils finden Sie unter [Benutzerdefinierte iOS-Einstellungen](../configuration/custom-settings-ios.md) oder [Benutzerdefinierte macOS-Einstellungen](../configuration/custom-settings-macos.md).

Gilt für:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Neuer Konfigurations-Designer beim Erstellen eines OEMConfig-Profils für Android Enterprise<!-- 3712769   -->
In Intune können Sie ein Gerätekonfigurationsprofil erstellen, das eine OEMConfig-App verwendet (Gerätekonfiguration > Profile > Profil erstellen > Android Enterprise (Plattform) > OEMConfig (Profiltyp)). Dadurch öffnet sich ein JSON-Editor mit einer Vorlage und Werten, die Sie ändern können. 

Dieses Update enthält einen Konfigurations-Designer mit verbesserter Benutzerfreundlichkeit, der in die App eingebettete Details wie Titel, Beschreibungen und mehr anzeigt. Der JSON-Editor ist weiterhin verfügbar und zeigt alle Änderungen an, die Sie im Konfigurations-Designer vornehmen.

Informationen zu den aktuellen Einstellungen finden Sie unter [Verwenden und Verwalten von Android Enterprise-Geräten mit OEMConfig](../configuration/android-oem-configuration-overview.md).

Gilt für: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Aktualisierte Benutzeroberfläche für die Konfiguration von Windows Hello<!-- 4089576            -->
Wir haben die Konsole aktualisiert, in der Sie [Intune für die Verwendung von Windows Hello for Business konfigurieren](../protect/windows-hello.md). Alle Konfigurationseinstellungen sind nun im gleichen Bereich der Konsole verfügbar, in dem Sie die Unterstützung für Windows Hello aktivieren.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Das Intune PowerShell SDK, das die Intune-API über Microsoft Graph unterstützt, wurde auf Version 6.1907.1.0 aktualisiert. Das SDK unterstützt jetzt folgende Optionen:
- Arbeitet mit Azure Automation.
- Unterstützt Lesevorgänge, die nur für die Anwendungsauthentifizierung gelten. 
- Unterstützt benutzerfreundliche verkürzte Namen als Aliase.
- Entspricht den PowerShell-Benennungskonventionen. Insbesondere wurde der Parameter `PSCredential` (im Cmdlet `Connect-MSGraph`) in `Credential` umbenannt.
- Unterstützt die manuelle Angabe des Wertes des Headers `Content-Type` bei Verwendung des Cmdlets `Invoke-MSGraphRequest`.

Weitere Informationen finden Sie unter [PowerShell SDK für Microsoft Intune Graph-API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Updates für Registrierungseinschränkungen<!-- 2871968 -->
Die Registrierungseinschränkungen für neue Mandanten wurden aktualisiert, sodass Android Enterprise-Arbeitsprofile standardmäßig zulässig sind. Für vorhandene Mandanten ergeben sich keine Änderungen. Um die Arbeitsprofile von Android Enterprise verwenden zu können, müssen Sie Ihr [Intune-Konto noch mit Ihrem verwalteten Google Play-Konto verbinden](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Aktualisierungen der Benutzeroberfläche für die Apple-Registrierung und Registrierungseinschränkungen<!--4089575, 4089579  -->
Die beiden folgenden Prozesse verwenden eine Benutzeroberfläche im Assistentenstil:
- Apple-Geräteregistrierung. Weitere Informationen finden Sie unter [Automatisches Registrieren von iOS-Geräten mit dem Programm zur Geräteregistrierung von Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Erstellung einer Registrierungseinschränkung. Weitere Informationen finden Sie unter [Festlegen von Registrierungseinschränkungen](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Behandeln von Vorkonfigurationen von Unternehmensgerätebezeichern für Android Q-Geräte<!-- 4711509  idmiss -->
In Android Q (v10) entfernt Google die Möglichkeit für MDM-Agents auf älteren verwalteten (Geräteadministrator) Android-Geräten, um Informationen zum Gerätebezeichner zu erfassen.  Intune bietet ein Feature, mit dem IT-Administratoren eine [Liste von Geräteseriennummern oder IMEIs vorkonfigurieren können](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number), um diese Geräte automatisch als unternehmenseigen zu kennzeichnen. Dieses Feature funktioniert nicht für Android Q-Geräte, die vom Geräteadministrator verwaltet werden.  Unabhängig davon, ob die Seriennummer oder die IMEI für das Gerät hochgeladen wird, wird sie bei der Intune-Anmeldung immer als persönlich betrachtet.  Sie können die Angaben zum Besitzer nach der Registrierung manuell auf das Unternehmen umstellen.  Dies betrifft nur neue Registrierungen, bestehende registrierte Geräte sind nicht betroffen.  Android-Geräte, die mit Arbeitsprofilen verwaltet werden, sind von dieser Änderung nicht betroffen und arbeiten weiterhin wie bisher.  Darüber hinaus können Android Q-Geräte, die als Geräteadministrator registriert sind, die Seriennummer oder IMEI in der Intune-Konsole nicht mehr als Geräteeigenschaften melden.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Die Symbole für Android Enterprise-Registrierungen haben sich geändert (Arbeitsprofil, dedizierte Geräte sowie vollständig verwaltete Geräte).<!-- 4977730 -->
Die Symbole für Android Enterprise-Registrierungsprofile wurden geändert. Zum Anzeigen der neuen Symbole gehen Sie zu **Intune** > **Registrierungen** > **Android-Registrierungen** > **Registrierungsprofile**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Änderung bezüglich der Windows-Diagnosedatensammlung<!-- 4113859 -->
Der Standardwert für die Diagnosedatensammlung hat sich für Geräte mit Windows 10, Version 1903 und höher, geändert. Ab Windows 10 Version 1903 ist die Sammlung von Diagnosedaten standardmäßig aktiviert. Windows-Diagnosedaten sind wichtige technische Daten von Windows-Geräten über das Gerät und die Funktionsweise von Windows und der zugehörigen Software. Weitere Informationen finden Sie unter [Konfigurieren von Windows-Diagnosedaten in Ihrer Organisation](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization). Autopilotgeräte verwenden auch in die „Vollständige“ Telemetrie, sofern im Autopilotprofil mit [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) nichts anderes festgelegt ist.

### <a name="device-management"></a>Geräteverwaltung

#### <a name="improve-device-location---3855417----"></a>Gerätestandort verbessern<!-- 3855417  -->
Mithilfe der Aktion **Gerät suchen** können Sie die exakten Koordinaten eines Geräts vergrößern. Weitere Informationen zum Auffinden verlorener IOS-Geräte finden Sie unter [Suchen von verlorenen iOS-Geräten](../remote-actions/device-locate.md).

### <a name="device-security"></a>Gerätesicherheit

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Erweiterte Einstellungen für Windows Defender-Firewall (öffentliche Vorschauversion)<!--  1311949     -->  
Verwenden Sie Intune, um [benutzerdefinierte Firewallregeln als Teil eines Gerätekonfigurationsprofils](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) für Endpoint Protection unter Windows 10 zu verwalten. Regeln können das Eingangs- und Ausgangsverhalten von Anwendungen, Netzwerkadressen und Ports festlegen. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Aktualisierte Benutzeroberfläche für die Verwaltung von Sicherheitsbaselines<!-- 4091125     -->
Wir haben die [Erstellung und Bearbeitung](../protect/security-baselines.md#create-the-profile) in der Intune-Konsole für unsere Sicherheitsbaselines aktualisiert. Die Änderungen umfassen:

Ein einfacheres Format im Assistentenstil, das zu einem einzigen Blatt zusammengefasst wurde. Dank dieses neuen Designs müssen IT-Experten nicht mehr auf mehreren Blättern arbeiten und einen Drilldown in mehrere separate Bereiche ausführen.  
Sie können nun Zuweisungen als Teil des Erstellungs- und Bearbeitungsprozesses erstellen, anstatt später zurückkehren zu müssen, um Baselines zuzuweisen. Wir haben eine Zusammenfassung der Einstellungen hinzugefügt, die Sie vor der Erstellung einer neuen Baseline und bei der Bearbeitung einer bestehenden anzeigen können. Beim Bearbeiten zeigt die Zusammenfassung nur die Liste der Elemente an, die in der einen Kategorie der zu bearbeitenden Eigenschaften festgelegt sind.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Woche vom 15. Juli 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Symbole für „Managed Home Screen“ und verwaltete Einstellungen<!-- 4918107 -->
Das Symbol für die App „Managed Home Screen“ und für die **verwalteten Einstellungen** wurde aktualisiert. Die App „Managed Home Screen“ wird nur von Geräten verwendet, die bei Intune als dedizierte Android Enterprise-Geräte (AE) registriert sind und im Kioskmodus mit mehreren Apps ausgeführt werden. Weitere Informationen über die App „Managed Home Screen“ finden Sie unter [Konfigurieren der Managed Home Screen-App von Microsoft für Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Device Policy auf dedizierten Android Enterprise-Geräten<!-- 4918136 -->
Die Android Device Policy-Anwendung kann über den Debugbildschirm der App „Managed Home Screen“ aufgerufen werden. Die App „Managed Home Screen“ wird nur von Geräten verwendet, die bei Intune als dedizierte Android Enterprise-Geräte (AE) registriert sind und im Kioskmodus mit mehreren Apps ausgeführt werden. Weitere Informationen finden Sie unter [Konfigurieren der Managed Home Screen-App von Microsoft für Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>Aktualisierungen des iOS-Unternehmensportals<!-- 3902931 -->
Ihr Unternehmensname in den Verwaltungsaufforderungen der iOS-App ersetzt den aktuellen Text „i.manage.microsoft.com“. Beispielsweise sehen Benutzer ihren Unternehmensnamen anstelle von „i.manage.microsoft.com“, wenn sie versuchen, eine iOS-App aus dem Unternehmensportal zu installieren, oder wenn sie die Verwaltung der App erlauben. Diese Neuerung wird in den nächsten Tagen für alle Kunden eingeführt.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Verwalten von FileVault für macOS<!--  3858502 + 4557986 + 1210104  -->
Mit Intune können Sie die [FileVault-Verschlüsselung für MacOS-Geräte verwalten](../protect/encrypt-devices.md). Zum Verschlüsseln von Geräten verwenden Sie ein Profil für die Endpoint Protection-Gerätekonfiguration.

Unsere Unterstützung für FileVault umfasst die Verschlüsselung unverschlüsselter Geräte, das Hinterlegen eines persönlichen Wiederherstellungsschlüssels, die automatische oder manuelle Rotation von persönlichen Verschlüsselungsschlüsseln und das Abrufen von Schlüsseln für Ihre Unternehmensgeräte. Endbenutzer können auch die Website des Unternehmensportals nutzen, um den persönlichen Wiederherstellungsschlüssel für ihre verschlüsselten Geräte zu erhalten.

Wir haben den Verschlüsselungsbericht neben Informationen zu BitLocker auch mit [Informationen zu FileVault](../protect/encryption-monitor.md) ergänzt, sodass Sie alle Verschlüsselungsdetails Ihrer Geräte zentral anzeigen können.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Die Windows Autopilot-Zurücksetzung entfernt den primären Benutzer des Geräts<!-- 4156123 -->
Bei der Verwendung der Autopilot-Zurücksetzung auf einem Gerät, wird dessen primäre Benutzer entfernt. Der nächste Benutzer, der sich nach dem Zurücksetzen anmeldet, wird als primärer Benutzer festgelegt. Dieses Feature wird in den nächsten Tagen für alle Kunden eingeführt.

## <a name="week-of-july-8-2019"></a>Woche vom 8. Juli 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Neue Office-, Windows- und OneDrive-Einstellungen in administrativen Vorlagen für Windows 10 <!-- 3510695 -->

Sie können in Intune Verwaltungsvorlagen erstellen, die die Gruppenrichtlinienverwaltung vor Ort nachahmen (**Geräteverwaltung** > **Profile** > **Profil** > **Windows 10 und höher** (Plattform) > **Administrationsvorlage** (Profiltyp)).

Dieses Update enthält weitere Office-, Windows- und OneDrive-Einstellungen, die Sie Ihren Vorlagen hinzufügen können. hinzufügen können. Mit diesen neuen Einstellungen können Sie jetzt über 2.500 Einstellungen konfigurieren, die zu vollständig cloudbasiert sind.

Weitere Informationen zu diesem Feature finden Sie unter [Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Microsoft Intune](../configuration/administrative-templates-windows.md).

Gilt für: Windows 10 und höher

## <a name="week-of-july-1-2019"></a>Woche vom 1. Juli 2019 

### <a name="app-management"></a>App-Verwaltung

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD und APP auf Android Enterprise-Geräten<!-- 3574267 -->
Beim Onboarding vollständig verwalteter Android Enterprise-Geräte registrieren sich Benutzer jetzt bei der ersten Einrichtung Ihres neuen oder auf Werkseinstellungen zurückgesetzten Geräts bei Azure Active Directory (AAD). Bisher musste der Benutzer bei einem vollständig verwalteten Gerät nach Abschluss der Einrichtung die Microsoft Intune-App manuell starten, um die AAD-Registrierung zu beginnen. Wenn der Benutzer jetzt nach der ersten Einrichtung zur Startseite des Geräts gelangt, ist das Gerät sowohl registriert als auch angemeldet.

Zusätzlich zu den AAD-Updates werden die Intune-App-Schutzrichtlinien (APP) jetzt auf vollständig verwalteten Android-Unternehmensgeräten unterstützt. Diese Funktionalität wird mit dem Rollout verfügbar. Weitere Informationen finden Sie unter [Hinzufügen von verwalteten Google Play-Apps für Android Enterprise-Geräte mit Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019-1906-service-release"></a>Woche vom 24. Juni 2019 (1906 Dienstrelease)

### <a name="app-management"></a>App-Verwaltung

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Konfigurieren, welche Browser zu Unternehmensdaten verlinken dürfen<!-- 3145939 -->
Intune-Schutzrichtlinien für Apps für Android- und iOS-Geräte ermöglichen Ihnen jetzt die Übertragung von Unternehmensweblinks an einen spezifischen anderen Browser als Intune Managed Browser oder Microsoft Edge.  Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>Die Seite „Alle Apps“ zeige Online-/Offline-Apps aus dem Microsoft Store für Unternehmen an<!--4089647 -->
Die Seite **Alle Apps** enthält nun eine Kennzeichnung, um Anwendungen im Microsoft Store für Unternehmen (MSFB) als Online- oder Offlineanwendungen zu identifizieren. Jede MSFB-App erhält jetzt ein Suffix für **Online** oder **Offline**. Die App-Detailseite enthält auch Informationen zu **Lizenztyp** und **Unterstützung der Gerätekontextinstallation** (nur offline lizenzierte Apps).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Unternehmensportal-App auf freigegebenen Windows-Geräten<!--4393553 -->
Benutzer können nun auf freigegebenen Windows-Geräten auf die Unternehmensportal-App zugreifen. Den Endbenutzern wird auf der Gerätekachel jetzt die Kennzeichnung **Freigegeben** angezeigt. Dies gilt für die Windows-Unternehmensportal-App Version 10.3.45609.0 und höher.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Anzeigen aller installierten Apps auf der neuen Unternehmensportal-Webseite<!-- 4224326 -->
Auf der neuen Seite **Installierte Apps** der Unternehmensportalwebsite werden alle verwalteten Apps (sowohl erforderliche als auch verfügbare) aufgeführt, die auf den Geräten eines Benutzers installiert sind. Neben dem Zuweisungstyp können Benutzer auch den Herausgeber, das Veröffentlichungsdatum und den aktuellen Installationsstatus der Apps sehen. Wenn Sie keine Apps für Ihre Benutzer als erforderlich oder verfügbar eingerichtet haben, erhalten sie die Meldung, dass keine Unternehmens-Apps installiert wurden. Die neue Webseite finden Sie, indem Sie die [Unternehmensportalwebsite](https://portal.manage.microsoft.com) aufrufen und auf **Installierte Apps** klicken.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>Mit der neuen Ansicht können Benutzer alle verwalteten Apps sehen, die auf einem Gerät installiert sind<!-- 2352913 -->  
In der Unternehmensportal-App für Windows werden nun alle verwalteten (sowohl erforderlichen als auch verfügbaren) Apps aufgelistet, die auf dem Gerät eines Benutzers installiert sind. Benutzer können versuchte und ausstehende App-Installationen sowie deren aktuellen Status einsehen. Wenn Sie keine Apps für Ihre Benutzer als erforderlich oder verfügbar eingerichtet haben, erhalten sie die Meldung, dass keine Unternehmens-Apps installiert wurden. Die neue Ansicht finden Sie im Navigationsbereich des Unternehmensportals unter **Apps** > **Installierte Apps**.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Konfigurieren von Einstellungen für Kernelerweiterungen auf macOS-Geräten<!-- 2043024 -->
Sie können auf macOS-Geräten ein Gerätekonfigurationsprofil erstellen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** (Plattform)). Dieses Update enthält weitere Einstellungen, die Sie zum Konfigurieren und Verwenden von Kernelerweiterungen auf Ihren Geräten verwenden können. Sie können bestimmte Erweiterungen hinzufügen oder alle Erweiterungen von einem bestimmten Partner oder Entwickler zulassen.

Weitere Informationen zu diesem Feature finden Sie in der [Übersicht zu Kernelerweiterungen](../configuration/kernel-extensions-overview-macos.md) und in den [Einstellungen für die Kernelerweiterung](../configuration/kernel-extensions-settings-macos.md).

Gilt für: macOS 10.13.2 und höher

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Weitere Konfigurationsoptionen für die Einstellung „Apps from the store only“ (Nur Apps aus dem Store) für Windows 10-Geräte<!-- 2697002 -->
Wenn Sie ein Geräteeinschränkungsprofil für Windows-Geräte erstellen, können Sie die Einstellung **Apps from the store only** (Nur Apps aus dem Store) verwenden, damit Benutzer nur Apps aus dem Microsoft Store installieren können (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Diese Einstellung wird in diesem Update mit weiteren Optionen erweitert.

Die neuen Einstellungen finden Sie unter [Einstellungen für Windows 10-Geräte (und höher) zum Zulassen oder Einschränken von Features mit Intune](../configuration/device-restrictions-windows-10.md#app-store).

Gilt für: Windows 10 und höher

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Bereitstellen mehrerer Zebra Mobility Extensions-Geräteprofile für ein Gerät, für dieselbe Benutzergruppe oder dieselbe Gerätegruppe<!-- 4089955 -->
Sie können Zebra Mobility Extensions (MX) in einem Gerätekonfigurationsprofil in Intune verwenden, um für Zebra-Geräte Einstellungen anzupassen, die nicht in Intune integriert sind. Derzeit können Sie ein Profil für ein einzelnes Gerät bereitstellen. In diesem Update können Sie mehrere Profile für Folgendes bereitstellen:
- für dieselbe Benutzergruppe
- für dieselbe Gerätegruppe
- für ein einzelnes Gerät

Unter [Nutzen und Verwalten von Zebra-Geräten mithilfe von Zebra Mobility Extensions in Microsoft Intune](../configuration/android-zebra-mx-overview.md) wird die Verwendung von MX in Intune veranschaulicht.

Gilt für: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Für einige Kioskeinstellungen auf iOS-Geräten wird „Blockieren“ anstelle von „Zulassen“ verwendet.<!-- 4404075  -->
Beim Erstellen eines Geräteeinschränkungsprofils für iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Kiosk**) legen Sie die **Automatische Sperre**, den **Ruftonschalter**, die **Automatische Ausrichtung**, die **Standbytaste** und die **Lautstärkeregler** fest.

Diese Werte sind in diesem Update **Blockieren** (blockiert das Feature) und **Nicht konfiguriert** (lässt das Feature zu). Die Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md#kiosk).

Gilt für: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Verwenden von Face ID für die Kennwortauthentifizierung auf iOS-Geräten<!-- 4490704 -->
Wenn Sie ein Geräteeinschränkungsprofil für iOS-Geräte erstellen, können Sie einen Fingerabdruck als Kennwort verwenden. In einem Update ermöglichen die Fingerabdruck-Kennworteinstellungen auch die Gesichtserkennung (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Kennwort**). Aus diesem Grund wurden die folgenden Einstellungen geändert:

- **Entsperrung durch Fingerabdruck** heißt nun **Touch ID und Face ID entsperren**.
- **Fingerabdruckänderung (nur überwacht)** heißt nun **Touch ID- und Face ID-Änderungen (nur überwacht)** .

Face ID ist ab iOS 11.0 verfügbar. Die Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md#password).

Gilt für: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>Einschränken von Spiele- und App Store-Features auf iOS-Geräten ist jetzt von der Bewertungsregion abhängig<!-- 4593948 -->
Auf iOS-Geräten können Sie Features mit Bezug zu Spielen, dem App Store und dem Anzeigen von Dokumenten zulassen oder einschränken (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **App Store, Dokumentanzeige, Spiele**). Sie können außerdem die Bewertungsregion auswählen, z. B. USA.

In diesem Update ist das Feature **Apps** der **Bewertungsregion** untergeordnet und von der **Bewertungsregion** abhängig. Die Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gilt für: iOS

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Windows Autopilot-Unterstützung für Azure AD Hybrid Join<!-- 4809146-->
Windows Autopilot für vorhandene Geräte unterstützt jetzt Azure AD Hybrid Join (zusätzlich zur vorhandenen Azure AD Join-Unterstützung). Gilt für Geräte mit Windows 10, Version 1809 und höher. Weitere Informationen finden Sie unter [Windows Autopilot für vorhandene Geräte](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Geräteverwaltung

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Anzeigen der Sicherheitspatchebene von Android-Geräten<!-- 4461911 -->
Sie können jetzt die Sicherheitspatchebene von Android-Geräten anzeigen. Klicken Sie hierzu auf **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie dann auf **Hardware**.
Die Patchebene ist im Abschnitt **Betriebssystem** aufgeführt.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Zuweisen von Bereichsmarkierungen zu allen verwalteten Geräten in einer Sicherheitsgruppe<!-- 3173810 -->
Sie können jetzt einer Sicherheitsgruppe Bereichsmarkierungen zuweisen. Die Bereichsmarkierungen werden allen Geräten in dieser Sicherheitsgruppe zugewiesen. Die Bereichsmarkierung wird allen Geräten in diesen Gruppen zugewiesen. Bereichsmarkierungen, die mit diesem Feature festgelegt werden, überschreiben die Bereichsmarkierungen, die mit der aktuellen Vorgehensweise zugewiesen wurden. Weitere Informationen finden Sie unter [Verwenden der RBAC und von Bereichsmarkierungen für eine verteilte IT](scope-tags.md).

### <a name="device-security"></a>Gerätesicherheit

#### <a name="use-keyword-search-with-security-baselines------"></a>Verwenden der Schlüsselwortsuche mit Sicherheitsbaselines<!--  -->
Wenn Sie [Sicherheitsbaselineprofile](../protect/security-baselines.md#create-the-profile) erstellen oder bearbeiten, können Sie in der neuen *Suchleiste* Schlüsselwörter angeben, um die verfügbaren Einstellungsgruppen nach denen zu filtern, die Ihre Suchkriterien enthalten.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>Das Sicherheitsbaselinefeatures ist jetzt allgemein verfügbar<!-- 3785395 -->
Die Vorschauphase des **Sicherheitsbaselinefeatures** ist vorbei. Das Feature ist jetzt allgemein verfügbar (GA).  Dies bedeutet, dass das Feature jetzt in der Produktion eingesetzt werden kann. Die einzelnen Basislinienvorlagen können jedoch in der Vorschauphase verbleiben und werden ausgewertet und nach eigenen Zeitplänen an die allgemeine Verfügbarkeit freigegeben.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>Die MDM-Sicherheitsbaselinevorlage ist jetzt allgemein verfügbar<!-- 3794072, 4217151,  3534649 -->
Die Vorschauphase der MDM-Sicherheitsbaselinevorlage ist vorbei. Das Feature ist jetzt allgemein verfügbar (GA). Die GA-Vorlage ist mit **MDM-Sicherheitsbaseline für Mai 2019** gekennzeichnet.  Dies ist eine neue Vorlage und kein Upgrade der Vorschauversion.  Da es sich um eine neue Vorlage handelt, müssen Sie die [darin enthaltenen Einstellungen](../protect/security-baseline-settings-mdm.md) überprüfen und dann neue Profile erstellen, um die Vorlage auf Ihrem Gerät bereitzustellen. Andere Sicherheitsbaselinevorlagen können in der Vorschau verbleiben. Eine Liste der verfügbaren Baselines finden Sie unter [Verfügbare Sicherheitsbaselines](../protect/security-baselines.md#available-security-baselines).  

Die Vorlage *MDM-Sicherheitsbaseline für Mai 2019* ist nicht nur eine neue Vorlage, sondern enthält auch die beiden Einstellungen, die wir kürzlich in unserem Artikel „In Entwicklung“ angekündigt haben:  
- Sperrbildschirm: Per Sprache zu aktivierende App über einen Sperrbildschirm  
- DeviceGuard: Verwendet die virtualisierungsbasierte Sicherheit (VBS) beim nächsten Neustart von Geräten.  

Die *MDM-Sicherheitsbaseline für Mai 2019* beinhaltet auch mehrere neue Einstellungen, einige Einstellungen wurden entfernt und der Standardwert einer Einstellung wurde überarbeitet. Eine detaillierte Liste der Änderungen von Vorschau zu GA finden Sie unter **Was hat sich in der neuen Vorlage geändert?** .

#### <a name="security-baseline-versioning---3194322---"></a>Versionsverwaltung für Sicherheitsbaselines<!-- 3194322 -->
Sicherheitsbaselines für die Intune-Unterstützung der Versionsverwaltung. Mit dieser Unterstützung können Sie Ihre bestehenden Sicherheitsbaselineprofile aktualisieren, um die neuere Baselineversion zu verwenden, ohne eine neue Baseline von Grund auf neu erstellen und bereitstellen zu müssen, sobald neue Versionen der jeweiligen Sicherheitsbaseline veröffentlicht werden. Darüber hinaus können Sie in der Intune-Konsole Informationen über jede Baseline anzeigen, wie z.B. die Anzahl der einzelnen Profile, die die Baseline verwenden, wie viele der verschiedenen Baselineversionen von Ihren Profilen verwendet werden und wann die neueste Version einer bestimmten Sicherheitsbaseline veröffentlicht wurde.  Weitere Informationen finden Sie unter **Sicherheitsbaselines**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>Die Einstellung „Sicherheitsschlüssel zur Anmeldung verwenden“ wurde verschoben<!-- 4501151 -->
Die Gerätekonfigurationseinstellung für Identity Protection mit dem Namen **Sicherheitsschlüssel zur Anmeldung verwenden** ist keine Untereinstellung mehr von *Windows Hello for Business konfigurieren*. Es handelt sich nun um eine Einstellung auf oberster Ebene, die immer verfügbar ist, auch wenn Sie die Verwendung von Windows Hello for Business nicht aktivieren. Weitere Informationen finden Sie unter [Identity Protection](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Neue Berechtigungen für zugewiesene Gruppenadministratoren<!-- 4504437   -->
Die in Intune integrierte Rolle des Schuladministrators verfügt nun über CRUD-Berechtigungen (Create, Read, Update und Delete [Erstellen, Lesen, Aktualisieren und Löschen]) für verwaltete Apps. Dieses Update bedeutet, dass Sie, wenn Sie in Intune for Education als Gruppenadministrator zugewiesen sind, nun das iOS-MDM-Push-Zertifikat, die iOS-MDM-Servertoken und die iOS-VPP-Token zusammen mit [allen vorhandenen Berechtigungen](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions) erstellen, anzeigen, aktualisieren und löschen können. Um eine dieser Aktionen durchzuführen, gehen Sie zu **Mandanteneinstellungen** > **iOS-Geräteverwaltung**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Anwendungen können die Graph-API verwenden, um Lesevorgänge ohne Benutzeranmeldeinformationen aufzurufen<!-- 4655885 -->
Anwendungen können Lesevorgänge der Intune-Graph-API mithilfe der App-Identität ohne Benutzeranmeldeinformationen aufrufen. Weitere Informationen zum Zugriff auf die Microsoft Graph-API für Intune finden Sie unter [Arbeiten mit Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Anwenden von Bereichsmarkierungen für Apps aus dem Microsoft Store für Unternehmen<!-- 4392555 -->
Sie können jetzt Bereichsmarkierungen für Apps aus dem Microsoft Store für Unternehmen anwenden. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Verwenden der rollenbasierten Zugriffssteuerung (RBAC) und Bereichsmarkierungen für verteilte IT](scope-tags.md).

## <a name="week-of-june-17-2019"></a>Woche vom 17. Juni 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="new-features-in-microsoft-intune-app"></a>Neue Features in der Microsoft Intune-App
Der Microsoft Intune-App (Preview) für Android wurden neue Features hinzugefügt. Benutzer mit vollständig verwalteten Android-Geräten haben jetzt folgende Möglichkeiten:  

* Sie können die Geräte anzeigen und verwalten, die sie über das Intune-Unternehmensportal oder die Microsoft Intune-App registriert haben.
* Sie können sich an ihre Organisation wenden, um Unterstützung zu erhalten.
* Sie können Feedback an Microsoft senden.
* Sie können Geschäftsbedingungen anzeigen, sofern diese von ihrer Organisation festgelegt wurden.

## <a name="week-of-june-10-2019"></a>Woche ab 10. Juni 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Neue Beispiel-Apps für die Intune SDK-Integration auf GitHub verfügbar<!-- 2653471 -->
Dem GitHub-Konto „msintuneappsdk“ wurden neue Beispielanwendungen für iOS (Swift), Android, Xamarin.iOS, Xamarin Forms und Xamarin.Android hinzugefügt. Diese Apps dienen zur Ergänzung unserer vorhandenen Dokumentation und veranschaulichen die Integration des SDK für die Intune-App in Ihre eigenen mobilen Apps. Wenn Sie App-Entwickler sind und weitere Unterstützung für das Intune SDK benötigen, sehen Sie sich die folgenden verknüpften Beispiele an:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): Eine native iOS-App (Swift) für Chats, die die Azure Active Directory-Authentifizierungsbibliothek (ADAL) für die vermittelte Authentifizierung verwendet.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): Eine native Android-App für Aufgabenlisten, die die ADAL für die vermittelte Authentifizierung verwendet.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): Eine Xamarin.Android-App für Aufgabenlisten, die die ADAL für die vermittelte Authentifizierung verwendet. Dieses Repository enthält auch die Xamarin.Forms-App.
- [Xamarin.iOS-Beispiel-App](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): Eine Barebone-Beispiel-App für Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Woche vom 27. Mai 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Berichterstellung über potenziell schädlichen Apps auf Android-Geräten<!-- 4223162 -->
Intune stellt jetzt zusätzliche Berichterstellungsinformationen über potenziell schädliche Apps auf Android-Geräten bereit. 

## <a name="week-of-may-20-2019"></a>Woche vom 20. Mai 2019

### <a name="app-management"></a>App-Verwaltung

#### <a name="windows-company-portal-app---3316993---"></a>Windows-Unternehmensportal-App<!-- 3316993 -->
Die Windows-Unternehmensportal-App enthält jetzt die neue Seite **Geräte**. Auf der Seite **Geräte** werden den Endbenutzern alle ihre registrierten Geräte angezeigt. Benutzer sehen diese Änderung im Unternehmensportal, wenn sie Version 10.3.4291.0 und höher verwenden. Informationen zum Konfigurieren des Unternehmensportals finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot-Gerät – Attributname „OrderID“ in „Gruppentag“ geändert <!-- 4659453 -->

Um die Aussagekraft zu erhöhen, wurde der Attributname **OrderID** bei Autopilot-Geräten in **Gruppentag** geändert. Wenn Sie Autopilot-Geräteinformationen über freigegebene Clustervolumen (CSVs) hochladen, müssen Sie „Gruppentag“ (und nicht „OrderID“) als Spaltenüberschrift verwenden.  

## <a name="week-of-may-13-2019-1905-service-release"></a>Woche vom 13. Mai 2019 (1905 Dienstrelease)

### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App<!-- 1927359  -->
Bei Geräten, die bereits mithilfe des Setup-Assistenten über eine der Methoden von Apple für die Registrierung von Unternehmensgeräten registriert wurden, unterstützt Intune das Unternehmensportal nicht mehr, wenn es manuell von Endbenutzern aus dem App-Store installiert wurde. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Wenn Benutzer die Unternehmensportal-App aus dem App Store installieren und dann versuchen, diese Geräte darüber zu registrieren, erhalten sie eine Fehlermeldung. Es wird vorausgesetzt, dass diese Geräte die Unternehmensportal-App nur dann verwenden, wenn sie während der Registrierung von Intune mithilfe von Push automatisch übertragen wird. Registrierungsprofile in Intune im Azure-Portal werden aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Wenn Sie wünschen, dass Ihre DEP-Gerätebenutzer die Unternehmensportal-App verwenden, müssen Sie Ihre Einstellungen in einem Registrierungsprofil angeben. 

Darüber hinaus wird der Bildschirm **Gerät identifizieren** im iOS-Unternehmensportal entfernt. Deshalb müssen Administratoren, die den bedingten Zugriff aktivieren oder Unternehmens-Apps bereitstellen möchten, das DEP-Registrierungsprofil aktualisieren. Diese Anforderung gilt nur, wenn die DEP-Registrierung mit dem Setup-Assistenten authentifiziert wird. In diesem Fall müssen Sie die Unternehmensportal-App mithilfe von Push auf das Gerät übertragen. Wählen Sie dazu **Intune** > **Geräteregistrierung** > **Apple-Registrierung** > **Registrierungsprogrammtoken** > anschließend ein Token > **Profile** > dann ein Profil und > **Eigenschaften** aus, und > legen Sie für **Unternehmensportal installieren** den Wert **Ja** fest.

Um die Unternehmensportal-App auf bereits registrierten DEP-Geräten zu installieren, müssen Sie zu „Intune“ > „Client-Apps“ wechseln und sie als verwaltete App mit App-Konfigurationsrichtlinien mithilfe von Push übertragen. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Konfigurieren, wie Endbenutzer eine LOB-App mithilfe einer App-Schutzrichtlinie aktualisieren können<!-- 3568384 -->
Sie können jetzt konfigurieren, wo Ihre Endbenutzer eine aktualisierte Version einer LOB-App (Line-of-Business-App, branchenspezifische App) erhalten können. Endbenutzer sehen diese Funktion im bedingten Startdialogfeld **App-Mindestversion**, in dem der Benutzer aufgefordert wird, auf eine Mindestversion der LOB-App zu aktualisieren. Sie müssen diese Updatedetails als Teil Ihrer LOB-App-Schutzrichtlinie (APP) angeben. Dieses Feature ist unter iOS und Android verfügbar. Unter iOS erfordert dieses Feature, dass die App integriert (oder mit dem Wrapping Tool umschlossen) und dafür das Intune SDK für iOS, V. 10.0.7 oder höher, verwendet wird. Unter Android wäre für dieses Feature die neueste Unternehmensportal-App erforderlich. Um zu konfigurieren, wie ein Endbenutzer eine LOB-App aktualisiert, muss eine verwaltete App-Konfigurationsrichtlinie mit dem Schlüssel `com.microsoft.intune.myappstore` an diese gesendet werden. Der gesendete Wert definiert, aus welchem Speicher der Endbenutzer die App herunterladen wird. Wenn die App über das Unternehmensportal bereitgestellt wird, muss der Wert `CompanyPortal` sein. Für alle anderen Speicher müssen Sie eine vollständige URL eingeben.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>PowerShell-Skripts zur Erweiterung der Intune-Verwaltung<!-- 3734186  -->
Sie können PowerShell-Skripts so konfigurieren, dass sie mit Administratorrechten des Benutzers auf dem Gerät ausgeführt werden. Weitere Informationen finden Sie unter [Verwenden von PowerShell-Skripts auf Windows 10-Geräten in Intune](../apps/intune-management-extension.md) und [Win32-App-Verwaltung](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Verwaltung von Android Enterprise-Apps<!-- 4459905 -->
Um IT-Administratoren die Konfiguration und Nutzung der Android Enterprise-Verwaltung zu erleichtern, fügt Intune der Intune-Verwaltungskonsole automatisch vier gängige Android Enterprise-bezogene Apps hinzu. Die vier Android Enterprise-Apps sind wie folgt:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** : für vollständig verwaltete Android Enterprise-Szenarien.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** : hilft bei der Anmeldung bei Ihren Konten, wenn Sie die zweistufige Überprüfung verwenden.
- **[Intune-Unternehmensportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** : wird für App Protection Policies (APP) und Szenarien mit Android Enterprise-Arbeitsprofilen genutzt.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) : wird für dedizierte/Kioskszenarien mit Android Enterprise verwendet.

Bisher mussten IT-Administratoren diese Apps im [verwalteten Google Play Store](https://play.google.com/store/apps) als Teil des Setups manuell auffinden und genehmigen. Durch diese Änderung entfallen diese bislang manuellen Schritte, sodass Kunden die Android Enterprise-Verwaltung einfacher und schneller nutzen können.

Administratoren werden feststellen, dass diese vier Apps automatisch zur Liste ihrer Intune-Apps hinzugefügt wurden, wenn sie ihren Intune-Mandanten zum ersten Mal mit dem verwaltetem Google Play Store verbinden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung zwischen Ihrem Intune-Konto und Ihrem verwalteten Google Play-Konto](../enrollment/connect-intune-android-enterprise.md). Für Mandanten, die ihren Mandanten bereits verbunden haben oder Android Enterprise bereits nutzen, gibt es keinerlei Administrationsaufwand. Diese vier Apps werden automatisch binnen 7 Tagen nach Abschluss des Dienstrollouts vom Mai 2019 verfügbar sein.

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>PFX-Zertifikatconnector für Microsoft Intune aktualisiert<!-- 1533038 -->
Wir haben ein Update zum [PFX-Zertifikatconnector für Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht, das ein Problem behebt, bei dem vorhandene PFX-Zertifikate weiter erneut verarbeitet werden. Dies führt dazu, dass der Connector die Verarbeitung neuer Anforderungen beendet.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Intune-Sicherheitsaufgaben für Defender ATP (in öffentlicher Vorschau)<!-- 3208597 -->
In der öffentlichen Vorschau können Sie Intune verwenden, um [Sicherheitsaufgaben für Microsoft Defender Advanced Threat Protection (ATP)](../protect/atp-manage-vulnerabilities.md) zu verwalten. Diese Integration in ATP bietet einen risikobasierten Ansatz zur Erkennung, Priorisierung und Behebung von Schwachstellen und Fehlkonfigurationen an Endpunkten, wobei gleichzeitig die Zeitspanne zwischen Ermittlung und Risikominderung verkürzt wird.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Prüfen nach einem TPM-Chipsatz in einer Windows 10-Gerätekonformitätsrichtlinie<!-- 3617671   idstaged-->
Viele Geräte unter Windows 10 und höher haben Chipsätze von Trusted Platform Module (TPM). Dieses Update enthält eine neue Konformitätseinstellung, die die Version des TPM-Chips auf dem Gerät überprüft.

Unter [Richtlinieneinstellungen für Windows 10 und höher](../protect/compliance-policy-create-windows.md#device-security) wird diese Einstellung beschrieben.

Gilt für: Windows 10 und höher

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Hindern von Endbenutzern am Ändern ihres privaten Hotspots und Deaktivieren der Siri-Serverprotokollierung auf iOS-Geräten<!-- 4097904   -->  
Sie können auf einem iOS-Gerät ein Geräteeinschränkungsprofil einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). Dieses Update umfasst neue Einstellungen, die Sie konfigurieren können:

- **Integrierte Apps**: Serverseitige Protokollierung für Siri-Befehle
- **Drahtlos**: Benutzeränderung des persönlichen Hotspots (nur überwacht)

Zum Anzeigen dieser Einstellungen wechseln Sie zu [built-in app settings for iOS](../configuration/device-restrictions-ios.md#built-in-apps) (Integrierte App-Einstellungen für iOS) und [wireless settings for iOS](../configuration/device-restrictions-ios.md#wireless) (Drahtloseinstellungen für iOS).

Gilt für: iOS 12.2 und höher

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Neue Geräteeinschränkungseinstellungen für Classroom-App für macOS-Geräte<!-- 4097905   --> 
Sie können für macOS-Geräte Gerätekonfigurationsprofile einrichten (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **macOS** als Plattform > **Geräteeinschränkungen** als Profiltyp). Dieses Update enthält neue Classroom-App-Einstellungen, die Option zum Sperren von Screenshots und die Option zum Deaktivieren der iCloud-Fotomediathek.

Die aktuellen Einstellungen finden Sie unter [macOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-macos.md).

Gilt für: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>Die iOS-Einstellung „Kennwort für Zugriff auf App Store“ wird umbenannt<!-- 4557891  -->
Die Einstellung **Kennwort für Zugriff auf App Store** wird umbenannt in **iTunes Store-Kennwort für alle Käufe erforderlich** (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für „Plattform“ > **Geräteeinschränkungen** für „Profiltyp“ > **App Store, Dokumentanzeige, Spiele**).

Zum Anzeigen der verfügbaren Einstellungen wechseln Sie zu [App Store, Dokumentanzeige, Spiele > iOS-Einstellungen](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Gilt für: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender Advanced Threat Protection-Baseline (Vorschauversion)<!--  3754134 -->
Wir haben eine Vorschauversion der Sicherheitsbaseline für [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md)-Einstellungen hinzugefügt. Diese Baseline ist verfügbar, wenn Ihre Umgebung den Anforderungen zur Verwendung von [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites) entspricht.

### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Statusseite für die Windows-Registrierung ist jetzt allgemein verfügbar<!-- 3605348 -->
Die Statusseite für die Registrierung ist jetzt in der Vorschauversion nicht mehr enthalten. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Update bei Intune-Benutzeroberfläche – Erstellung eines Autopilot-Registrierungsprofils<!-- 4593669 -->
Die Benutzeroberfläche zum Erstellen eines Autopilot-Registrierungsprofils wurde aktualisiert und an den Still der Azure-Benutzeroberflächen angepasst. Weitere Informationen finden Sie unter [Erstellen eines Autopilot-Registrierungsprofils](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Zukünftig werden weitere Intune-Szenarien auf diesen neuen Stil der Benutzeroberfläche aktualisiert.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>„Autopilot-Zurücksetzung aktivieren“ bei allen Windows-Geräten<!-- 4225665 -->
„Autopilot-Zurücksetzung aktivieren “ funktioniert jetzt bei allen Windows-Geräten – sogar denen, die nicht zur Verwendung der Statusseite für die Registrierung konfiguriert wurden. Wenn für ein Gerät bei der Erstregistrierung keine Statusseite für die Registrierung konfiguriert wurde, wechselt das Gerät nach der Anmeldung direkt zum Desktop. Es kann bis zu acht Stunden dauern, bis die Synchronisierung abgeschlossen ist und das Gerät in Intune als konform angezeigt wird. Weitere Informationen finden Sie unter [Reset devices with remote Windows Autopilot Reset (Zurücksetzen von Geräten mit Remote-Windows Autopilot-Zurücksetzung)](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Exaktes IMEI-Format beim Durchsuchen von „Alle Geräte“ nicht erforderlich<!--30407680 -->
Wenn Sie **Alle Geräte** durchsuchen, müssen Sie in IMEI-Nummern keine Leerzeichen einbeziehen.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Das Löschen eines Geräts im Apple-Portal wird im Intune-Portal widergespiegelt<!--2489996 -->
Wenn ein Gerät aus dem Programm zur Geräteregistrierung von Apple oder den Apple Business Manager-Portalen gelöscht wird, wird das Gerät bei der nächsten Synchronisierung automatisch aus Intune gelöscht.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>Die Nachverfolgung auf der Seite zum Registrierungsstatus umfasst jetzt Win32-Apps<!-- 2714451 -->
Dies gilt nur für Geräte mit Windows 10, Version 1903 und höher. Weitere Informationen finden Sie unter [Einrichten einer Statusseite für die Registrierung](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Geräteverwaltung

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Zurücksetzen von Geräten in einem Massenvorgang mithilfe der Graph-API<!-- 3295288 -->
Mithilfe der Graph-API können Sie jetzt in einem Massenvorgang bis zu 100 Geräte zurücksetzen.

### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>Der Verschlüsselungsbericht ist in der öffentlichen Vorschau nicht mehr enthalten<!-- 4587546      -->
Der [report for BitLocker and device encryption](../protect/encryption-monitor.md) (Bericht für BitLocker-Geräteverschlüsselung) ist jetzt allgemein verfügbar und nicht mehr Teil der öffentlichen Vorschau.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Outlook-Signatur und biometrische Einstellungen für iOS- und Android-Geräte<!-- 4050557 -->
Sie können jetzt angeben, ob die Standardsignatur in Outlook auf iOS- und Android-Geräten aktiviert ist. Darüber hinaus können Sie wählen, dass Benutzer die biometrische Einstellung in Outlook für iOS ändern dürfen.

## <a name="week-of-may-6-2019"></a>Woche vom 6. Mai 2019

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>NAC-Unterstützung (Network Access Control, Netzwerkzugriffssteuerung) für F5 Access für iOS-Geräte<!-- 4500808 -->

F5 hat ein Update zu BIG-IP 13 veröffentlicht, dass NAC-Funktionalität für F5 Access unter iOS in Intune ermöglicht. Zur Nutzung dieses Features ist Folgendes erforderlich:

- Aktualisieren Sie BIG-IP auf 13.1.1.5. BIG-IP 14 wird nicht unterstützt.
- Integrieren Sie BIG-IP für NAC in Intune. Lesen Sie dazu die Schritte in [Übersicht: Konfigurieren von APM für Gerätestatusüberprüfungen mit Endpunktverwaltungssystemen](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Überprüfen Sie die Einstellung **Netzwerkzugriffssteuerung (NAC) aktivieren** im VPN-Profil in Intune.

Die verfügbaren Einstellungen finden Sie unter [Configure VPN settings on iOS devices (Konfigurieren von VPN-Einstellungen auf iOS-Geräten)](../configuration/vpn-settings-ios.md).

Gilt für: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>PFX-Zertifikatconnector für Microsoft Intune aktualisiert<!-- doc-vso 1521237  -->  
Wir haben ein Update für den [PFX-Zertifikatconnector für Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) veröffentlicht, wodurch das Abrufintervall von 5 Minuten auf 30 Sekunden verkürzt wird.




## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
