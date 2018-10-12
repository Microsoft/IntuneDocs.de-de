---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f6447f4a5cfb2638278a59414e83f744adb8c81
ms.sourcegitcommit: ed97b68f08c1a8469f0b45bc1c839a0b5f5c71e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "45978262"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Die Early Edition für Microsoft Intune – September 2018

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>Benutzerkontozugriff von Intune-Apps auf verwalteten Android- und iOS-Geräten <!-- ! 1248496  -->

Wie der Microsoft Intune-Administrator werden Sie steuern können, welche Benutzerkonten Microsoft Office-Anwendungen auf verwalteten Geräten hinzugefügt werden. Sie werden den Zugriff auf zulässige Organisationsbenutzerkonten beschränken und persönliche Konten auf registrierten Geräten blockieren können. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Erstellen von DNS-Suffixen in VPN-Konfigurationsprofilen auf Geräten mit Windows 10 <!-- 1333668 -->
Beim Erstellen eines VPN-Gerätekonfigurationsprofils (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** Plattform > **VPN**-Profiltyp) geben Sie DNS-Einstellungen ein. Sie werden auch mehrere **DNS-Suffixe** in Intune eingeben können. Wenn Sie DNS-Suffixe verwenden, können Sie nach einer Netzwerkressource mithilfe ihres Kurznamens anstelle des vollqualifizierten Domänennamens (Fully Qualified Domain Name, FQDN) suchen. Mit diesem Update können Sie auch die Reihenfolge der DNS-Suffixe in Intune ändern.
In [VPN-Einstellungen für Windows 10](vpn-settings-windows-10.md#dns-settings) sind die aktuellen DNS-Einstellungen aufgeführt.
Gilt für: Windows 10-Geräte

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Unterstützung für Always On-VPN für Android-Enterprisearbeitsprofile <!-- 1333705 -->
Sie können Always On-VPN-Verbindungen auf Android-Enterprisegeräten mit verwalteten Arbeitsprofilen verwenden. Always On-VPN-Verbindungen bleiben erhalten oder werden sofort wieder hergestellt, wenn der Benutzer sein Gerät entsperrt, wenn das Gerät neu gestartet wird oder das drahtlose Netzwerk sich ändert. Sie können die Verbindung auch in den „Sperrmodus“ setzen, der den gesamten Netzwerkdatenverkehr blockiert, bis die VPN-Verbindung aktiv ist.
Die Always On-VPN-Einstellung wird in **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Android Enterprise** für Plattform > **Geräteeinschränkungen** unter **Nur Arbeitsprofile** für Profiltyp > **Konnektivitätseinstellungen** vorgenommen. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Konfigurationsrichtlinie für Outlook für iOS und Android-App <!--1828527 -->
Sie können eine Konfigurationsrichtlinie für Outlook für iOS und Android-Apps erstellen. Zusätzliche Konfigurationseinstellungen werden hinzugefügt, sobald sie für Outlook für iOS und Android aktiviert werden.

###  <a name="windows-line-of-business-lob-app-file-extensions----1884873---"></a>Dateierweiterungen branchenspezifischer Windows-Apps (LOB-Apps) <!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps umfassen *.msi*, *.appx*, *.appxbundle*, *.msix* und *.msixbundle*. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Client-Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird angezeigt. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>Remotesperren nicht konformer Geräte <!-- 2064495 -->
Wenn ein Gerät nicht konform ist, werden Sie eine Aktion in der Konformitätsrichtlinie erstellen können, die das Gerät remote sperrt. Erstellen Sie in Intune > **Gerätekonformität** eine neue Richtlinie, oder wählen Sie eine vorhandene Richtlinie aus. Wählen Sie **Aktionen bei Inkompatibilität** > **Hinzufügen** und dann das Remotesperren des Geräts aus.
Unterstützt auf: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 und höher 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Intune-APP-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten <!-- 2244713 -->
Sie werden die Steuerung der Intune-APP-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten von der Angabe der Identität des registrierten Benutzers trennen können. Administratoren, die IntuneMAMUPN nicht verwenden, werden keine Verhaltensänderung feststellen. Wenn diese Funktion verfügbar ist, sollten Administratoren, die mit IntuneMAMUPN das Datenübertragungsverhalten auf registrierten Geräten steuern, die neuen Einstellungen überprüfen und ihre APP-Einstellungen nach Bedarf aktualisieren.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Verwenden eines vorinstallierten Schlüssels in einem Windows 10-WLAN-Profil <!-- 2662938 -->
Sie werden einen vorinstallierten Schlüssel (Pre-Shared Key, PSK) mit dem WPA/WPA2-Personal-Sicherheitsprotokoll verwenden können, um ein WLAN-Konfigurationsprofil für Windows 10 zu authentifizieren.
Derzeit müssen Sie ein WLAN-Profil importieren oder ein benutzerdefiniertes Profil erstellen, um einen vorinstallierten Schlüssel zu verwenden. [WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune](wi-fi-settings-windows.md) werden die aktuellen Einstellungen aufgeführt. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995-eeready---"></a>App-Schutzrichtlinieneinstellungen (APP) für Webdaten <!-- 2662995 eeready -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Erhöhen der Synchronisierungshäufigkeit von Autopilot-Geräten auf alle 12 Stunden <!-- 2753673 -->
Autopilot-Geräte werden alle 12 Stunden statt alle 24 Stunden synchronisiert.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Anwenden des Autopilot-Profils auf Win 10-Geräte, die noch nicht für Autopilot registriert sind <!-- 1558983 -->
Sie können Autopilot-Profile auf registrierte Win 10-Geräte anwenden, die noch nicht für Autopilot registriert sind. Wählen Sie im Autopilot-Profil die Option **Alle Zielgeräte in Autopilot-Geräte konvertieren** aus, um Nicht-Autopilot-Geräte automatisch mit dem Autopilot-Bereitstellungsdienst zu registrieren. Die Verarbeitung der Registrierung kann 48 Stunden dauern. Wenn die Registrierung des Geräts aufgehoben und es zurückgesetzt ist, stellt Autopilot es bereit. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>Erstellen und Zuweisen mehrerer Registrierungsstatus-Seitenprofile für Azure AD-Gruppen <!-- 2526564-->
Sie werden mehrere Registrierungsstatus-Seitenprofile für Azure AD-Benutzergruppen erstellen und zuweisen können.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Updates der Intune-Angebotsseite und Umbenennen von Knoten <!--2867309 -->
Updates der Intune-Angebotsseite enthalten neue und geänderte Überwachungskacheln und Diagramme für eine bessere Visualisierung von Daten. Der Knoten **Mobile Apps** ändert sich in **Client-Apps**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Höherer Endbenutzerzugriff über die Unternehmensportal-App <!-- 772203 -->
Endbenutzer werden mit der Unternehmensportal-App auf wichtige Kontoaktionen wie das Zurücksetzen des Kennworts und ihres AAD-Profils zugreifen können.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Ausstellen von SCEP-Zertifikaten für Geräte ohne Benutzer <!-- 1744554 -->
Derzeit werden Zertifikate an Benutzer ausgegeben. Sie werden SCEP-Zertifikate für Geräte, einschließlich benutzerlose Geräte wie z.B. Kioske, ausstellen können (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** für Plattform > **SCEP-Zertifikat** für Profil). Andere Updates werden Folgendes beinhalten:
- Die **Betreff**-Eigenschaft in einem SCEP-Profil ist nun ein benutzerdefiniertes Textfeld und kann neue Variablen enthalten. 
- Die **Alternativer Antragstellername**-Eigenschaft (Subject Alternative Name, SAN) in einem SCEP-Profil ist nun ein Tabellenformat und kann neue Variablen enthalten. In der Tabelle kann ein Administrator ein Attribut hinzufügen und den Wert in einem benutzerdefinierten Textfeld ausfüllen. Der SAN unterstützt die folgenden Attribute: 
  - DNS
  - E-Mail-Adresse
  - UPN: Diese neuen Variablen können mit statischem Text in einem benutzerdefinierten Werttextfeld hinzugefügt werden. Beispielsweise kann das DNS-Attribut als `DNS = {{AzureADDeviceId}}.domain.com` hinzugefügt werden.
  > [!NOTE]
  > Geschweifte Klammern, Semikolons und Pipesymbole „{}; |“ funktionieren nicht im statischen SAN-Text. Geschweifte Klammern dürfen nur eine der neuen Gerätezertifikatvariablen umschließen, die entweder für `Subject` oder `Subject alternative name` akzeptiert werden. Neue Gerätezertifikatvariablen:  
```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` funktioniert nur für Windows und in die Domäne eingebundene Geräte. 
>  -  Bei der Angabe von Geräteeigenschaften wie IMEI, Seriennummer und vollständig qualifiziertem Domänennamen im Betreff oder SAN für ein Gerätezertifikat achten Sie unbedingt darauf, dass diese Eigenschaften von einer Person mit Zugriff auf das Gerät gespooft sein könnten. 

[SCEP-Zertifikatprofil erstellen](certificates-scep-configure.md#create-a-scep-certificate-profile) listet beim Erstellen eines SCEP-Konfigurationsprofils die aktuellen Variablen auf. 

Gilt für: Windows 10 und höher sowie iOS, für WLAN unterstützt



<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-Token, das von einer anderen MDM-Software verwendet wird <!-- 1488946 -->
Intune erkennt und zeigt Details an, wenn ein VPP-Token (Apple Volume Purchase Program) von Intune und einer anderen MDM-Software verwendet wird.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS-Versionsnummer und Buildnummer werden angezeigt <!-- 1892471 -->
Unter **Gerätekompatibilität** > **Gerätekompatibilität** wird die iOS-Betriebssystemversion angezeigt. In einem zukünftigen Update wird auch die Buildnummer angezeigt.
Wenn Sicherheitsupdates veröffentlicht werden, bleibt die Versionsnummer von Apple in der Regel unverändert bestehen, die Buildnummer wird jedoch aktualisiert. Durch Anzeigen der Buildnummer können Sie einfach überprüfen, ob ein Sicherheitsupdate installiert wird.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Abgekoppelte Geräte im Gerätekonformitätsdashboard <!-- 1981119 -->
In einem zukünftigen Update werden abgekoppelte Geräte aus dem Gerätekonformitätsdashboard entfernt. Dadurch werden Ihre Konformitätsnummern geändert.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Änderungen im Updateprozess für lokale Connectors <!-- 2277554 -->
Auf Grundlage von Kundenfeedback wird die Art und Weise, wie Updates für lokale Connectors ausgeführt werden, geändert. Nachdem Sie erstmalig einen lokalen Connector installiert haben, werden Updates automatisch ausgeführt. Diese Änderung beginnt mit dem neuen PFX Certificate Connector für Microsoft Intune und wird dann langsam auf andere Typen lokaler Connectors ausgeweitet. 

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Windows 10 und höher: Verbesserungen des Kioskprofils im Azure-Portal <!-- 2748224 eeready -->
Das Windows 10-Kiosk-Gerätekonfigurationsprofil (**Gerätekonfiguration** > **Profile** > **Profil erstellen**  >  **Windows 10 und höher** für Plattform > **Kioskvorschau** für Profiltyp) wird verbessert: 
- Derzeit können Sie mehrere Kioskprofile auf demselben Gerät erstellen. Ab diesem Update unterstützt Intune nur ein Kioskprofil pro Gerät. Wenn Sie noch mehrere Kioskprofile auf einem einzelnen Gerät benötigen, können Sie einen benutzerdefinierten URI verwenden.
– In einem **Multi-App-Kioskprofil** können Sie die Anwendungskachelgröße und Reihenfolge für das **Startmenülayout** im Raster der Anwendung auswählen. Wenn Sie eine umfassendere Anpassung bevorzugen, können Sie weiterhin eine XML-Datei hochladen.
- Die Kioskbrowsereinstellungen werden in die **Kiosk**-Einstellungen verschoben. Derzeit haben die **Kioskwebbrowser**-Einstellungen ihre eigene Kategorie im Azure-Portal.
Gilt für: Windows 10 und höher

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Verbesserungen an den Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager <!-- 675800 -->
Wenn ein Geräteregistrierungs-Manager (DEM) sich in der Unternehmensportal-App für Windows anmeldet, listet die App nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserungen werden Timeouts vermindert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte zu laden.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Überprüfen des Configuration Manager auf Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und wenn die Lizenzen für das Unternehmensportal knapp werden.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Zusätzliche Sicherheitseinstellungen für Windows Installer <!-- 2282430 -->
Sie werden Benutzern erlauben können, App-Installationen zu steuern. Wenn diese Option aktiviert ist, werden Installationen, die normalerweise wegen Sicherheitsverstößen unterbrochen werden würden, weiterhin ausgeführt. Sie werden festlegen können, dass Windows Installer bei der Installation eines beliebigen Programms auf einem System erhöhte Berechtigungen verwendet. Zusätzlich werden Sie festlegen können, dass Windows Information Protection-Elemente (WIP) indiziert und die zugehörigen Metadaten an einem nicht verschlüsselten Speicherort gespeichert werden. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente weder indiziert noch in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Diese Optionen sind standardmäßig deaktiviert. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können zukünftig auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator werden Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen können, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Anfordern der nicht biometrischen Identifikation nach angegebenem Timeout <!-- 1506985 --> 

Durch die erzwungene Verwendung einer nicht biometrischen PIN nach einem vom Administrator festgelegten Zeitraum wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, mobile Anwendungsverwaltung) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aktualisieren der „Hilfe und Feedback“-Oberfläche in der Unternehmensportal-App für Android <!--1631531 -->

Die „Hilfe und Feedback“-Benutzeroberfläche in der Unternehmensportal-App für Android wird zukünftig aktualisiert, um den Best Practices für Android-Apps zu entsprechen. Die Unternehmensportal-App für Android wird in den nächsten Monaten aktualisiert. Das **Hilfe und Feedback**-Menüelement wird in die Menüelemente **Hilfe** und **Feedback senden** unterteilt. Auf der **Hilfe**-Seite wird es einen **Häufig gestellte Fragen**-Abschnitt und eine **E-Mail-Support**-Schaltfläche zum Hochladen von Protokollen an Microsoft und Senden von E-Mails an die Supportabteilung Ihres Unternehmens geben, in denen die Probleme beschrieben werden. Die Option **Feedback senden** führt den Benutzer durch den Standardprozess zur Feedbackübermittlung von Microsoft, in dem der Benutzer angeben kann, ob ihm etwas gefällt, nicht gefällt und Vorschläge machen kann.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



