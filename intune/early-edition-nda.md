---
title: Early Edition – Microsoft Intune
titlesuffix: ''
description: Early Edition für Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/09/2019
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
ms.openlocfilehash: 0efc84da6a9efb594600b9ca33aa5eb7622c8101
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203432"
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

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Bereitstellung von online lizenzierten Microsoft Store für Unternehmen-Apps <!-- 1672660  -->
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

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Das Intune App SDK unterstützt 256-Bit-Verschlüsselungsschlüssel <!-- 1832174 -->
Das Intune App SDK für Android verwendet 256-Bit-Verschlüsselungsschlüssel, wenn die Verschlüsselung durch App-Schutzrichtlinien aktiviert ist. Das SDK bietet zur Kompatibilität mit Inhalten und Apps, die ältere SDK-Versionen verwenden, weiterhin Unterstützung der 128-Bit-Schlüssel.


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


### <a name="additional-settings-for-outlook----3301182---"></a>Zusätzliche Einstellungen für Outlook <!-- 3301182 -->
Sie können nun zusätzliche Einstellungen für Outlook für iOS und Android mit Intune konfigurieren.  Sie können folgende Einstellungen vornehmen:
- Lassen Sie nur die Verwendung von Geschäfts-, Schul- oder Unikonten in Outlook in iOS und Android zu.
- Stellen sie eine moderne Authentifizierung für Office 365 und eine hybride moderne Authentifizierung für lokale Konten bereit.
- Verwenden Sie `SAMAccountName` für das Feld „Benutzername“ im E-Mail-Profil, wenn die Basisauthentifizierung aktiviert ist.
- Ermöglichen Sie das Speichern von Kontakten.
- Konfigurieren Sie E-Mail-Infos von externen Empfängern.
- Konfigurieren Sie **Posteingang mit Relevanz**.
- Erfordern Sie biometrische Daten für den Zugriff auf Outlook für iOS. 
- Blockieren Sie externe Bilder.

> [!NOTE]
> Wenn Sie die Richtlinien für den Intune-App-Schutz zur Verwaltung des Zugriffs auf Unternehmensidentitäten verwenden, sollten Sie ggf. nicht aktivieren, dass **biometrische Daten erforderlich** sind. Weitere Informationen finden Sie unter **Unternehmensanmeldeinformationen für Zugriff erforderlich** für [iOS-Zugriffsanforderungen](app-protection-policy-settings-ios.md#access-settings) und [Android-Zugriffsanforderungen](app-protection-policy-settings-android.md#access-settings).

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und werden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->
Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update: Administrative Vorlagen umfasst über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
Administrative Vorlagen stehen als Public Preview zur Verfügung und werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** >**Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
Berichterstellung wird aktiviert. Gilt für: Windows 10 und höher

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Dunkler Modus für Intune macOS-Unternehmensportal <!-- 3300524 -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Erscheinungsbild des Unternehmensportals an die Farben für diesen Modus angepasst.

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines <!-- 2055484 -->
Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

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



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Überprüfen des Configuration Manager auf Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher



## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



