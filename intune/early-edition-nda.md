---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/3/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: d00c367cdcd0b8172d64c3ebbcd0dec2165407c9
ms.sourcegitcommit: b93db06ba435555f5b126f97890931484372fcfb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829129"
---
# <a name="the-early-edition-for-microsoft-intune---december-2018"></a>Die Early Edition für Microsoft Intune – Dezember 2018

> [!Note]
> Benachrichtigung zum Geheimhaltungsvertrag: Die folgenden Änderungen befinden sich in der Entwicklung für Intune. Die Freigabe dieser Informationen erfolgt im Geheimhaltungsvertrag (GHV) auf einer sehr begrenzten Basis. Posten Sie keine der folgenden Informationen in sozialen Medien oder auf öffentlichen Websites wie Twitter, UserVoice, Reddit usw. 

Die **Early Edition** enthält eine Liste der Features, die im Rahmen des Geheimhaltungsvertrags freigegeben und in späteren Releases von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Verfassen Sie außerhalb Ihres Unternehmens keinen Tweet oder Post auf UserVoice o.Ä. über diese Informationen. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung <!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie mit verwaltetem Google Play Store-Apps und branchenspezifische Apps für Benutzer bereitstellen. Insbesondere kann die IT-Abteilung Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte kompromittieren müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Neue Optionen zum automatischen Herstellen einer Verbindung und Beibehalten von Regeln bei der Verwendung von DNS-Einstellungen unter Windows 10 und höher <!-- 1333665, 2999078 -->
Auf Geräten unter Windows 10 und höher werden Sie möglicherweise ein VPN-Konfigurationsprofil erstellen können, das eine Liste von DNS-Servern zum Auflösen von Domänen enthält, z.B. „contoso.com“. Dazu gehören neue Einstellungen für die Namensauflösung (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **Windows 10 und höher** als Plattform und **VPN** als Profiltyp aus, und wählen Sie **DNS-Einstellungen** >**Hinzufügen** aus): 

- **Automatisch verbinden**: Wenn **Aktiviert**, stellt das Gerät automatisch eine Verbindung mit dem VPN her, wenn ein Gerät mit einer Domäne Kontakt aufnimmt, die Sie eingeben, z.B. „contoso.com“.
- **Persistent**: Standardmäßig sind alle Regeln der Namensauflösungsrichtlinie-Tabelle (Name Resolution Policy Table, NRPT) aktiv, solange das Gerät über dieses VPN-Profil verbunden ist. Wenn diese Einstellung für eine NRPT-Regel **Aktiviert** ist, bleibt die Regel auch dann auf dem Gerät aktiv, wenn das VPN getrennt ist oder das VPN-Profil entfernt wird. Die Regel gilt, bis sie manuell entfernt wird – dies ist mit PowerShell möglich.

In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) wird die aktuelle Liste der Einstellungen beschrieben. 

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Hilfe- und Supportseite in der Windows-Unternehmensportal-App <!-- 1488939 -->
Der Windows-Unternehmensportal-App wird eine neue Seite hinzugefügt. Die Hilfe- und Supportseite enthält die Helpdesk-Kontaktinformationen. Benutzer werden darüber hinaus Unternehmensportalprotokolle senden können, wenn Probleme auftreten. Die Seite bietet auch einen FAQ-Abschnitt, um Endbenutzer zu unterstützen.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Verwenden vertrauenswürdiger Netzwerkerkennung für VPN-Profile auf Windows 10-Geräten <!-- 1500165 -->
Wenn Sie die Erkennung vertrauenswürdiger Netzwerke verwenden, werden Sie verhindern können, dass VPN-Profile automatisch eine VPN-Verbindung herstellen, wenn der Benutzer sich bereits in einem vertrauenswürdigen Netzwerk befindet. Sie werden DNS-Suffixe zum Aktivieren der Erkennung vertrauenswürdiger Netzwerke auf Geräten mit Windows 10 und höher hinzufügen können (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** als Plattform > **VPN** als Profiltyp).
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) sind die aktuellen VPN-Einstellungen aufgeführt.

### <a name="support-for-android-corporate-owned-fully-managed-devices----574342---"></a>Unterstützung für vollständig verwaltete Android-Unternehmensgeräte <!-- 574342 -->
Intune wird vollständig verwaltete Android-Geräte in einem „Gerätebesitzer“-Szenario unterstützen, in dem das Unternehmen Besitzer ist und die Geräte konsequent von der IT-Abteilung verwaltet und einzelnen Benutzern zugewiesen werden. So können Administratoren das gesamte Gerät verwalten, einen erweiterten Bereich von Richtlinienkontrollen erzwingen, die Arbeitsprofilen nicht zur Verfügung stehen, und Benutzer werden derart eingeschränkt, dass sie nur Apps von verwaltetem Google Play installieren können. Um vollständig verwaltete Android-Geräte einzurichten, wechseln Sie zu **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte**.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Das Intune App SDK unterstützt 256-Bit-Verschlüsselungsschlüssel <!-- 1832174 -->
Das Intune App SDK für iOS wird 256-Bit-Verschlüsselungsschlüssel verwenden, wenn die Verschlüsselung von App-Schutzrichtlinien aktiviert ist. Das SDK bietet zur Kompatibilität mit Inhalten und Apps, die ältere SDK-Versionen verwenden, weiterhin Unterstützung der 128-Bit-Schlüssel.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917---"></a>Aktivierte freigegebene PC-Einstellungen im Intune-Profil <!-- 1907917 -->
Derzeit können Sie freigegebene PC-Einstellungen auf Windows 10-Desktopgeräten mithilfe einer benutzerdefinierten OMA-URI-Einstellung konfigurieren. Ein neues Profil zum Konfigurieren freigegebener PC-Einstellungen wird hinzugefügt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Freigegebenes, von mehreren Benutzern verwendetes Gerät**).
Gilt für: Windows 10 und höher, Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App  <!-- 1927359 -->
Intune wird die Unternehmensportal-App auf bestimmten Geräten nicht mehr unterstützen, wenn sie aus dem App Store installiert wird. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

Wenn Benutzer die Unternehmensportal-App aus dem App Store installieren und dann versuchen, diese Geräte darüber zu registrieren, erhalten sie eine Fehlermeldung. Es wird vorausgesetzt, dass diese Geräte die Unternehmensportal-App nur dann verwenden, wenn sie während der Registrierung automatisch von Intune per Push übertragen wird. Registrierungsprofile in Intune im Azure-Portal werden aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Wenn Sie wünschen, dass Ihre DEP-Gerätebenutzer die Unternehmensportal-App verwenden, müssen Sie Ihre Einstellungen in einem Registrierungsprofil angeben. Darüber hinaus wird der Bildschirm **Identifizieren Sie Ihr Gerät** in der Unternehmensportal-App bald veraltet sein.  
Um die Unternehmensportal-App auf bereits registrierten DEP-Geräten zu installieren, müssen Sie zu „Intune“ > „Client-Apps“ wechseln und sie als verwaltete App mit App-Konfigurationsrichtlinien mithilfe von Push übertragen. Nähere Informationen zu diesen Schritten erhalten Sie in zukünftigen Dokumentationen.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Nicht-Administratoren können BitLocker auf Windows 10-Geräten aktivieren, die in Azure AD eingebunden sind<!-- 2147379 -->
Beim Aktivieren der BitLocker-Einstellungen auf Windows 10-Geräten (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** als Plattform > **Endpunktschutz** als Profiltyp > **Windows-Verschlüsselung**) fügen Sie BitLocker-Einstellungen hinzu. Dieses Update enthält eine neue BitLocker-Einstellung, um Standardbenutzern (Nicht-Administratoren), die Verschlüsselung zu ermöglichen. Die aktuellen Einstellungen finden Sie unter [Endpoint protection settings for Windows 10 (Endpunktschutz-Einstellungen für Windows 10)](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-app-pin----2298397---"></a>Intune-App-PIN <!-- 2298397 -->
Als IT-Administrator müssen Sie möglicherweise die Anzahl der Tage konfigurieren, die ein Endbenutzer warten kann, bis seine Intune-App-PIN geändert werden muss. Die neue Einstellung steht im Azure-Portal bei Auswahl von **Intune** > **Client-Apps** > **App-Schutzrichtlinien**  >  **Richtlinie erstellen** > **Einstellungen** > **Zugriffsanforderungen** zur Verfügung. Dieses Feature wird für Android- und iOS-Geräte zur Verfügung gestellt. Diese Einstellung unterstützt einen positiven Ganzzahlwert.

### <a name="new-windows-10-update-settings----2626030-2512994---"></a>Neue Windows 10-Updateeinstellungen <!-- 2626030 2512994 -->
Für Ihre Windows 10-Updateringe werden Sie Folgendes durchführen können:
- Wiederherstellen der ursprünglichen Einstellungen für automatische Updates auf einem Windows 10-Computer auf Computern, die das *Oktober 2018-Update* ausführen
- Konfigurieren einer neuen Softwareupdateseinstellung, mit der Sie blockieren oder zulassen können, dass Ihre Benutzer Updateinstallationen über die *Einstellungen* ihrer Computer anhalten. 



### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS-E-Mail-Profile können S/MIME-Signatur und -Verschlüsselung verwenden <!-- 2662949 -->
Sie werden ein E-Mail-Profil erstellen können, das unterschiedliche Einstellungen enthält. Dies schließt S/MIME-Einstellungen ein, die zum Signieren und Verschlüsseln der E-Mail-Kommunikation auf iOS-Geräten verwendet werden können (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **E-Mail** als Profiltyp aus).

[iOS-E-Mail-Konfigurationseinstellungen](email-settings-ios.md) listet die aktuellen Einstellungen auf.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509---"></a>Weitere Setup-Assistent-Bildschirme auf einem iOS-DEP-Gerät überspringen <!-- 2687509 -->
Zusätzlich zu den Bildschirmen, die Sie derzeit überspringen können, werden Sie in der Lage sein, iOS-DEP-Geräte so einzustellen, dass die folgenden Bildschirme des Setup-Assistenten übersprungen werden, wenn ein Benutzer das Gerät registriert: „Displayton“, „Datenschutz“, „Android-Migration“, „Home-Taste“, „iMessage & FaceTime“, „Onboarding“, „Watch-Migration“, „Darstellung“, „Bildschirmzeit“, „Softwareupdate“, „SIM-Setup“.
Um die zu überspringenden Bildschirme auszuwählen, wechseln Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, wählen Sie das Token und unter **Profile** das Profil aus, wählen Sie **Eigenschaften** > **Anpassung des Setup-Assistenten** und **Ausblenden**  für alle Bildschirme aus, die Sie überspringen möchten, und wählen Sie **OK** aus.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Einige BitLocker-Einstellungen unterstützen die Windows 10 Pro-Edition<!-- 2727036 -->
Sie werden ein Konfigurationsprofil erstellen können, das die Endpunktschutz-Einstellungen auf Windows 10-Geräten einschließlich BitLocker festlegt. Damit wird auch die Windows 10 Professional-Edition für einige BitLocker-Einstellungen unterstützt. Die aktuellen Einstellungen für die Windows 10-Edition finden Sie unter [Endpoint protection settings for Windows 10 (Endpunktschutz-Einstellungen für Windows 10)](endpoint-protection-windows-10.md#windows-encryption).
Intune wird zusätzliche Felder zur Geräteberichtserstellung bieten, einschließlich Feldern für Android-Hersteller, Modell und Sicherheitspatchversion sowie iOS-Modell. In Intune werden diese Felder durch Auswahl von **Client-Apps** > **Status des App-Schutzes** und **Bericht zum App-Schutz: iOS, Android** verfügbar sein. Darüber hinaus werden diese Parameter Sie bei der Konfiguration der **Zulassen**-Liste für den Gerätehersteller (Android), der **Zulassen**-Liste für das Gerätemodell (Android und iOS) sowie der Einstellung der mindestens erforderlichen Android-Sicherheitspatchversion unterstützen. 

### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal----2809362---"></a>Konfiguration freigegebener Geräte wird im Azure-Portal in „Nachricht auf Sperrbildschirm“ für iOS-Geräte umbenannt <!-- 2809362 -->
Bei der Erstellung eines Konfigurationsprofils für iOS-Geräte werden Sie **Konfiguration freigegebener Geräte**-Einstellungen hinzufügen können, um einem bestimmten Text auf dem Sperrbildschirm anzuzeigen. Dies umfasst folgende Änderungen: 

- Die **Konfiguration freigegebener Geräte**-Einstellungen im Azure-Portal werden umbenannt in „Nachricht auf Sperrbildschirm (nur überwacht)“ (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **iOS** als Plattform und **Gerätefunktionen** als Profiltyp aus, wählen Sie **Nachricht auf Sperrbildschirm** aus).
- Beim Hinzufügen von Sperrbildschirmnachrichten können Sie eine Seriennummer, einen Gerätenamen oder einen anderen gerätespezifischen Wert als Variable in **Bestandskennzeicheninformationen** einfügen. Sie können z.B. `Device name: {{device name}}` oder `Serial number is {{serial number}}` mit geschweiften Klammern eingeben. [iOS-Token](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) listet die verfügbaren Token auf, die verwendet werden können.

[Einstellungen zur Anzeige von Nachrichten auf dem Sperrbildschirm](shared-device-settings-ios.md) listet die aktuellen Einstellungen auf.

### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564--"></a>Ausführlicheres Messaging zu Registrierungseinschränkungsfehlern <!-- 3111564-->
Ausführlichere Fehlermeldungen werden verfügbar sein, wenn Registrierungseinschränkungen nicht erfüllt werden. Um diese Meldungen anzuzeigen, wechseln Sie zu **Intune** > **Problembehandlung**, und überprüfen Sie die Tabelle „Registrierungsfehler“.

### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Neue Benachrichtigungen, Hinweise und Keyguard-Einstellungen zu Geräten von Android Enterprise-Gerätebesitzern <!-- 3201839 3201843 -->
Dieses Update umfasst mehrere neue Features für Android Enterprise-Geräte bei Ausführung als Gerätebesitzer. Um diese Features zu verwenden, wechseln Sie zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie als **Plattform** **Android Enterprise** und als **Profiltyp** **Nur Gerätebesitzer** > **Geräteeinschränkungen** aus.
Die folgende neuen Funktionen sind verfügbar: 
- Deaktivieren der Anzeige von Systembenachrichtigungen einschließlich eingehender Anrufe, Systemwarnungen, Systemfehler und mehr
- Überspringen des Startens von Tutorials und von Hinweisen für Apps, die erstmals geöffnet werden, wird vorgeschlagen
- Deaktivieren erweiterter Keyguard-Einstellungen, z.B. Kamera, Benachrichtigungen, Fingerabdruckentsperrung und mehr

Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [Android Enterprise device restriction settings (Android Enterprise-Geräteeinschränkungseinstellungen)](device-restrictions-android-for-work.md).

### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Geräte von Android Enterprise-Gerätebesitzern können Always On-VPN-Verbindungen verwenden <!-- 3202194 -->
In diesem Update können Sie Always On-VPN-Verbindungen mit Geräten von Android Enterprise-Gerätebesitzern verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Sie können Always On-VPN wie folgt aktivieren: Wählen Sie in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** als Plattform, **Geräteeinschränkungen** für „Nur Gerätebesitzer“ und die Einstellungen für **Konnektivität** aus. Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [Android Enterprise device restriction settings (Android Enterprise-Geräteeinschränkungseinstellungen)](device-restrictions-android-for-work.md).

### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Neue Einstellung für Endprozesse im Task-Manager auf Windows 10-Geräten <!-- 3285177 --> 
Dieses Update umfasst eine neue Einstellung für Endprozesse im Task-Manager auf Windows 10-Geräten. Mithilfe eines Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie für **Plattform**  **Windows 10** und für **Profiltyp** **Geräteeinschränkungen** > **Allgemein** aus) lassen Sie diese Einstellung zu oder verhindern sie.
Um die aktuellen Einstellungen anzuzeigen, wechseln Sie zu [Windows 10 device restriction settings (Windows 10-Geräteeinschränkungseinstellungen)](device-restrictions-windows-10.md).
Gilt für: Windows 10 und höher

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und werden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->
Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update umfassen die administrativen Vorlagen über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
Administrative Vorlagen stehen als Public Preview zur Verfügung und werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** >**Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
Berichterstellung wird aktiviert. Gilt für: Windows 10 und höher


<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines <!-- 2055484 -->
Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

### <a name="scope-tags-for-apps---1081941---"></a>Bereichsmarkierungen für Apps <!--1081941 -->
Sie können Bereichsmarkierungen erstellen, um den Zugriff auf Intune-Ressourcen einzuschränken. Fügen Sie einer Rollenzuweisung eine Bereichsmarkierung hinzu, und fügen Sie diese anschließend einem Konfigurationsprofil hinzu. Die Rolle hat nur Zugriff auf Ressourcen mit Konfigurationsprofilen, die über übereinstimmende Bereichsmarkierungen (oder keine Bereichsmarkierung) verfügen.
Um eine Bereichsmarkierung zu erstellen, klicken Sie auf **Intune-Rollen** > **Bereich (Markierungen)** > **Erstellen**.
Um einer Rollenzuweisung eine Bereichsmarkierung hinzuzufügen, klicken Sie auf **Intune-Rollen** > **Alle Rollen** > **Policy and Profile Manager** (Richtlinien- und Profil-Manager) > **Zuweisungen** > **Bereich (Gruppen)**.
Um eine Bereichsmarkierung zu einem Konfigurationsprofil hinzuzufügen, klicken Sie auf **Gerätekonfiguration** > **Profile**, wählen Sie ein Profil aus, und klicken Sie auf **Eigenschaften** > **Bereich (Markierungen)**.

### <a name="tenant-health-dashboard----1124854---"></a>Dashboard zur Mandantenintegrität <!-- 1124854 -->
Auf der Seite zum Mandantenstatus in Intune werden Informationen zum Mandantenstatus an einem zentralen Ort bereitgestellt. Die Seite ist in vier Abschnitte unterteilt:  
- **Mandantendetails**: Enthält Informationen, z. B. Ihre MDM-Autorität, die insgesamt bei Ihrem Mandanten angemeldeten Geräte und Ihre Lizenzzähler. In diesem Abschnitt wird auch die aktuelle Dienstversion für Ihren Mandanten angezeigt.
- **Connectorstatus**: Enthält Informationen zu konfigurierten Connectors, z. B. Apple VPP, Windows Store for Business und Zertifikatsconnectors. Basierend auf ihrem aktuellen Zustand werden die Connectors als *Fehlerfrei*, *Warnung* oder *Fehlerhaft* gekennzeichnet.
- **Intune Service Health**: Enthält aktive Vorfälle oder Ausfälle für Ihren Mandanten. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen ([https://portal.office.com](https://portal.office.com)).
- **Intune News**: Enthält aktive Nachrichten für Ihren Mandanten, z. B. Benachrichtigungen, dass Ihr Mandant die neuesten Intune-Features erhalten hat. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Bereitgestellte WIP-Richtlinien ohne Benutzerregistrierung <!-- 1434452 -->
WIP-Richtlinien (Windows Information Protection) können bereitgestellt werden, ohne dass MDM-Benutzer ihr Windows 10-Gerät registrieren müssen. Diese Konfiguration ermöglicht es Unternehmen, ihre Unternehmensdokumente auf der Grundlage der WIP-Konfiguration zu schützen, während der Benutzer die Verwaltung seiner eigenen Windows-Geräte beibehalten kann. Sobald Dokumente durch eine WIP-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Mobile App** > **Selektive App-Zurücksetzung** aus.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>App-Schutzrichtlinieneinstellungen (APP) für Webdaten <!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-Token, das von einer anderen MDM-Software verwendet wird <!-- 1488946 -->
Intune erkennt und zeigt Details an, wenn ein VPP-Token (Apple Volume Purchase Program) von Intune und einer anderen MDM-Software verwendet wird.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Abgekoppelte Geräte im Gerätekonformitätsdashboard <!-- 1981119 -->
In einem zukünftigen Update werden abgekoppelte Geräte aus dem Gerätekonformitätsdashboard entfernt. Dadurch werden Ihre Konformitätsnummern geändert.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Änderungen im Updateprozess für lokale Connectors <!-- 2277554 -->
Auf Grundlage von Kundenfeedback wird die Art und Weise, wie Updates für lokale Connectors ausgeführt werden, geändert. Nachdem Sie erstmalig einen lokalen Connector installiert haben, werden Updates automatisch ausgeführt. Diese Änderung beginnt mit dem neuen PFX Certificate Connector für Microsoft Intune und wird dann langsam auf andere Typen lokaler Connectors ausgeweitet. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Überprüfen des Configuration Manager auf Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher



## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



