---
title: Early Edition – Microsoft Intune
titlesuffix: ''
description: Early Edition für Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
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
ms.openlocfilehash: d50925d9f5422e1bfea01869233c63d6a2889109
ms.sourcegitcommit: 12f8b7f0bca1baa2c1f68dd6af4f16a4814daa11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737501"
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
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>Ausführung von PowerShell-Skripts auf einem 64-Bit-Host auf 64-Bit-Geräten<!-- 1862675  -->
Wenn Sie ein PowerShell-Skript zu einem Gerätekonfigurationsprofil hinzufügen, wird das Skript immer im 32-Bit-Modus ausgeführt, auch auf einem 64-Bit-Betriebssystem. Seit diesem Update kann ein Administrator das Skript auf einem 64-Bit-Gerät auf einem 64-Bit-Host von PowerShell ausführen (**Gerätekonfiguration** > **PowerShell-Skripts** > **Hinzufügen** > **Konfigurieren** > **Skript in 64-Bit-PowerShell-Host ausführen**).
Weitere Informationen zur Verwendung von PowerShell finden Sie unter [Verwalten von PowerShell-Skripts in Intune für Windows 10-Geräte](intune-management-extension.md).
Gilt für: Windows 10 und höher

### <a name="rename-an-enrolled-windows-device----1911112----"></a>Umbenennen eines registrierten Windows-Geräts <!-- 1911112  -->
Sie können ein registriertes Windows 10-Gerät (RS4 oder höher) umbenennen. Navigieren Sie hierfür zu **Intune** > **Geräte** > **Alle Geräte**, wählen Sie ein Gerät aus, und klicken Sie auf **Gerät umbenennen**.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>Zuweisen von SCEP-Zertifikaten zu einem macOS-Gerät ohne Benutzer <!-- 2340521   -->
Sie können SCEP-Zertifikate (Simple Certificate Enrollment-Protokoll) zu einem macOS-Gerät ohne Benutzer zuweisen und das Zertifikat WLAN- oder VPN-Profilen zuordnen. Dadurch wird das vorhandene Feature zum [Zuweisen von Zertifikaten zu Windows-, iOS- oder Android-Geräten ohne Benutzer](certificates-scep-configure.md#create-a-scep-certificate-profile) erweitert.

### <a name="intune-conditional-access-ui-update------2432313----"></a>Update der Intune-Benutzeroberfläche für den bedingten Zugriff <!-- 2432313  -->
Wir haben die Benutzeroberfläche für den bedingten Zugriff über die Intune-Konsole verbessert. Dazu gehören:
- Das Intune-Blatt *Bedingter Zugriff* wurde durch das entsprechende Blatt aus Azure Active Directory ersetzt. Dadurch wird sichergestellt, dass Sie alle Einstellungen und Konfigurationen für den bedingten Zugriff (eine Technologie von Azure AD) nutzen können.
- Richten Sie den *Exchange-Dienstconnector* für das aktuelle Blatt *Lokaler Zugriff* ein. Das Blatt wird außerdem in *Exchange-Zugriff* umbenannt. Dadurch ändert sich der Ort, an dem Sie Details zu Exchange (online und lokal) konfigurieren und überwachen.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Verwendung von Google Play Protect-APIs für Android-Geräte in Intune <!-- 2577355  -->
Manche IT-Administratoren arbeiten in einer Bring Your Own Device-Umgebung (BYOD), in der manche Endbenutzer ihre Mobiltelefone möglicherweise rooten oder jailbreaken. Viele Benutzer handeln zwar nicht in schlechter Absicht, dennoch kann dieses Verhalten dazu führen, dass viele Intune-Richtlinien umgangen werden, die zum Schutz der Organisationsdaten auf dem Gerät des Endbenutzers eingerichtet wurden. Deshalb enthält Intune eine Erkennung von Rooting und Jailbreaks für registrierte und nicht registrierte Geräte. Ab diesem Release verwendet Intune die Google Play Protect-APIs, um die bisherigen Überprüfungen auf Rooting für nicht registrierte Geräte zu ergänzen. Google stellt zwar nicht alle Überprüfungsmechanismen für Rooting zur Verfügung, aber diese APIs sollten dennoch Benutzer ermitteln können, die Ihre Geräte abweichend von der Gerätekonfiguration gerootet haben, um neuere Betriebssystemupdates für ältere Geräte zu erhalten. Diesen Benutzern kann der Zugriff auf Unternehmensdaten verwehrt werden, oder ihre Unternehmenskonten können aus den Apps entfernt werden, für die Richtlinien aktiviert sind. Es wurden zudem einige Updates für die Berichterstellung auf dem Blatt „Intune-App-Schutz“ vorgenommen, um IT-Administratoren die Arbeit zu erleichtern: Der Bericht „Gekennzeichnete Benutzer“ enthält die Benutzer, die durch eine Überprüfung mit der SafetyNet-API von Google Play Protect ermittelt wurden, und der Bericht „Potentially Harmful Apps“ (Potenziell schädliche Apps) enthält die Apps, die durch eine Überprüfung mit der Verify Apps-API von Google ermittelt wurden. Dieses Feature ist unter Android verfügbar. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>Informationen zu Win32-Apps auf dem Blatt „Problembehandlung“ <!-- 2617342    -->
Sie können Protokolldateien zu Fehlern bei der Installation von Win32-Apps über das Blatt **Problembehandlung** der Intune-App abrufen. Weitere Informationen zur Behandlung von Problemen mit der App-Installation finden Sie unter [Problembehandlung bei der App-Installation](troubleshoot-app-install.md).

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>Ausführung von Kioskbrowsern und Microsoft Edge-Browser-Apps auf Windows 10-Geräten im Kioskmodus <!-- 2935135  -->
Sie können Windows 10-Geräte im Kioskmodus verwenden, um eine oder mehrere Apps auszuführen. Durch dieses Update wurden unter anderem folgende Änderungen an der Verwendung von Browser-Apps im Kioskmodus vorgenommen:

- Der Microsoft Edge-Browser und der Kioskbrowser können nun als ausführbare Apps zu Kioskgeräten hinzugefügt werden (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) bzw. **Kiosk** (Profiltyp)).
- Microsoft Edge kann eingeschränkt werden, damit der Browser im Kioskmodus ausgeführt werden kann (oder nicht) (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **Windows 10 und höher** (Plattform) bzw. **Geräteeinschränkungen** (Profiltyp) > **Microsoft Edge-Browser**). Wenn Microsoft Edge nicht im Kioskmodus ausgeführt wird, können die Einstellungen vom Endbenutzer geändert werden.

Eine Liste der aktuellen Einstellungen finden Sie unter:

- [Geräteeinstellungen bei Windows 10 (und höher) zur Ausführung als Kiosk in Intune](kiosk-settings-windows.md)
- [Microsoft Edge-Browser](device-restrictions-windows-10.md#microsoft-edge-browser)

Gilt für: Windows 10 und höher

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Automatisches Zuweisen von Bereichstags zu Ressourcen, die von einem Administrator für diesen Bereich erstellt wurden <!-- 3173823  -->
Wenn ein Administrator eine Ressource erstellt, werden alle Bereichstags, die dem Administrator zugewiesen sind, automatisch auch den neuen Ressourcen zugewiesen.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>Neue Einstellungen für Einschränkungen für iOS- und macOS-Geräte <!-- 3448774 -->
Sie können einige Einstellungen und Features auf iOS- und macOS-Geräten einschränken (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** bzw. **macOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)). Durch dieses Update können Sie weitere Features und Einstellungen konfigurieren. Sie können unter anderem die Bildschirmzeit festlegen, eSIM-Einstellungen und Mobilfunkpläne ändern, Softwareupdates später für Benutzer bereitstellen oder das Content Caching blockieren.
Weitere Informationen zu den derzeit einschränkbaren Features und Einstellungen finden Sie unter:
- [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md)
- [Einstellungen für Geräteeinschränkungen für macOS-Geräte in Microsoft Intune](device-restrictions-macos.md)

Gilt für:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>Bericht für fehlgeschlagene Registrierungen wurde auf das Blatt „Geräteregistrierung“ verschoben <!-- 3560202 -->
Der Bericht zu **fehlgeschlagenen Registrierungen** wird in den Abschnitt **Überwachen** des Blatts **Geräteregistrierung** verschoben. Zudem wurden zwei neue Spalten („Enrollment Method“ (Registrierungsmethode) und „Betriebssystemversion“) hinzugefügt.

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>Änderung von „Kiosk“ in „Dedizierte Geräte“ <!-- 3598402  -->
Die Option **Kiosk** wird in **Dedizierte Geräte** geändert, damit sie mit der Android-Terminologie übereinstimmt. Sie finden die Option in den Gerätekonfigurationsprofilen unter **Android Enterprise** > **Gerätebesitzer** > **Geräteeinschränkungen**.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>iOS-Einstellungen für die Anzeige von Softwareupdates für Safari und Delaying werden auf der Intune-Benutzeroberfläche verschoben <!-- 3640850, , 3803313  -->
Für iOS-Geräte können Sie Safari-Einstellungen festlegen und Softwareupdates konfigurieren. Mit diesem Update werden diese Einstellungen auf der Intune-Benutzeroberfläche verschoben:

- Die Safari-Einstellungen wurden von **Safari** (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp)) zu **Integrierte Apps** verschoben. 
- Die Einstellung **Delaying user software update visibility for supervised iOS devices** (Sichtbarkeit von Updates für Benutzer von überwachten iOS-Geräten verzögern) (**Softwareupdates** > **Richtlinien für iOS aktualisieren**) wird zu **Geräteeinschränkungen** > **Allgemein** verschoben.

Eine Liste der aktuellen Einstellungen finden Sie unter [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md) und [Konfigurieren von iOS-Updaterichtlinien in Intune](software-updates-ios.md).

Gilt für: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>Umbenennung von „Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)“ auf iOS-Geräten in „Bildschirmzeit (nur überwacht)“ <!-- 3699164  -->
Sie können die Einstellung **Aktivieren von Einschränkungen in den Geräteeinstellungen (nur überwacht)** für überwachte iOS-Geräte (**Gerätekonfiguration** > **Profile** > **Neues Profil** > **iOS** (Plattform) > **Geräteeinschränkungen** (Profiltyp) > **Allgemein**) konfigurieren. Mit diesem Update wurde die Einstellung in **Bildschirmzeit (nur überwacht)** umbenannt. Das Verhalten ändert sich nicht. Genauer gesagt: 

- iOS 11.4.1 und früher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltenden Einschränkungen in den Geräteeinstellungen bearbeiten. 
- iOS 12.0 und höher: Durch die Option **Blockieren** kann verhindert werden, dass Endbenutzer die für sie geltende **Bildschirmzeit** (einschließlich Einschränkungen von Inhalt und Datenschutz) in den Geräteeinstellungen bearbeiten. Auf Geräten, auf denen mindestens iOS 12.0 ausgeführt wird, wird die Registerkarte „Einschränkungen“ in den Geräteeinstellungen nicht mehr angezeigt. Diese Einstellungen befinden sich unter **Bildschirmzeit**. 

Eine Liste der aktuellen Einstellungen finden Sie in den [iOS-Geräteeinstellungen zum Zulassen oder Einschränken von Funktionen mit Intune](device-restrictions-ios.md).

Gilt für: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>Details zum Status von iOS-Apps <!-- 3761235  -->
Es wurden neue Fehlermeldungen eingeführt, die bei folgenden Problemen bei der Installation von Apps ausgelöst werden:
- Fehler beim Installieren von VPP-Apps auf gemeinsam genutzten iPads
- Fehler bei deaktiviertem App Store
- Fehler beim Suchen von VPP-Lizenzen für Apps
- Fehler beim Installieren von System-Apps mit MDM-Anbietern
- Fehler beim Installieren von Apps, wenn das Gerät sich im Kioskmodus oder im Modus für verlorene Geräte befindet
- Fehler beim Installieren von Apps wenn der Benutzer nicht im App Store angemeldet ist

Navigieren Sie in Intune zu **Client-Apps** > **Apps** > Name der App > **Geräteinstallationsstatus**. Die neuen Fehlermeldungen werden in der Spalte **Statusdetails** angezeigt.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Bereitstellung von online lizenzierten Microsoft Store für Unternehmen-Apps <!-- 1672660  -->
Sie können die erforderlichen, online lizenzierten Microsoft Store für Unternehmen-Apps im Gerätekontext zuweisen. Wenn Sie eine Microsoft Store für Unternehmen-App auf diese Weise bereitstellen, kann die App für alle Benutzer auf dem Gerät installiert werden. Dies gilt nur für Windows 10 RS4-Desktopgeräte und höher. Die Option zur Installation im Gerätekontext ist auf der Seite für die Zuweisung von Client-Apps für online lizenzierte Microsoft Store für Unternehmen-Apps verfügbar.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE-App-Bereitstellung <!-- 1171203 -->
Für Android-Geräte in einem Bereitstellungsszenario mit einer nicht registrierten App-Schutzrichtlinie ohne Registrierung (App Protection Policy Without Enrollment, APP-WE) können Sie mit verwaltetem Google Play Store-Apps und branchenspezifische Apps für Benutzer bereitstellen. Insbesondere kann die IT-Abteilung Endbenutzern einen App-Katalog bieten und für einen Installationsvorgang sorgen, in dem Endbenutzer nicht mehr den Sicherheitsstatus ihrer Geräte kompromittieren müssen, indem sie Installationen aus unbekannten Quellen zulassen. Darüber hinaus sorgt dieses Bereitstellungsszenario für höhere Benutzerfreundlichkeit.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Authentifizierungsmethode für Intune-Richtlinienupdate und Installation der Unternehmensportal-App  <!-- 1927359 -->
Bei Geräten, die bereits mithilfe des Setup-Assistenten über eine der Methoden von Apple für die Registrierung von Unternehmensgeräten registriert wurden, unterstützt Intune das Unternehmensportal nicht mehr, wenn es manuell von Endbenutzern aus dem App-Store installiert wurde. Diese Änderung ist nur relevant, wenn Sie sich während der Registrierung mit dem Setup-Assistenten von Apple authentifizieren. Diese Änderung wirkt sich nur auf iOS-Geräte aus, die registriert werden über:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

Wenn Benutzer die Unternehmensportal-App aus dem App Store installieren und dann versuchen, diese Geräte darüber zu registrieren, erhalten sie eine Fehlermeldung. Es wird vorausgesetzt, dass diese Geräte die Unternehmensportal-App nur dann verwenden, wenn sie während der Registrierung automatisch von Intune per Push übertragen wird. Registrierungsprofile in Intune im Azure-Portal werden aktualisiert, sodass Sie angeben können, wie sich Geräte authentifizieren, und ob sie die Unternehmensportal-App erhalten. Wenn Sie wünschen, dass Ihre DEP-Gerätebenutzer die Unternehmensportal-App verwenden, müssen Sie Ihre Einstellungen in einem Registrierungsprofil angeben. Darüber hinaus wird der Bildschirm **Identifizieren Sie Ihr Gerät** in der Unternehmensportal-App bald veraltet sein.  
Um die Unternehmensportal-App auf bereits registrierten DEP-Geräten zu installieren, müssen Sie zu „Intune“ > „Client-Apps“ wechseln und sie als verwaltete App mit App-Konfigurationsrichtlinien mithilfe von Push übertragen. Nähere Informationen zu diesen Schritten erhalten Sie in zukünftigen Dokumentationen.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrative Vorlagen stehen als Public Preview zur Verfügung und werden in ihr eigenes Konfigurationsprofil verschoben <!-- 3322847 -->
Administrative Vorlagen in Intune (**Gerätekonfiguration** > **Administrative Vorlagen**) stehen derzeit als Public Preview zur Verfügung. Mit diesem Update: Administrative Vorlagen umfasst über 300 Einstellungen, die in Intune verwaltet werden können. Diese Einstellungen waren zuvor nur im Gruppenrichtlinien-Editor vorhanden.
Administrative Vorlagen stehen als Public Preview zur Verfügung und werden von **Gerätekonfiguration** > **Administrative Vorlagen** verschoben. Gehen Sie zukünftig wie folgt vor, um administrative Vorlagen aufzurufen: **Gerätekonfiguration** > **Profile** >**Profil erstellen**, wählen Sie für **Plattform** **Windows 10 und höher** und für **Profiltyp** **Administrative Vorlagen** aus.
Berichterstellung wird aktiviert. Gilt für: Windows 10 und höher

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Dunkler Modus für Intune macOS-Unternehmensportal <!-- 3300524 -->
Das Intune macOS-Unternehmensportal unterstützt ab sofort den dunklen Modus für macOS. Wenn Sie den dunklen Modus auf einem Gerät mit macOS 10.14 und höher aktivieren, wird das Unternehmensportal an die Farben dieses Modus angepasst.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>App-Schutzrichtlinieneinstellungen (APP) für Webdaten <!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-Token, das von einer anderen MDM-Software verwendet wird <!-- 1488946 -->
Intune erkennt und zeigt Details an, wenn ein VPP-Token (Apple Volume Purchase Program) von Intune und einer anderen MDM-Software verwendet wird.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Abgekoppelte Geräte im Gerätekonformitätsdashboard <!-- 1981119 -->
In einem zukünftigen Update werden abgekoppelte Geräte aus dem Gerätekonformitätsdashboard entfernt. Dadurch werden Ihre Konformitätsnummern geändert.

## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).