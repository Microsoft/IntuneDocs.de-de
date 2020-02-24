---
title: Neues in Microsoft Intune – Azure | Microsoft-Dokumentation
titleSuffix: ''
description: Erfahren Sie, welche Neuerungen es im Intune-Azure-Portal gibt
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/07/2020
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
ms.openlocfilehash: 7018e2ab4290219c752f44b4b391822438461e8e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415084"
---
# <a name="whats-new-in-microsoft-intune"></a>Neuerungen in Microsoft Intune

Erfahren Sie jede Woche, welche Neuerungen Microsoft Intune zu bieten hat. Hier finden Sie auch [wichtige Hinweise](#notices), [frühere Releases](whats-new-archive.md) und Informationen zur [Veröffentlichung von Intune-Dienstupdates](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Bei jedem [monatlichen Update](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) kann das Rollout bis zu drei Tage dauern und erfolgt in dieser Reihenfolge:
>
> - 1\. Tag: Asien-Pazifik (APAC)
> - 2\. Tag: Europa, Naher Osten und Afrika (EMEA)
> - 3\. Tag: Nordamerika
> - 4\. Tag und später: Intune for Government
>
> Die Einführung einiger Funktionen dauert möglicherweise mehrere Wochen, sodass sie in der ersten Woche nicht für alle Kunden verfügbar sind.
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
## <a name="week-of-february-10-2020"></a>Woche des 10. Februar 2020

### <a name="windows-7-ends-extended-support---3042987--"></a>Ende des erweiterten Supports für Windows 7 <!--3042987-->
Der erweiterte Support für Windows 7 endete am 14. Januar 2020. Gleichzeitig wurde die Intune-Unterstützung für Geräte eingestellt, auf denen Windows 7 ausgeführt wird. Technische Unterstützung und automatische Updates zum Schutz Ihres PCs sind nicht mehr verfügbar. Führen Sie ein Upgrade auf Windows 10 durch. Weitere Informationen finden Sie im [Blogbeitrag zum Planen der Änderung](https://aka.ms/Windows7_Intune).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Hiermit wird Microsoft Edge, Version 77 und höher auf Windows 10-Geräten hinzugefügt.<!-- 5843584 -->
Intune unterstützt nun die Deinstallation der Microsoft Edge-Version 77 und später auf Windows 10-Geräten. Weitere Informationen finden Sie unter [Hinzufügen von Microsoft Edge für Windows 10 zu Microsoft Intune](~/apps/apps-windows-edge.md).

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Bildschirm aus dem Unternehmensportal bzw. der Android-Arbeitsprofilregistrierung entfernt<!--6103987 -->
Der Bildschirm **Wie geht es weiter?** wurde aus dem Registrierungsflow des Android-Arbeitsprofils im Unternehmensportal entfernt, um die Handhabung zu optimieren. Wechseln Sie zu [Registrieren mit dem Android-Arbeitsprofil](/intune-user-help/enroll-device-android-work-profile), um den aktualisierten Registrierungsflow für das Android-Arbeitsprofil anzuzeigen.  

#### <a name="company-portal-app-improved-performance---6178652---"></a>Verbesserte Leistung der Unternehmensportal-App<!-- 6178652 -->
Die Unternehmensportal-App wurde aktualisiert und unterstützt jetzt eine verbesserte Leistung für Geräte mit ARM64-Prozessoren, z. B. das Surface Pro X. Zuvor wurde das Unternehmensportal in einem emulierten ARM32-Modus betrieben. In Version 10.4.7080.0 und höher ist jetzt die Unternehmensportal-App nativ für ARM64 kompiliert. Weitere Informationen zur Unternehmensportal-App finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](~/apps/company-portal-app.md).

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>Woche ab 27. Januar 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>Intune-Unterstützung für einen zusätzlichen Bereitstellungskanal für macOS in Microsoft Edge-Version 77<!-- 5983950  -->
Microsoft Intune unterstützt jetzt den zusätzlichen Bereitstellungskanal **Stable** für die Microsoft Edge-App für macOS. Der **Stable Channel** wird für die umfassende Bereitstellung von Microsoft Edge in Unternehmensumgebungen empfohlen. Der Kanal wird alle sechs Wochen aktualisiert, und jedes Release umfasst Verbesserungen aus dem Kanal **Beta**. Zusätzlich zu den Kanälen **Stable** und **Beta** unterstützt Intune einen **Dev**-Kanal. Die öffentliche Vorschau bietet die Kanäle „Stable“ und „Dev“ für Microsoft Edge, Version 77 und höher, für macOS. Automatische Updates des Browsers sind automatisch aktiviert. Weitere Informationen finden Sie unter [Hinzufügen von Microsoft Edge zu macOS-Geräten mit Microsoft Intune](~/apps/apps-edge-macos.md).

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Außerbetriebnahme von Intune Managed Browser<!--5728447 -->
Der Intune Managed Browser wird eingestellt. Verwenden Sie Microsoft Edge für Ihre geschützte Intune-Browserumgebung. Weitere Informationen finden Sie unter [Maßnahme erforderlich: Verwenden von Microsoft Edge für Ihre geschützte Intune-Browserumgebung](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience) im Abschnitt [Hinweise](~/fundamentals/whats-new.md#notices) weiter unten.

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>Woche ab 20. Januar 2020 (Dienstrelease 2001)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Veränderte Benutzeroberfläche beim Hinzufügen von Apps zu Intune<!-- 4705829   -->
Zum Hinzufügen von Apps zu Intune steht Ihnen eine neue Benutzeroberfläche zur Verfügung. Auf dieser Oberfläche können Sie auf dieselben Einstellungen und Details wie bisher zugreifen, allerdings ähnelt der neue Prozess zum Hinzufügen einer App zu Intune eher einem Assistenten. Diese neue Oberfläche bietet auch eine Seite zum Überprüfen der Einstellungen, bevor die App hinzugefügt wird. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Option **Apps** > **Alle Apps** > **Hinzufügen** aus. Weitere Informationen finden Sie unter [Hinzufügen von Apps zu Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Obligatorischer Neustart von Win32-Apps <!-- 5622282   -->
Sie können festlegen, dass eine Win32-App nach einer erfolgreichen Installation neu gestartet werden muss. Darüber hinaus können die Zeitspanne auswählen, die vergehen darf, bevor der Neustart erfolgen muss (Karenzzeit).

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Änderung der Benutzeroberfläche beim Konfigurieren von Apps in Intune<!-- 4207990   -->
Beim Erstellen von App-Konfigurationsrichtlinien in Intune steht Ihnen jetzt eine neue Benutzeroberfläche zur Verfügung. Auf dieser Oberfläche können Sie auf dieselben Einstellungen und Details wie bisher zugreifen, allerdings ähnelt der neue Prozess zum Hinzufügen einer Richtlinie zu Intune eher einem Assistenten. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) die Optionen **Apps** > **App-Konfigurationsrichtlinien** > **Hinzufügen** aus. Weitere Informationen finden Sie unter [App-Konfigurationsrichtlinien für Microsoft Intune](~/apps/app-configuration-policies-overview.md). 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Intune-Unterstützung für einen zusätzlichen Bereitstellungskanal für Microsoft Edge für Windows 10<!-- 5861774 -->
Microsoft Intune unterstützt jetzt den zusätzlichen Bereitstellungskanal **Stable** für die Microsoft Edge-App (Version 77 und höher) für Windows 10. Der **Stable Channel** wird für die umfassende Bereitstellung von Microsoft Edge für Windows 10 in Unternehmensumgebungen empfohlen. Der Kanal wird alle sechs Wochen aktualisiert, und jedes Release umfasst Verbesserungen aus dem Kanal **Beta**. Zusätzlich zu den Kanälen **Stable** und **Beta** unterstützt Intune einen **Dev**-Kanal. Weitere Informationen finden Sie unter [Microsoft Edge für Windows 10 – Konfigurieren von App-Einstellungen](~/apps/apps-windows-edge.md#configure-app-settings).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Verbesserte Benutzeroberfläche beim Konfigurieren des lokalen Connectors von Exchange ActiveSync<!-- 5695492   -->
Wir haben die Benutzeroberfläche beim [Konfigurieren des lokalen Connectors von Exchange ActiveSync](../protect/exchange-connector-install.md) aktualisiert. Die aktualisierte Benutzeroberfläche bietet einen zentralen Bereich zum Konfigurieren, Bearbeiten und Zusammenfassen der Details zu Ihrem lokalen Connector. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Hinzufügen automatischer Proxyeinstellungen zu WLAN-Profilen für Android Enterprise-Arbeitsprofile<!-- 4490822   -->
Auf Geräten mit Android Enterprise-Arbeitsprofilen können Sie WLAN-Profile erstellen. Wenn Sie den Typ „Unternehmen“ für das WLAN auswählen, können Sie auch den EAP-Typ (Extensible Authentication Protocol) eingeben, der in Ihrem WLAN verwendet wird.

Wenn Sie jetzt den Typ „Unternehmen“ auswählen, können Sie auch automatische Proxyeinstellungen eingeben, z. B. eine Proxyserver-URL wie `proxy.contoso.com`.

Informationen zu den aktuellen WLAN-Einstellungen, die Sie konfigurieren können, finden Sie unter [Hinzufügen von WLAN-Einstellungen für Geräte mit Android Enterprise und Android-Kioskgeräte in Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Gilt für:
- Android Enterprise-Arbeitsprofil

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Geräteregistrierung

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>Blockieren von Android-Registrierungen nach Gerätehersteller<!--5197392  -->
Sie können die Registrierung eines Geräts basierend auf dem Hersteller des Geräts blockieren. Dies gilt für die Profile „Android-Geräteadministrator“ und „Android Enterprise-Arbeitsprofil“. Zum Anzeigen der Registrierungseinschränkungen navigieren Sie zu [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Geräte** > **Registrierungseinschränkungen**.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>Verbesserungen an der Benutzeroberfläche zum Erstellen von Registrierungstypprofilen unter iOS/iPadOS<!-- 6055005 -->
Die Seite **Profil für Registrierungstyp erstellen** **Einstellungen** für die Registrierung von iOS/iPadOS-Benutzern wurde optimiert, um die Auswahl des **Registrierungstyps** zu verbessern und die Funktionalität beizubehalten. Sie finden die neue Benutzeroberfläche auf der Seite [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Geräte** > **iOS** > **iOS-Registrierung** > **Registrierungstypen** > **Profil erstellen** > **Einstellungen**. Weitere Informationen finden Sie unter [Erstellen eines Benutzerregistrierungsprofils in Intune](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="new-information-in-device-details---4471759-5604099----"></a>Neue Informationen in den Gerätedetails<!-- 4471759 5604099  -->
Die folgenden Informationen finden Sie jetzt auf der Seite **Übersicht** für Geräte:
- Arbeitsspeicherkapazität (Menge des physischen Arbeitsspeichers auf dem Gerät)
- Speicherkapazität (Menge des physischen Massenspeichers auf dem Gerät) 
- CPU-Architektur


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>Remoteaktion „Aktivierungssperre umgehen“ für iOS umbenannt in „Aktivierungssperre deaktivieren“ <!--5904591  -->
Die Remoteaktion **Aktivierungssperre umgehen** wurde in **Aktivierungssperre deaktivieren** umbenannt. Weitere Informationen finden Sie unter [Deaktivieren der Aktivierungssperre für iOS mit Intune](../remote-actions/device-activation-lock-bypass.md).

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Unterstützung der Bereitstellung von Windows 10-Featureupdates für Autopilot-Geräte<!-- 5948137   -->
Intune unterstützt jetzt die [Bereitstellung von Windows 10-Featureupdates](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) für registrierte Autopilot-Geräte.

Richtlinien für Windows 10-Featureupdates können bei Autopilot-Ausführung über die Windows-Willkommensseite (Out Of Box Experience, OOBE) nicht angewendet werden und gelten erst bei der ersten Windows Update-Überprüfung nach der Bereitstellung eines Geräts (in der Regel ein Tag).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Bereitstellungsberichte für Windows Autopilot (Vorschau) <!-- 3856172   -->
In einem neuen Bericht werden Informationen zu allen Geräten angegeben, die mit Windows Autopilot bereitgestellt wurden. Weitere Informationen finden Sie im [Autopilot-Bereitstellungsbericht](../enrollment/enrollment-autopilot.md#autopilot-deployments-report).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>Neue integrierte Intune-Rolle: Endpunktsicherheits-Manager<!--4253397   -->
Eine neue integrierte Intune-Rolle steht zur Verfügung: Endpunktsicherheits-Manager. Mit dieser neuen Rolle erhalten Administratoren Vollzugriff auf den Endpoint Manager-Knoten in Intune und schreibgeschützten Zugriff auf andere Bereiche. Die Rolle ist eine Erweiterung der Rolle „Sicherheitsadministrator“ aus Azure AD. Wenn Sie aktuell nur über die Rolle „Globale Administratoren“ verfügen, sind keine Änderungen erforderlich. Wenn Sie Rollen verwenden und die Granularität der Rolle „Sicherheits-Manager für Endpunkte“ nutzen möchten, weisen Sie diese Rolle zu, wenn Sie verfügbar ist. Weitere Informationen zu integrierten Rollen finden Sie unter [Rollenbasierte Zugriffssteuerung für Microsoft Intune](role-based-access-control.md).

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Woche vom 6. Januar 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>S/MIME-Unterstützung für Microsoft Outlook für iOS<!-- 2669398 -->
Intune unterstützt die Bereitstellung von S/MIME-Signatur- und Verschlüsselungszertifikaten, die mit Outlook für iOS auf iOS-Geräten verwendet werden können. Weitere Informationen finden Sie unter [Vertraulichkeitsbezeichnung und Schutz in Outlook für iOS-und Android-](https://aka.ms/omsmime).

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Zwischenspeichern von Win32-App-Inhalten mithilfe eines Microsoft Connected Cache-Servers<!-- 6030314 -->
Sie können einen Microsoft Connected Cache-Server auf Ihren Configuration Manager-Verteilungspunkten installieren, um Inhalte von Intune Win32-Apps zwischenzuspeichern. Weitere Informationen finden Sie unter [Microsoft Connected Cache in Configuration Manager – Unterstützung für Intune Win32-Apps](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Rollenbasierte Zugriffssteuerung

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>Windows 10-Profile für administrative Vorlagen (ADMX) unterstützen jetzt Bereichsmarkierungen <!--5137390 -->
Sie können Bereichsmarkierungen jetzt Profilen für administrative Vorlagen (ADMX) zuweisen. Wechseln Sie zu diesem Zweck zu **Intune** > **Geräte** > **Konfigurationsprofile**. Wählen Sie in der Liste ein Profil für administrative Vorlagen und dann **Eigenschaften** > **Bereichsmarkierungen** aus. Weitere Informationen zu Bereichsmarkierungen finden Sie unter [Zuweisen von Bereichsmarkierungen zu anderen Objekten](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Woche vom 30. Dezember 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Abrufen eines persönlichen Wiederherstellungsschlüssels von MEM-verschlüsselten macOS-Geräten<!-- 4851745 -->
Endbenutzer können mithilfe der Unternehmensportal-App für iOS ihren persönlichen Wiederherstellungsschlüssel (FileVault-Schlüssel) abrufen. Das Gerät mit dem persönlichen Wiederherstellungsschlüssel muss bei Intune registriert und über Intune mit FileVault verschlüsselt sein. Endbenutzer können mit der Unternehmensportal-App für iOS ihre persönlichen Wiederherstellungsschlüssel auf dem verschlüsselten macOS-Gerät abrufen, indem sie auf **Wiederherstellungsschlüssel abrufen** klicken. Sie können den Wiederherstellungsschlüssel auch aus Intune abrufen, indem Sie **Geräte** > *das verschlüsselte und registrierte macOS-Gerät* > **Wiederherstellungsschlüssel abrufen** auswählen. Weitere Informationen zu FileVault finden Sie unter [FileVault-Verschlüsselung für macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>Von iOS- und iPadOS-Benutzern lizenzierte VPP-Apps<!-- 5619268 -->
Für benutzerseitig registrierte iOS- und iPadOS-Geräte werden den Endbenutzern keine neu erstellten und bereitgestellten VPP-Anwendungen mit Gerätelizenzierung mehr als verfügbar angeboten. Den Endbenutzern werden aber weiterhin alle benutzerseitig lizenzierten VPP-Apps im Unternehmensportal angezeigt. Weitere Informationen zu VPP-Apps finden Sie unter [Verwalten von iOS- und macOS-Apps, die über das Apple Volume Purchase Program mit Microsoft Intune erworben wurden](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>Woche vom 23. Dezember 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Hinweis: Die Unterstützung für Windows 10 1703 (RS2) wird eingestellt. <!-- 5026679 -->
Am 9. Oktober 2018 endete für Windows 10 1703 (RS2) die Microsoft-Plattformunterstützung für die Home-, Pro- und Pro for Workstations-Editionen. Für Windows 10 Enterprise und die Education-Editionen endete die Plattformunterstützung für Windows 10 1703 (RS2) am 8. Oktober 2019. Am 26. Dezember 2019 wurde die mindestens erforderliche Version der Windows-Unternehmensportalanwendung auf Windows 10 1709 (RS3) angehoben. Computer, auf denen eine ältere als Version 1709 ausgeführt wird, werden nicht mehr mit aktualisierten Versionen der Anwendung aus dem Microsoft Store versorgt. Diese Änderung wurde den Kunden mit einer ältere Version von Windows 10 im Vorfeld über das Message Center mitgeteilt. Weitere Informationen finden Sie im [Informationsblatt zum Lebenszyklus von Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>Woche vom 16. Dezember 2019

### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Aktualisierungen an den administrativen Vorlagen für Windows 10-Geräte <!-- 5941568 -->

Sie können in Microsoft Intune mithilfe von ADMX-Vorlagen Einstellungen für Microsoft Edge, Office und Windows steuern und verwalten. Für die administrativen Vorlagen in Intune gelten die folgenden Aktualisierungen der Richtlinieneinstellungen:

- Unterstützung für Microsoft Edge-Versionen 78 und 79 hinzugefügt
- Umfasst die ADMX-Dateien vom 11. November 2019 in [Administrative Vorlagendateien (ADMX/ADML) und Office-Anpassungstool für Office 365 ProPlus, Office 2019 und Office 2016](https://www.microsoft.com/download/details.aspx?id=49030)

Weitere Informationen zu ADMX-Vorlagen in Intune finden Sie unter [Verwenden von Windows 10-Vorlagen zum Konfigurieren von Gruppenrichtlinieneinstellungen in Microsoft Intune](../configuration/administrative-templates-windows.md).

Gilt für:

- Windows 10 und höher

## <a name="week-of-december-9-2019-1912-service-release"></a>Woche vom 9. Dezember 2019 (1912 Dienstrelease)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrieren zu Microsoft Edge für das verwaltete Durchsuchen<!-- 5173762 -->
Im Hinblick auf die Einstellung von Intune Managed Browser wurden Änderungen an den App-Schutzrichtlinien vorgenommen, um die erforderlichen Schritte zu vereinfachen, die für die Umstellung Ihrer Benutzer auf Edge nötig sind. Die Optionen für die App-Schutzrichtlinieneinstellung **Übertragung von Webinhalt in andere Apps einschränken** wurden aktualisiert, sodass die folgenden Optionen verfügbar sind:

- Jede App
- Intune Managed Browser
- Microsoft Edge
- Nicht verwalteter Browser 

Wenn Sie **Microsoft Edge** auswählen, wird Ihren Endbenutzern Messaging für bedingten Zugriff angezeigt, das sie darüber benachrichtigt, dass Microsoft Edge für das verwaltete Durchsuchen erforderlich ist. Sie werden dazu aufgefordert, Microsoft Edge herunterzuladen und sich mit ihren AAD-Konten anzumelden, wenn sie dies noch nicht getan haben.  Dies entspricht einer Anwendung der App-Konfigurationseinstellung `com.microsoft.intune.useEdge`, die auf **True** festgelegt ist, auf Ihre MAM-fähigen Apps. In den vorhandenen App-Schutzrichtlinien, die die Einstellung **Mit Richtlinien verwaltete Browser** verwendet haben, ist jetzt **Intune Managed Browser** ausgewählt. Dabei ist keine Verhaltensänderung erkennbar. Das bedeutet, dass Ihren Benutzern Messaging zur Verwendung von Microsoft Edge angezeigt wird, wenn Sie die App-Konfigurationseinstellung **useEdge** auf **True** festgelegt haben. Wir empfehlen allen Kunden, die verwalteten Browserszenarios nutzen, ihre App-Schutzrichtlinien mit der Einstellung **Übertragung von Webinhalt in andere Apps einschränken** zu aktualisieren, um sicherzustellen, dass Benutzer die richtigen Anleitungen für den Übergang zu Microsoft Edge sehen, unabhängig davon, welche App sie verwenden. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Konfigurieren von App-Benachrichtigungsinhalt für Organisationskonten<!-- 2576686  -->
Intune-App-Schutzrichtlinien auf Android- und iOS-Geräten ermöglichen es Ihnen, den App-Benachrichtigungsinhalt für Organisationskonten zu steuern. Sie können durch Auswahl einer Option auswählen („Zulassen“, „Organisationsdaten blockieren“ oder „Blockiert“) angeben, wie Benachrichtigungen für Organisationskonten für die ausgewählte App angezeigt werden. Dieses Feature erfordert die Unterstützung von Anwendungen und ist möglicherweise nicht für alle Anwendungen verfügbar, die App-Schutzrichtlinien unterstützen. Outlook für iOS, Version 4.15.0 (oder höher) und Outlook für Android, Version 4.83.0 (oder höher) unterstützen diese Einstellung. Die Einstellung ist in der Konsole verfügbar, aber die Funktionalität ist erst ab dem 16. Dezember 2019 in Kraft. Weitere Informationen zu Intune-App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](../apps/app-protection-policy.md)

#### <a name="microsoft-app-icons-update--4677605----"></a>Aktualisierung der Microsoft-App-Symbole<!--4677605  -->
Die für Microsoft-Apps im App-Zielbereich verwendeten Symbole für App-Schutzrichtlinien und App-Konfigurationsrichtlinien wurden aktualisiert.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Erforderliche Verwendung von genehmigten Tastaturen unter Android<!--4761794  -->
Im Rahmen einer App-Schutzrichtlinie können Sie die Einstellung [**Zugelassene Tastaturen**](../apps/app-protection-policy-settings-android.md#data-protection) festlegen, um zu verwalten, welche Android-Tastaturen mit verwalteten Android-Apps verwendet werden können. Wenn ein Benutzer die verwaltete App öffnet und nicht bereits eine genehmigte Tastatur für diese App verwendet, wird er aufgefordert, zu einer der genehmigten Tastaturen zu wechseln, die bereits auf seinem Gerät installiert sind. Bei Bedarf wird den Benutzern ein Link zum Download einer genehmigten Tastatur aus dem Google Play Store angezeigt, die sie installieren und einrichten können. Die Benutzer können nur dann Textfelder in einer verwalteten App bearbeiten, wenn die aktive Tastatur eine genehmigte Tastatur ist.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Gerätekonfiguration

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Aktualisiertes SSO-Verhalten für Apps und Websites auf iOS-, iPadOS- und macOS-Geräten<!-- 4999578  -->
In Intune wurden weitere Einstellungen für das einmalige Anmelden (Single Sign-On, SSO) für iOS-, iPadOS- und macOS-Geräte hinzugefügt. Sie können ab sofort eine Umleitung für SSO-App-Erweiterungen konfigurieren, die von Ihrer Organisation oder Ihrem Identitätsanbieter geschrieben wurden. Verwenden Sie diese Einstellungen, um ein nahtloses SSO-Verhalten für Apps und Websites zu konfigurieren, die moderne Authentifizierungsmethoden wie beispielsweise OAuth und SAML2 verwenden. 

Diese neuen Einstellungen erweitern die bisherigen Einstellungen für SSO-App-Erweiterungen und die integrierte Kerberos-Erweiterung von Apple (**Geräte** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS** oder **macOS** für den Plattformtyp > **Gerätefunktionen** für den Profiltyp). 

Um eine vollständige Liste der Einstellungen für SSO-App-Erweiterungen anzuzeigen, die Sie konfigurieren können, wechseln Sie zu [SSO unter iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) und [SSO unter macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Gilt für:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>Wir haben zwei Einstellungen zur Geräteeinschränkung für iOS- und iPadOS-Geräte aktualisiert, um deren Verhalten zu korrigieren<!-- 5701352    -->
Für iOS-Geräte können Sie Geräteeinschränkungsprofile mit den Einstellungen **Drahtlose PKI-Updates zulassen** und **Modus mit USB-Einschränkung blockieren**. (**Geräte** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS/iPadOS** für Plattform > **Geräteeinschränkungen** für Profiltyp). Vor diesem Release waren die Benutzeroberflächeneinstellungen und Beschreibungen für die folgenden Einstellungen falsch, diese wurden nun korrigiert. Ab diesem Release lautet das Einstellungsverhalten wie folgt:

**Drahtlose PKI-Updates blockieren**: **Blockieren**: Verhindert, dass Ihre Benutzer Softwareupdates erhalten, wenn das Gerät nicht an einen Computer angeschlossen ist. **Nicht konfiguriert** (Standardeinstellung): Ermöglicht es einem Gerät, Softwareupdates zu empfangen, ohne mit einem Computer verbunden zu sein.
- Bisher konnte diese Einstellung auf **Zulassen** festgelegt werden, um es Ihren Benutzern zu ermöglichen, Softwareupdates zu empfangen, ohne ihre Geräte mit einem Computer verbinden zu müssen.
**USB-Zubehör bei gesperrtem Gerät zulassen**: **Zulassen**: USB-Zubehör kann Daten mit einem Gerät austauschen, das seit mehr als einer Stunde gesperrt ist. **Nicht konfiguriert** (Standardeinstellung): Der Modus mit USB-Einschränkung auf dem Gerät wird nicht aktualisiert, und USB-Zubehör wird daran gehindert, Daten vom Gerät zu übertragen, wenn dieses länger als eine Stunde gesperrt ist.
- Bisher konnte diese Einstellung auf **Blockieren** festgelegt werden, um den Modus mit USB-Einschränkung auf überwachten Geräten zu deaktivieren.

Weitere Informationen zu allen konfigurierbaren Einstellungen finden Sie unter [iOS- und iPadOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](../configuration/device-restrictions-ios.md).

Diese Funktion gilt für:

- OS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Gerätekonfigurationsprofil für das kabelgebundene Netzwerk für macOS-Geräte<!-- 3508686  -->
   > [!NOTE]
   > Diese Funktion hat sich verzögert, wird aber bald veröffentlicht.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Sperren der Konfiguration von Zertifikatanmeldeinformationen im verwalteten Schlüsselspeicher auf Android Enterprise-Gerätebesitzergeräten durch die Benutzer<!-- 3311998 -->
Auf Android Enterprise-Gerätebesitzergeräten können Sie die Benutzer mithilfe einer neuen Einstellung daran hindern, ihre Zertifikatanmeldeinformationen im verwalteten Schlüsselspeicher zu konfigurieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Nur Gerätebesitzer > Geräteeinschränkungen** für Profiltyp > **Benutzer und Konten**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Geräteverwaltung

#### <a name="protected-wipe-action-now-available--51150000---"></a>Geschütztes Zurücksetzen ab sofort verfügbar<!--51150000 -->
Sie haben jetzt die Möglichkeit, die Aktion „Gerät zurücksetzen“ zu verwenden, um Ihr Gerät geschützt zurückzusetzen. Das geschützte Zurücksetzen entspricht der Standardzurücksetzung, mit dem Unterschied, dass der Vorgang nicht durch Ausschalten des Geräts umgangen werden kann. Beim geschützten Zurücksetzen wird solange versucht, das Gerät zurückzusetzen, bis der Vorgang erfolgreich ist. In manchen Konfigurationen kann das Gerät aufgrund dieser Aktion nicht neu gestartet werden. Weitere Informationen finden Sie auf der Seite [Abkoppeln oder Zurücksetzen von Geräten](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Ethernet-MAC-Geräteadresse auf der Übersichtsseite des Geräts hinzugefügt<!--5562275 -->
Sie können ab sofort die Ethernet-MAC-Geräteadresse auf der Seite mit den Gerätedetails anzeigen (**Geräte** > **Alle Geräte** > Auswählen eines Geräts > **Übersicht**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Gerätesicherheit

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Verbesserte Funktionalität auf einem gemeinsam genutzten Gerät, wenn gerätebasierte Richtlinien für bedingten Zugriff aktiviert sind<!-- 1734096  -->
Die Benutzerumgebung für ein gemeinsam genutztes Gerät mit mehreren Benutzern, für die gerätebasierte Richtlinien für bedingten Zugriff gelten, wurde verbessert, indem bei der Erzwingung der Richtlinie die neueste Konformitätsbewertung für den Benutzer überprüft wird. Weitere Informationen finden Sie in den folgenden Artikeln:
- [Azure-Übersicht zum bedingten Zugriff](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Übersicht über die Intune-Gerätekonformität](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Verwendung von PKCS-Zertifikatprofilen zum Bereitstellen von Geräten mit Zertifikaten<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
Sie können ab sofort PKCS-Zertifikatprofile verwenden, um Zertifikate für *Geräte* auszustellen, die Android for Work, iOS und Windows ausführen, wenn sie mit Profilen wie denen für WLAN und VPN verknüpft sind. Zuvor unterstützten diese drei Plattformen nur benutzerbasierte Zertifikate, die gerätebasierte Unterstützung war auf macOS beschränkt.

> [!NOTE]
> PKCS-Zertifikatprofile werden nicht mit WLAN-Profilen unterstützt. Wählen Sie stattdessen SCEP-Zertifikatsprofile, wenn Sie einen [EAP-Typ](../configuration/wi-fi-settings-windows.md#enterprise-profile) verwenden.

Um ein gerätebasiertes Zertifikat zu erstellen, wählen Sie [während der Erstellung eines PKCS-Zertifikatprofils](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) für die unterstützten Plattformen **Einstellungen** aus. Daraufhin wird die Einstellung **Zertifikattyp** angezeigt, die Optionen für Gerät oder Benutzer unterstützt.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Überwachung und Problembehandlung

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Zentralisierte Überwachungsprotokolle<!--5603185, 5697164 -->
Eine neue zentralisierte Benutzeroberfläche für Überwachungsprotokolle sammelt erfasst ab sofort die Überwachungsprotokolle für alle Kategorien auf einer Seite. Sie können die Protokolle filtern, um die Daten abzurufen, nach denen Sie suchen. Wechseln Sie zum Anzeigen der Überwachungsprotokolle zu **Mandantenverwaltung** > **Überwachungsprotokolle**. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>Einschluss von Informationen zu Bereichstags in Aktivitätsdetails von Überwachungsprotokollen<!--5763534 -->
Die Details zu Überwachungsprotokollaktivitäten enthalten ab sofort auch Informationen zu den Bereichstags (für Intune-Objekte, die Bereichstags unterstützen). Weitere Informationen zu Überwachungsprotokollen finden Sie unter [Verwenden von Überwachungsprotokollen zum Nachverfolgen und Überwachen von Ereignissen](monitor-audit-logs.md).


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Woche des 2. Dezember 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Neue Lizenzierung der Co-Verwaltung von Microsoft Endpoint Configuration Manager<!--5027281-->
Configuration Manager-Kunden mit Software Assurance können die Intune-Co-Verwaltung für Windows 10-PCs nutzen, ohne eine zusätzliche Intune-Lizenz für die Co-Verwaltung erwerben zu müssen. Kunden müssen ihren Endbenutzern nicht mehr einzelne Intune-/EMS-Lizenzen für die Co-Verwaltung von Windows 10 zuweisen.
- Geräte, die von Configuration Manager verwaltet und bei der Co-Verwaltung registriert werden, verfügen über fast die gleichen Rechte wie eigenständige MDM-verwaltete Intune-PCs. Nach dem Zurücksetzen können sie jedoch nicht mithilfe von Autopilot nochmals bereitgestellt werden.
- Windows 10-Geräte, die anderweitig bei Intune registriert sind, benötigen vollständige Intune-Lizenzen.
- Geräte auf anderen Plattformen benötigen weiterhin vollständige Intune-Lizenzen.

Weitere Informationen finden Sie unter [Lizenzierungsbestimmungen](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Woche vom 18. November 2019 (1911 Dienstrelease)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>App-Verwaltung

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Benutzeroberflächenupdate beim selektiven Löschen von App-Daten<!-- 4102028 -->
Die Benutzeroberfläche zum selektiven Löschen von App-Daten in Intune wurde aktualisiert. Die Änderungen der Benutzeroberfläche umfassen:
- eine vereinfachte Funktion mithilfe eines Formats im Assistentenstil in einem einzigen Bereich
- Ein Update für den Erstellungsflow zum Einschließen von Zuweisungen.
- Eine zusammengefasste Seite aller festgelegten Einstellungen beim Anzeigen der Eigenschaften, bevor eine neue Richtlinie erstellt wird oder bei der Bearbeitung einer Eigenschaft. Beim Bearbeiten von Eigenschaften zeigt die Zusammenfassung nur eine Liste der Elemente aus der Kategorie der Eigenschaften an, die bearbeitet werden.

Weitere Informationen finden Sie unter [Zurücksetzen nur von Unternehmensdaten aus mit Intune verwalteten Apps](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Unterstützung von Tastaturen von Drittanbietern für iOS und iPadOS<!-- 4922950 -->
Im März 2019 haben wir angekündigt, dass die Unterstützung für die App-Schutzrichtlinie „Tastaturen von Drittanbietern“ für iOS aufgehoben wurde. Das Feature kehrt sowohl mit iOS- als auch mit iPadOS-Unterstützung zu Intune zurück. Wählen Sie die Registerkarte **Datenschutz** einer neuen oder bestehenden iOS/iPadOS-App-Schutzrichtlinie aus, um diese Einstellung zu aktivieren, und suchen Sie die Einstellung **Tastaturen von Drittanbietern** unter **Datenübertragung**.

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

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Verbesserte macOS-Registrierungsoberfläche im Unternehmensportal <!-- 5074349  -->  
Das Unternehmensportal für die macOS-Registrierung verfügt über einen einfacheren Registrierungsprozess, der sich enger an das Unternehmensportal für die iOS-Registrierung ausrichtet. Gerätebenutzer wird jetzt Folgendes angezeigt:  

* Eine schlankere Benutzeroberfläche  
* Eine verbesserte Prüfliste für die Registrierung  
* Deutlichere Anweisungen zum Registrieren ihrer Geräte  
* Verbesserte Optionen zur Problembehandlung  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Web-Apps, die aus der Windows-Unternehmensportal-App gestartet werden<!-- 5030972 -->
Endbenutzer können Web-Apps jetzt direkt aus der Windows-Unternehmensportal-App starten. Endbenutzer können die Web-App auswählen und dann die Option **Im Browser öffnen** auswählen. Die veröffentlichte Web-URL wird direkt einem Webbrowser geöffnet. Diese Funktionalität wird in der nächsten Woche eingeführt. Weitere Informationen über Web-Apps finden Sie unter [Hinzufügen von Web-Apps zu Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Neue Spalte für den Zuweisungstyp im Unternehmensportal für Windows 10 <!-- 5459950  -->
Die Spalte im Unternehmensportal unter **Installierte Apps** > **Zuweisungstyp** wurde in **Von Ihrer Organisation als erforderlich festgelegt** umbenannt.  Unter dieser Spalte wird den Benutzern der Wert **Yes** (Ja) oder **No** (Nein) angezeigt, um anzugeben, dass eine App entweder erforderlich oder von ihrer Organisation als optional angesehen wird. Diese Änderungen wurden durchgeführt, da Gerätebenutzer über das Konzept der verfügbaren Apps irritiert waren. Ihre Benutzer können weitere Informationen zum Installieren von Apps im Unternehmensportal unter [Installieren und Freigeben von Apps auf Ihrem Gerät](/intune-user-help/install-apps-cpapp-windows) finden. Weitere Informationen zum Konfigurieren der Unternehmensportal-App für Ihre Benutzer finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Woche vom 4. November 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Gerätesicherheit

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Sicherheitsbaselines werden auf Microsoft Azure Government unterstützt.<!-- 4062552 -->

Intune-Instanzen, die auf *Microsoft Azure Government* gehostet werden, können nun [Sicherheitsbaselines](../protect/security-baselines.md) verwenden, mit denen Sie Ihre Benutzer und Geräte sichern und schützen können.

## <a name="whats-new-archive"></a>Archiv der Neuheiten
Die Neuigkeiten vorheriger Monate finden Sie im [Archiv für Neuheiten](whats-new-archive.md).

## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
