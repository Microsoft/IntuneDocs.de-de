---
title: Early Edition – Microsoft Intune
titlesuffix: ''
description: Early Edition für Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 94125ced318f304e5b2bdc8f09472280fc05b08a
ms.sourcegitcommit: 662afec5e87639a7f541bb89700cc0fec5037bb0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2019
ms.locfileid: "54069352"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Die Early Edition für Microsoft Intune – Januar 2019

> [!Note]
> GHV-Benachrichtigung: Die folgenden Änderungen sind in der Entwicklung für Intune. Die Freigabe dieser Informationen erfolgt im Geheimhaltungsvertrag (GHV) auf einer sehr begrenzten Basis. Posten Sie keine der folgenden Informationen in sozialen Medien oder auf öffentlichen Websites wie Twitter, UserVoice, Reddit usw. 

Die **Early Edition** enthält eine Liste der Features, die im Rahmen des Geheimhaltungsvertrags freigegeben und in späteren Releases von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Verfassen Sie außerhalb Ihres Unternehmens keinen Tweet oder Post auf UserVoice o.Ä. über diese Informationen. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Android Enterprise-Apps <!-- 1352553  -->
Sie können verwaltete Google Play-Apps aus Microsoft Intune löschen. Um eine verwaltete Google Play-App zu löschen, öffnen Sie Microsoft Intune im Azure-Portal und wählen **Client-Apps** > **Apps** aus. Klicken Sie in der App-Liste auf die Auslassungspunkte (...) rechts neben der verwalteten Google Play-App, und wählen Sie dann in der angezeigten Liste die Option **Löschen** aus. Wenn Sie eine verwaltete Google Play-App aus der App-Liste löschen, wird die Genehmigung für die Google Play-App automatisch aufgehoben.

### <a name="managed-google-play-app-type----1352580---"></a>App-Typ „Verwaltetes Google Play“ <!-- 1352580 -->
Der App-Typ **Verwaltetes Google Play** ermöglicht es Ihnen, [verwaltete Google Play-Apps](https://play.google.com/work/search?q=microsoft&c=apps) gezielt zu Intune hinzuzufügen. Als Intune-Administrator können Sie verwaltete Google Play-Apps ab sofort in Intune suchen, genehmigen, synchronisieren und genehmigte verwaltete Google Play-Anwendungen zuweisen. Sie müssen nicht mehr separat zur verwalteten Google Play-Konsole navigieren, und es ist keine erneute Authentifizierung mehr erforderlich. Klicken Sie in Intune auf **Client-Apps** > **Apps** > **Hinzufügen**. Wählen Sie in der Liste **App-Typ** als App-Typ **Verwaltetes Google Play** aus.

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Vorschau der Unterstützung für vollständig verwaltete Android-Unternehmensgeräte <!-- 1574342  -->
Intune wird vollständig verwaltete Android-Geräte in einem „Gerätebesitzer“-Szenario unterstützen, in dem das Unternehmen Besitzer ist und die Geräte konsequent von der IT-Abteilung verwaltet und einzelnen Benutzern zugewiesen werden. So können Administratoren das gesamte Gerät verwalten, einen erweiterten Bereich von Richtlinienkontrollen erzwingen, die Arbeitsprofilen nicht zur Verfügung stehen, und Benutzer werden derart eingeschränkt, dass sie nur Apps von verwaltetem Google Play installieren können. Um vollständig verwaltete Android-Geräte einzurichten, wechseln Sie zu **Geräteregistrierung** > **Android-Registrierung** > **Unternehmenseigene, vollständig verwaltete Geräte**. Hinweis: Dieses Feature befindet sich in der Vorschau. Einige Intune-Funktionen, wie z.B. Zertifikate, Konformität und bedingter Zugriff, stehen momentan für vollständig verwaltete Android-Benutzergeräte nicht zur Verfügung.

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660----"></a>Bereitstellung von online lizenzierten Microsoft Store für Unternehmen-Apps <!-- 16726660  -->
Sie können die erforderlichen, online lizenzierten Microsoft Store für Unternehmen-Apps im Gerätekontext zuweisen. Wenn Sie eine Microsoft Store für Unternehmen-App auf diese Weise bereitstellen, kann die App für alle Benutzer auf dem Gerät installiert werden. Dies gilt nur für Windows 10 RS4-Desktopgeräte und höher. Die Option zur Installation im Gerätekontext ist auf der Seite für die Zuweisung von Client-Apps für online lizenzierte Microsoft Store für Unternehmen-Apps verfügbar.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Konfigurieren des Profils zum Überspringen einiger Bildschirme während des Setup-Assistenten <!-- 2276470  -->
Wenn Sie ein macOS-Registrierungsprofil erstellen, können Sie dieses konfigurieren, um folgende Bildschirme zu überspringen, wenn ein Benutzer den Setup-Assistenten durchläuft:
- Android-Migration
- Anzeigefarbton
- Datenschutz
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Zuweisen von Autopilot-Profilen zur virtuellen Gruppe „Alle Geräte“ <!--2715522  -->
Sie können Autopilot-Profile zur virtuellen Gruppe „Alle Geräte“ zuweisen. Wählen Sie dazu **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** aus. Wählen Sie dann ein Profil > **Zuweisungen** > und unter **Zuweisen zu** wählen Sie **Alle Geräte** aus. Weitere Informationen zu Autopilot-Profilen finden Sie unter [Registrieren von Windows-Geräten mit Windows Autopilot](enrollment-autopilot.md).

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>Anpassen des Hintergrundbilds auf überwachten iOS-Geräten mithilfe eines Gerätekonfigurationsprofils <!-- 2809324  -->
Wenn Sie ein Gerätekonfigurationsprofil für iOS-Geräte erstellen, können Sie einige Einstellungen in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **iOS** für die Plattform > **Gerätebeschränkungen** für den Profiltyp zulassen und einschränken. Dieses Update enthält neue Einstellungen für das **Hintergrundbild**, die es einem Administrator ermöglichen, eine PNG-, JPG- oder JPEG-Bilddatei als Hintergrundbild zu verwenden, eine Bildvorschau anzuzeigen und Benutzer daran zu hindern, das Hintergrundbild zu ändern. Die Einstellungen für das Hintergrundbild gelten nur für überwachte Geräte. Eine Liste der aktuellen Einstellungen finden Sie in den [Geräteeinschränkungen für iOS-Geräte](device-restrictions-ios.md).

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Popupbenachrichtigungen für Win32-Apps <!-- 3136566   -->
Sie können die Anzeige von Popupbenachrichtigungen für die Benutzer pro App-Zuweisung unterdrücken. Wählen Sie in Intune **Client-Apps** > **Apps** > App-Auswahl > **Zuweisungen** > **Gruppen einschließen**. 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>Kontaktfreigabe über Bluetooth in „Geräteeinschränkungen“ > „Gerätebesitzer für Android Enterprise“ entfernt <!-- 3598396 -->
Wenn Sie ein Geräteeinschränkungsprofil für Android Enterprise-Geräte erstellen, gibt es die Einstellung **Kontaktfreigabe über Bluetooth**. In diesem Update wird die Einstellung **Kontaktfreigabe über Bluetooth** entfernt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen > Gerätebesitzer** für Profiltyp > **Allgemein**). 

Die Einstellung **Kontaktfreigabe über Bluetooth** wird für die Verwaltung von Android Enterprise-Gerätebesitzern nicht unterstützt. Die Entfernung dieser Einstellung hat deshalb keine Auswirkungen auf Geräte oder Mandanten – selbst dann, wenn diese Einstellung in Ihrer Umgebung aktiviert und konfiguriert ist.

Die aktuelle Liste der Einstellungen finden Sie unter [Android Enterprise-Geräteeinstellungen zum Zulassen oder Einschränken von Features](device-restrictions-android-for-work.md).

Gilt für: Android Enterprise-Gerätebesitzer

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung <!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie mit verwaltetem Google Play Store-Apps und branchenspezifische Apps für Benutzer bereitstellen. Insbesondere kann die IT-Abteilung Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte kompromittieren müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Neue Optionen zum automatischen Herstellen einer Verbindung und Beibehalten von Regeln bei der Verwendung von DNS-Einstellungen unter Windows 10 und höher <!-- 1333665, 2999078 -->
Auf Geräten unter Windows 10 und höher werden Sie möglicherweise ein VPN-Konfigurationsprofil erstellen können, das eine Liste von DNS-Servern zum Auflösen von Domänen enthält, z.B. „contoso.com“. Dazu gehören neue Einstellungen für die Namensauflösung (**Gerätekonfiguration** > **Profile** > **Profil erstellen**, wählen Sie **Windows 10 und höher** als Plattform und **VPN** als Profiltyp aus, und wählen Sie **DNS-Einstellungen** >**Hinzufügen** aus): 

- **Automatisch verbinden:** Wenn diese Option **Aktiviert** ist, stellt das Gerät automatisch eine Verbindung mit dem VPN her, wenn ein Gerät mit einer Domäne Kontakt aufnimmt, die Sie eingeben, z.B. „contoso.com“.
- **Persistent:** Standardmäßig sind alle Regeln der Namensauflösungsrichtlinie-Tabelle (Name Resolution Policy Table, NRPT) aktiv, solange das Gerät über dieses VPN-Profil verbunden ist. Wenn diese Einstellung für eine NRPT-Regel **aktiviert** ist, bleibt die Regel auch dann auf dem Gerät aktiv, wenn das VPN getrennt ist. Die Regel bleibt in Kraft, bis das VPN-Profil entfernt wird oder bis die Regel manuell entfernt wird – dies kann über PowerShell erfolgen.

In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) wird die aktuelle Liste der Einstellungen beschrieben. 

### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user----1333642-eeready---"></a>Verwenden von S/MIME zum Verschlüsseln und Signieren von mehreren Geräten für einen Benutzer <!-- 1333642 eeready -->
Die E-Mail-Verschlüsselung mit S/MIME mittels eines neuen Profils für importierte Zertifikate wird unterstützt. Navigieren Sie zu deren Verwendung zu **Gerätekonfiguration** > **Profile** > **Profil erstellen**, und wählen Sie zuerst die Plattform und dann den Profiltyp **Importiertes PKCS-Zertifikat** aus. In Intune können Sie Zertifikate im PFX-Format importieren. Intune kann dann genau diese Zertifikate an mehrere Geräte übergeben, die durch einen einzelnen Benutzer registriert wurden. Außerdem enthalten:

- Das native iOS-E-Mail-Profil unterstützt die Aktivierung der S/MIME-Verschlüsselung mithilfe importierter Zertifikate im PFX-Format.
- Die native E-Mail-App auf Windows Phone 10-Geräten verwendet automatisch das S/MIME-Zertifikat.
- Die privaten Zertifikate können über mehrere Plattformen übermittelt werden. Jedoch unterstützen nicht alle E-Mail-Apps S/MIME.
- Auf anderen Plattformen müssen Sie möglicherweise die E-Mail so konfigurieren, dass Sie S/MIME zulässt.  
- E-Mail-Apps, die die S/MIME-Verschlüsselung unterstützen, behandeln das Abrufen von Zertifikaten für die S/MIME-E-Mail-Verschlüsselung womöglich in einer Art und Weise, die von MDM nicht unterstützt werden kann, z.B. durch Lesen über den Zertifikatspeicher des Verlegers.

Unterstützt auf: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="help-and-support-page-in-the-windows-company-portal-app----1488939---"></a>Hilfe- und Supportseite in der Windows-Unternehmensportal-App <!-- 1488939 -->
Der Windows-Unternehmensportal-App wird eine neue Seite hinzugefügt. Die Hilfe- und Supportseite enthält die Helpdesk-Kontaktinformationen. Benutzer werden darüber hinaus Unternehmensportalprotokolle senden können, wenn Probleme auftreten. Die Seite bietet auch einen FAQ-Abschnitt, um Endbenutzer zu unterstützen.

### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Verwenden vertrauenswürdiger Netzwerkerkennung für VPN-Profile auf Windows 10-Geräten <!-- 1500165 -->
Wenn Sie die Erkennung vertrauenswürdiger Netzwerke verwenden, werden Sie verhindern können, dass VPN-Profile automatisch eine VPN-Verbindung herstellen, wenn der Benutzer sich bereits in einem vertrauenswürdigen Netzwerk befindet. Sie werden DNS-Suffixe zum Aktivieren der Erkennung vertrauenswürdiger Netzwerke auf Geräten mit Windows 10 und höher hinzufügen können (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** als Plattform > **VPN** als Profiltyp).
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md) sind die aktuellen VPN-Einstellungen aufgeführt.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Das Intune App SDK unterstützt 256-Bit-Verschlüsselungsschlüssel <!-- 1832174 -->
Das Intune App SDK für Android verwendet 256-Bit-Verschlüsselungsschlüssel, wenn die Verschlüsselung durch App-Schutzrichtlinien aktiviert ist. Das SDK bietet zur Kompatibilität mit Inhalten und Apps, die ältere SDK-Versionen verwenden, weiterhin Unterstützung der 128-Bit-Schlüssel.

### <a name="enabled-shared-pc-settings-in-intune-profile----1907917-1063203---"></a>Aktivierte freigegebene PC-Einstellungen im Intune-Profil <!-- 1907917, 1063203 -->
Derzeit können Sie freigegebene PC-Einstellungen auf Windows 10-Desktopgeräten mithilfe einer benutzerdefinierten OMA-URI-Einstellung konfigurieren. Ein neues Profil zum Konfigurieren freigegebener PC-Einstellungen wird hinzugefügt (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **Freigegebenes, von mehreren Benutzern verwendetes Gerät**).

Gilt für: Windows 10 und höher, Windows Holographic for Business

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App  <!-- 1927359 -->
Bei Geräten, die bereits mithilfe des Setup-Assistenten über eine der Methoden von Apple für die Registrierung von Unternehmensgeräten registriert wurden, unterstützt Intune das Unternehmensportal nicht mehr, wenn es manuell von Endbenutzern aus dem App-Store installiert wurde. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
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
Zusätzlich zu den Anzeigen, die Sie derzeit überspringen können, können Sie künftig festlegen, dass iOS-DEP-Geräte die folgenden Anzeigen im Setup-Assistenten überspringen, wenn ein Benutzer das Gerät registriert: Displayton, Privatsphäre, Android-Migration, Startschaltfläche, iMessage & FaceTime, Onboarding, Watch-Migration, Darstellung, Bildschirmzeit, Softwareupdate und SIM-Setup.
Um die zu überspringenden Bildschirme auszuwählen, wechseln Sie zu **Geräteregistrierung** > **Apple-Registrierung** > **Token für Registrierungsprogramm**, wählen Sie das Token und unter **Profile** das Profil aus, wählen Sie **Eigenschaften** > **Anpassung des Setup-Assistenten** und **Ausblenden**  für alle Bildschirme aus, die Sie überspringen möchten, und wählen Sie **OK** aus.

### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Einige BitLocker-Einstellungen unterstützen die Windows 10 Pro-Edition<!-- 2727036 -->
Sie werden ein Konfigurationsprofil erstellen können, das die Endpunktschutz-Einstellungen auf Windows 10-Geräten einschließlich BitLocker festlegt. Damit wird auch die Windows 10 Professional-Edition für einige BitLocker-Einstellungen unterstützt. Die aktuellen Einstellungen für die Windows 10-Edition finden Sie unter [Endpoint protection settings for Windows 10 (Endpunktschutz-Einstellungen für Windows 10)](endpoint-protection-windows-10.md#windows-encryption).

### <a name="intune-device-reporting-fields----2748738---"></a>Felder zur Geräteberichterstellung in Intune <!-- 2748738 -->
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
Es sind folgende neue Features verfügbar: 
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
Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update: Administrative Vorlagen umfasst über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
Administrative Vorlagen stehen als Public Preview zur Verfügung und werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** >**Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
Berichterstellung wird aktiviert. Gilt für: Windows 10 und höher

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Dunkler Modus für Intune macOS-Unternehmensportal <!-- 3300524 -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Erscheinungsbild des Unternehmensportals an die Farben für diesen Modus angepasst.

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
- **Mandantendetails:** Enthält Informationen wie Ihre MDM-Autorität, die insgesamt bei Ihrem Mandanten angemeldeten Geräte und Ihre Lizenzzähler. In diesem Abschnitt wird auch die aktuelle Dienstversion für Ihren Mandanten angezeigt.
- **Connectorstatus:** Enthält Informationen zu konfigurierten Connectors wie Apple VPP, Windows Store for Business und Zertifikatconnectors. Basierend auf ihrem aktuellen Zustand werden die Connectors als *Fehlerfrei*, *Warnung* oder *Fehlerhaft* gekennzeichnet.
- **Intune Service Health:** Enthält aktive Vorfälle oder Ausfälle für Ihren Mandanten. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen ([https://portal.office.com](https://portal.office.com)).
- **Intune-News** (Neuigkeiten zu Intune): Enthält aktive Nachrichten für Ihren Mandanten wie Benachrichtigungen, dass Ihr Mandant die neuesten Intune-Features erhalten hat. Die Informationen in diesem Abschnitt werden direkt über das Office-Nachrichtencenter abgerufen ([https://portal.office.com](https://portal.office.com)).


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



