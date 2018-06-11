---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745042"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Die Early Edition für Microsoft Intune (Juni 2018)

Die **Early Edition** enthält eine Liste der Funktionen, die in späteren Versionen von Microsoft Intune zur Verfügung stehen werden. Diese Informationen werden auf einer begrenzten Basis bereitgestellt, und Änderungen sind vorbehalten. Geben Sie diese Informationen nicht außerhalb Ihres Unternehmens weiter. Einige der hier aufgeführten Features werden möglicherweise bis zum Stichtag nicht fertig und werden erst in eine spätere Version aufgenommen. Andere Features werden in einer Pilotphase getestet (Test-Flighting), um sicherzustellen, dass sie für Kunden bereit sind. Wenden Sie sich mit Fragen oder Bedenken an den Ansprechpartner für Ihre Microsoft-Produktgruppe.

Diese Seite wird regelmäßig aktualisiert. Überprüfen Sie, ob weitere Updates vorliegen.

> [!Note]
>Die folgenden Änderungen sind in der Entwicklung für Intune. Weitere Informationen zu neuen Hybridfeatures finden Sie auf unserer [Seite mit neuen Hybridfeatures](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>COSU-Unterstützung (corporate-owned, single use, Unternehmensgeräte für spezifische Anwendungsfälle) für Android-Geräte <!-- 1630973 -->

Intune wird zukünftig kioskartige, stringent verwaltete Android-Geräte unterstützen, deren Einsatzbereich stark eingeschränkt ist. Dadurch können Administratoren festlegen, dass auf einem Gerät nur eine oder einige wenige Apps und Aktionen von Benutzern verwendet werden dürfen.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-Unterstützung für das Programm zur Geräteregistrierung von Apple<!-- 747651 -->

Intune wird zukünftig die Registrierung von macOS-Geräten über das Programm zur Geräteregistrierung (DEP) von Apple unterstützen. Gehen Sie hierzu folgendermaßen vor:

1. Weisen Sie unter deploy.apple.com einem MDM-Server die macOS-Seriennummern zu.
2. Importieren Sie die Seriennummern in Intune.
3. Erstellen Sie für das Registrierungsprogramm ein Profil, das auf macOS-Geräte abgestimmt ist.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Google-Namensänderungen für Android for Work und Play for Work <!--842873 -->
Intune wird zukünftig Android for Work-Terminologie aktualisieren, wenn sich Google-Markennamen ändern.  Die Benennungen „Android for Work“ und „Play for Work“ werden nicht mehr verwendet. Die Terminologie wird je nach Kontext angepasst:

- „Android Enterprise“ bezieht sich auf den allgemeinen modernen Android-Verwaltungsstapel.
- „Arbeitsprofil“ oder „Profilbesitzer“ bezieht sich auf BYOD-Geräte, die mit Arbeitsprofilen verwaltet werden.
- „Managed Google Play“ bezieht sich auf den App Store von Google.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Überwachen des Konfigurationsstatus von iOS-Apps auf allen Geräten <!-- 880037 eeready eestaged -->

Als Microsoft Intune-Administrator können Sie zukünftig auf jedem verwalteten Gerät den Konfigurationsstatus von iOS-Apps überwachen. Klicken Sie im Azure-Portal unter **Microsoft Intune** auf **Geräte** > **Alle Geräte**. Wählen Sie aus der Liste der verwalteten Geräte ein Gerät aus, für das ein Blatt angezeigt werden soll. Klicken Sie auf dem Geräteblatt auf **App-Konfiguration**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können zukünftig auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Erstellen von Konformitätsrichtlinien für macOS-Geräte über Firewalleinstellungen <!-- 1497640 -->
Beim Erstellen einer neuen macOS-Konformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: macOS** > **Systemsicherheit**) sind einige neue **Firewall**-Einstellungen verfügbar: 
- **Firewall:** Hier konfigurieren Sie, wie eingehende Verbindungen in Ihrer Umgebung behandelt werden.
- **Eingehende Verbindungen:** Mit dieser Einstellung können Sie eingehende Verbindungen für grundlegende Internetdienste wie DHCP, Bonjour und IPSec zulassen und alle anderen eingehenden Verbindungen **blockieren**. Alle Freigabedienste werden durch diese Einstellung blockiert.
- **Geschützter Modus:** Durch die **Aktivierung** dieser Einstellung hindern Sie das Gerät daran, auf Suchanforderungen zu antworten. Das Gerät antwortet weiterhin auf eingehende Anforderungen für autorisierte Apps.

Gilt für: macOS 10.12 und höher

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Verwenden von „sAMAccountName“ als Kontobenutzername für E-Mail-Profile <!-- 1500307 -->

Zukünftig können Sie das lokal vorhandene Attribut **sAMAccountName** als Kontobenutzername für Android-, iOS- und Windows 10-E-Mail-Profile verwenden. Mit den Attributen `domain` oder `ntdomain` können Sie in Azure Active Directory (Azure AD) außerdem die Domain abrufen. Alternativ können Sie auch eine benutzerdefinierte statische Domäne eingeben.

Zur Nutzung dieses Features müssen Sie das `sAMAccountName`-Attribut Ihrer lokalen Active Directory-Umgebung mit Azure AD synchronisieren.

Gilt für: Android, iOS, Windows 10 und höher

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts <!-- 1506985 -->

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, mobile Anwendungsverwaltung) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Zurücksetzen ausgewählter App-Daten einer Organisation <!-- 1507030 -->
Wenn die in den APP-Einstellungen festgelegten Bedingungen nicht erfüllt sind, können Administratoren zukünftig durch eine neue Aktion ausgewählte Organisationsdaten zurücksetzen.  Dieses Feature hilft Administratoren dabei, vertrauliche Organisationsdaten mithilfe festgelegter Kriterien automatisch zu schützen und aus Anwendungen zu entfernen.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Widerrufen einer Lizenz für iOS-Apps, die über VPP erworben wurden <!-- 1777384 -->
Als Microsoft Intune-Administrator haben Sie zukünftig die Möglichkeit, die Lizenz für eine bestimmte iOS-App zu widerrufen, die über das Volume Purchase Program (VPP) erworben wurde. Sie können Benutzer benachrichtigen, wenn ihnen eine App nicht mehr zugewiesen ist. Durch das Widerrufen einer App-Lizenz wird die zugehörige VPP-App nicht vom Gerät deinstalliert. Zum Deinstallieren einer VPP-App müssen Sie die Zuweisungsaktion in **Deinstallieren** ändern. Die Anzahl der widerrufenen Lizenzen wird innerhalb der Intune-**App**-Workload im Knoten **Lizenzierte Apps** angezeigt. Weitere Informationen zu iOS-VPP-Apps finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Widerrufen einer iOS-VPP-App-Lizenz <!-- 1863797 -->
Als Administrator haben Sie zukünftig die Möglichkeit, eine iOS-VPP-App-Lizenz zu widerrufen, die einem Benutzer oder Gerät zugewiesen ist. Dasselbe erreichen Sie mit der Deinstallation einer iOS-VPP-App. Anschließend können Sie die App-Lizenz einem anderen Benutzer oder Gerät zuweisen. Weitere Informationen zu iOS-VPP-App-Lizenzen, finden Sie unter [Verwalten von iOS-Apps, die über ein Volumenprogramm mit Microsoft Intune erworben wurden](vpp-apps-ios.md).

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968 -->
Die Unternehmensportalwebsite wird auf der Grundlage von Kundenfeedback um neue Features ergänzt. Dadurch werden auf Android-, iOS- und Windows-Geräten bereits vorhandene Funktionen verbessert, und die Benutzerfreundlichkeit erhöht sich. Bestimmte Bereiche der Website – z.B. Gerätedetails, Feedback und Support sowie die Geräteübersicht – werden mit einem neuen, modernen und dynamischen Design ausgestattet. Weiterhin sind enthalten:

- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- eine benutzerfreundlichere Sprache und weniger Fachbegriffe
- Möglichkeit, direkte Links zu Apps zu teilen
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Bearbeiten von Office 365 Pro Plus-App-Bereitstellungen <!-- 2150145 -->
Als Microsoft Intune-Administrator haben Sie zukünftig mehr Möglichkeiten, Ihre Office 365 Pro Plus-App-Bereitstellungen zu bearbeiten. Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps**. Wählen Sie aus der Liste der Apps Ihre Office 365 Pro Plus-Suite aus.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Duplikatprüfung auf Zeilenbasis beim Hochladen unternehmensspezifischer Gerätebezeichner <!-- 2203794 -->
Beim Hochladen von Unternehmensbezeichnern stellt Intune eine Liste mit mehrfach vorhandenen Bezeichnern bereit und bietet Ihnen die Möglichkeit, die vorhandenen Informationen zu ersetzen oder beizubehalten. Der Bericht wird angezeigt, wenn nach dem Klicken auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Bezeichner hinzufügen** Duplikate vorhanden sind. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Manuelles Hinzufügen von Unternehmensgerätebezeichnern <!-- 2203803 -->
Zukünftig können Sie Unternehmensgerätebezeichner manuell hinzufügen. Klicken Sie auf **Geräteregistrierung** > **Bezeichner von Unternehmensgeräten** > **Hinzufügen**.

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>Neue Status für Geräte in der Gerätekonfiguration <!-- 2308882 -->
Unter **Gerätekonfiguration** > **Übersicht** werden die folgenden neuen Status angezeigt:
- Erfolgreich
- Fehler
- Konflikt
- Ausstehend
- Nicht anwendbar. Außerdem wird eine Grafik angezeigt, in der die Anzahl der Geräte für andere Plattformen zu sehen ist. Beim Aufruf eines iOS-Profils wird beispielsweise auf der neuen Kachel die Anzahl der Nicht-iOS-Geräte angezeigt, die diesem Profil ebenfalls zugewiesen sind. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Unterstützung von Drittanbieter-Antivirenlösungen in Gerätekonformitätsrichtlinien <!-- 2325484 -->
Beim Erstellen einer Gerätekonformitätsrichtlinie (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Plattform: Windows 10 und höher** > **Einstellungen** > **Systemsicherheit**) sind neue Optionen für **Gerätesicherheit** verfügbar: 
- **Antivirus**: Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec) überprüfen, die beim Windows-Sicherheitscenter registriert sind. 
- **AntiSpyware**: Wenn für diese Einstellung **Require** (Erforderlich) festgelegt ist, können Sie die Konformität mit Anti-Spyware-Lösungen (beispielsweise Symantec) überprüfen, die beim Windows Security Center registriert sind. 

Gilt für: Windows 10 und höher 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Unterstützung für VPN-Profile für Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->

Mit diesem Update können Sie Palo Alto Networks GlobalProtect als VPN-Verbindungstyp für VPN-Profile in Intune auswählen (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Profiltyp** > **VPN**). Für dieses Release werden die folgenden Plattformen unterstützt: 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>Festlegen der Kompatibilität nach Gerätestandort <!-- 851881 ! -->
In einigen Situationen empfiehlt es sich, den Zugriff auf Unternehmensressourcen auf einen bestimmten Standort zu beschränken, der durch eine Netzwerkverbindung definiert ist. Sie können eine Kompatibilitätsrichtlinie (**Gerätekompatibilität** > **Standorte**) basierend auf der IP-Adresse des Geräts erstellen. Wird das Gerät außerhalb des IP-Bereichs bewegt, kann damit nicht auf Unternehmensressourcen zugegriffen werden.

Gilt für Android-Geräte 6.0 und höher mit der aktualisierten Unternehmensportal-App

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Verbesserte Problembehandlung für App-Installation <!-- 928990 -->
Auf Geräten, die mit Microsoft Intune MDM verwaltet werden, können App-Installationen manchmal fehlschlagen. In diesen Fällen kann es schwierig sein, die Fehlerursache zu verstehen oder das Problem zu beheben. Wir versenden eine öffentliche Vorschau unserer Features zur App-Problembehandlung. Unter jedem einzelnen Gerät wird ein neuer Knoten mit der Bezeichnung **Verwaltete Apps** angezeigt. Hier sind die Apps aufgelistet, die über Intune MDM übermittelt wurden. Innerhalb des Knotens wird eine Liste mit App-Installationsstatus angezeigt. Bei Auswahl einer einzelnen App wird die Problembehandlungsansicht für diese bestimmte App angezeigt. In der Problembehandlungsansicht sehen Sie den End-to-End-Lebenszyklus der App, z. B. wann die App erstellt, geändert, festgelegt und an ein Gerät übermittelt wurde. Darüber hinaus wird bei einer nicht erfolgreichen App-Installation der Fehlercode und eine hilfreiche Nachricht zur Ursache des Fehlers angezeigt.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts <!-- 1506985 --> 

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird zukünftig die Sicherheit von MAM-fähigen Apps durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockieren des App-Zugriffs basierend auf nicht genehmigten Geräteherstellern und Modellen <!-- 1425689 ! -->
Der Intune-IT-Administrator kann über Intune-App-Schutzrichtlinien die Umsetzung einer festgelegten Liste von Android-Herstellern und/oder iOS-Modellen erzwingen. Der IT-Administrator kann eine durch Semikolon getrennte Liste von Herstellern für Android-Richtlinien und Gerätemodelle für iOS-Richtlinien bereitstellen. Intune-App-Schutzrichtlinien gelten nur für Android und iOS. Für diese festgelegten Listen können zwei verschiedene Aktionen ausgeführt werden:
- Blockieren des App-Zugriffs auf Geräten, die nicht angegeben sind.
- Selektives Zurücksetzen von Unternehmensdaten auf Geräten, die nicht angegeben sind. 

Der Benutzer kann nicht auf die Zielanwendung zugreifen, wenn die Anforderungen der Richtlinie nicht erfüllt sind. Anhand von Einstellungen werden Benutzer entweder blockiert oder Unternehmensdaten innerhalb der App selektiv zurückgesetzt. Bei iOS-Geräten ist für dieses Feature die Beteiligung von Anwendungen erforderlich (d. h. WXP, Outlook, Managed Browser, Yammer), um das Intune App SDK zu integrieren und so die Mindestversionseinstellungen für die Zielanwendungen zu erzwingen. Diese Integration erfolgt fortlaufend und ist von den jeweiligen Anwendungsteams abhängig. Unter Android ist für dieses Feature das neueste Unternehmensportal erforderlich. 

Auf Endbenutzergeräten führt der Intune-Client Aktionen auf Grundlage eines einfachen Abgleichs der Zeichenfolgen aus, die auf dem Blatt „Intune“ für Anwendungsschutzrichtlinien angegeben sind. Dies hängt ausschließlich von dem Wert ab, den das Gerät meldet. Daher sollte der IT-Administrator sicherstellen, dass das beabsichtigte Verhalten korrekt ist. Dazu kann diese Einstellung basierend auf einer Vielzahl von Geräteherstellern und Modellen für eine kleine Benutzergruppe getestet werden. Wählen Sie in Microsoft Intune nacheinander **Mobile Apps** > **App-Schutzrichtlinien** aus, um App-Schutzrichtlinien anzuzeigen und hinzuzufügen. Weitere Informationen zu App-Schutzrichtlinien finden Sie unter [Was sind App-Schutzrichtlinien?](app-protection-policy.md)

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Aktivieren des Kioskmodus auf Windows 10-Geräten <!-- 1560072 ! -->
Auf Windows 10-Geräten können Sie ein Konfigurationsprofil erstellen und den Kioskmodus aktivieren (**Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10** > **Geräteeinschränkungen** > **Kiosk**). Bei diesem Update wurde die Einstellung **Kiosk (Vorschau)** in **Kiosk (veraltet)** umbenannt. **Kiosk (veraltet)** wird nicht mehr empfohlen, ist jedoch bis zum Juli-Update weiterhin funktionsfähig. **Kiosk (veraltet)** wird durch den neuen **Kiosk**-Profiltyp ersetzt (**Profil erstellen** > **Windows 10**  >  **Kiosk (Vorschau)**), der die Einstellungen zum Konfigurieren von Kiosks unter Windows 10 RS4 und höher enthält.

Gilt für Windows 10 und höher.

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Abrufen der zugeordneten App-Benutzermodell-ID (AUMID) für Apps im Microsoft Store für Unternehmen im Kioskmodus <!-- 1560077 ! -->
Intune kann die App-Benutzermodell-IDs (AUMIDs) für Apps im Microsoft Store für Unternehmen (Windows Store for Business, WSfB) abrufen, um eine verbesserte Konfiguration des Kioskprofils bereitzustellen.

Weitere Informationen zu Apps im Microsoft Store für Unternehmen finden Sie unter [Verwalten von Apps aus dem Microsoft Store für Unternehmen](windows-store-for-business.md).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Zugriff auf Aktionen für App-Schutzrichtlinien <!-- 1483510 EEready -->
Sie werden bald in der Lage sein, App-Schutzrichtlinien so zu konfigurieren, das nicht kompatible Geräte explizit zurückgesetzt, blockiert oder gewarnt werden. Mit der neuesten Aktion *Zurücksetzen* werden Ihre Unternehmensdaten von einem Gerät entfernt. Im Falle eines Zurücksetzens wird der Gerätebenutzer über den Grund für das Zurücksetzen und Schritte zur Wiederherstellung benachrichtigt. Für einige Einstellungen, wie z. B. die Mindestversion des Betriebssystems, können Sie mehrere Aktionen anwenden, z. B. das Blockieren und Zurücksetzen. Diese Aktionen werden ausgelöst, wenn die App gestartet wird.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Neue Inventurinformationen für Windows-Geräte <!-- 1333569 eeready -->

Für Windows-Geräte stehen die folgenden Inventurinformationen pro Gerät auf der Registerkarte **Hardware** bereit (**Gruppen** > **Alle mobilen Geräte** > **Geräte** > Gerät des Benutzers auswählen > **Eigenschaften anzeigen** > **Hardware**):
- TPM
- Antivirensoftware
- Antispyware
- Firewall
- UAC
- Akku
- Domänenname

Weitere Informationen dazu, wie diese Daten vom Konfigurationsdienstanbieter abgerufen werden, finden Sie unter den DeviceStatus-Einträgen im Artikel [DeviceStatus CSP (DeviceStatus-Konfigurationsdienstanbieter)](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune und der Microsoft Edge-Browser <!-- 1818969 -->
Der Microsoft Edge-Browser für mobile Geräte (iOS und Android) unterstützt nun Intune-App-Schutzrichtlinien. Benutzer, die sich mit ihren Azure AD-Unternehmenskonten bei der Edge-Browseranwendung anmelden, werden von Intune geschützt. 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Neue Einstellung für Sprache/Region beim Konfigurieren von OOBE für AutoPilot <!-- 1821766 -->
Es steht eine neue Konfigurationseinstellung zur Verfügung, mit der die Sprache und Region für AutoPilot-Profile während der Out-of-Box-Experience festgelegt werden kann.

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Neue Einstellung zum Konfigurieren der Gerätetastatur <!-- 1821768 -->
Es steht eine neue Einstellung zur Verfügung, mit der die Tastatur für AutoPilot-Profile während der Out-of-Box-Experience konfiguriert werden kann.

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Verwenden von TeamViewer zur Bildschirmübertragung zwischen iOS- und macOS-Geräten <!-- 1985547 -->
Derzeit können Sie TeamViewer zur Remoteverwaltung von [mit Intune verwalteten Android- und Windows-Geräten](device-profile-android-teamviewer.md) verwenden.

Administratoren können eine Verbindung mit TeamViewer herstellen und eine Bildschirmübertragungssitzung mit iOS- und macOS-Geräten starten. iPhone, iPad und macOS-Benutzer können ihre Bildschirme live an andere Desktops oder mobile Geräte übertragen. 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Benutzerdiagramm des Geräteprofils wieder vorhanden <!-- 2160133 -->
Während der Verbesserung der numerischen Werte, die im Diagramm des Geräteprofils dargestellt werden (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **(Übersicht)** ), wurde das Benutzerdiagramm vorübergehend entfernt.

Bei diesem Update ist das Benutzerdiagramm wieder enthalten und wird im Azure-Portal angezeigt.

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Zuweisen aller Benutzer und aller Geräte als Bereichsgruppen <!-- 2196803 -->
Sie können alle Benutzer, alle Geräte sowie alle Benutzer und alle Geräte in Bereichsgruppen zuweisen. Klicken Sie hierzu auf **Intune-Rollen** > **Alle Rollen** > **Policy and profile manage** (Richtlinien- und Profil-Manager) > **Zuweisungen** > choose an assignment (Zuweisung auswählen) **Bereich (Gruppen)**.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-Profile können bald Gruppenziele verwenden <!-- 1877935 -->
Derzeit können AutoPilot-Bereitstellungsprofile ausgewählten Geräten zugewiesen werden. Nach Veröffentlichung dieser Funktion erfolgt die Zuweisung dieser Profile wie folgt:
- Erstellen Sie (Azure AD-) Gruppen, die AutoPilot-Geräte enthalten.
- Weisen Sie die gewünschten Profile einer Azure AD-Gruppe zu. Das AutoPilot-Profil wird den AutoPilot-Geräten in dieser Gruppe zugewiesen.

### <a name="management-name-field-will-be-editable----1875989---"></a>Feld für Verwaltungsname kann bearbeitet werden <!-- 1875989 -->
Sie können das Feld für den Verwaltungsnamen auf dem Blatt **Eigenschaften** eines Geräts bearbeiten. Zum Bearbeiten dieses Felds wählen Sie **Geräte** > **Alle Geräte** > Gerät auswählen > **Eigenschaften** aus. Sie können das Feld für den Verwaltungsnamen zur eindeutigen Identifizierung eines Geräts verwenden.

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1403702 -->
Sie können zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte für Windows 10-Geräte konfigurieren. Zusätzliche Einstellungen sind zukünftig in den Bereichen Microsoft Netzwerk (Client), Microsoft-Netzwerk (Server), Netzwerkzugriff und -sicherheit und interaktive Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind zukünftig verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Geräteentfernung) aus.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 AutoPilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Um dieses Feature anzuzeigen, wechseln Sie in **Intune** zu **Geräteregistrierung** > **Windows-Registrierung** > **Windows AutoPilot-Profile** > **Neu erstellen** > **Registrierungseinstellungen**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Unterstützen von mehreren Exchange-Connectors <!-- 2070451 -->

Sie werden nicht länger auf einen Microsoft Intune Exchange-Connector pro Mandant beschränkt. Intune unterstützt mehrere Exchange-Connectors, sodass Sie Intune mithilfe von mehreren lokalen Exchange-Organisationen für bedingten Zugriff einrichten können.

Mit einem lokalen Exchange-Connector von Intune können Sie den Zugriff von Geräten auf Ihre lokalen Exchange-Postfächer verwalten. Dies ist abhängig davon, ob ein Gerät bei Intune registriert ist, und ob es den Gerätekompatibilitätsrichtlinien von Intune entspricht. Um einen Connector einzurichten, müssen Sie den lokalen Exchange-Connector von Intune aus dem Azure-Portal herunterladen und ihn auf einem Server in Ihrer Exchange-Organisation installieren. Klicken Sie im Microsoft Intune-Dashboard auf **Lokaler Zugriff** und dann unter **Setup** auf **Exchange ActiveSync-Connector**. Laden Sie den lokalen Exchange-Connector herunter, und installieren Sie ihn auf einem Server in Ihrer Exchange-Organisation. Da Sie nun nicht länger auf einen Exchange-Connector pro Mandant beschränkt werden, wenn Sie weitere Exchange-Organisationen haben, können Sie anhand des gleichen Durchgangs einen Connector für jede weitere Exchange-Organisation herunterladen und installieren.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Die Möglichkeit, erforderliche branchenspezifische Apps (LOB) für alle Benutzer von Windows 10 Desktop-Geräten bereitzustellen <!-- 1627835 RS4 -->.
Kunden können erforderliche branchenspezifische Apps unter Windows 10 bereitstellen, um in Gerätekontexte zu installieren. Dadurch können diese Apps für alle Benutzer auf dem Gerät verfügbar sein. Dies gilt nur für Windows 10 Desktop-Geräte.

### <a name="company-portal-enrollment-improved----1874230--"></a>Verbesserte Unternehmensportal-Registrierung <!-- 1874230-->
Benutzer, die mithilfe des Unternehmensportals unter Windows 10 Version 1703 oder höher ein Gerät registrieren, können den ersten Schritt der Registrierung ausführen, ohne die App verlassen zu müssen.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aktualisieren der „Hilfe und Feedback“-Oberfläche in der Unternehmensportal-App für Android <!--1631531 -->

Die „Hilfe und Feedback“-Benutzeroberfläche in der Unternehmensportal-App für Android wird zukünftig aktualisiert, um den Best Practices für Android-Apps zu entsprechen. Die Unternehmensportal-App für Android wird in den nächsten Monaten aktualisiert. Das **Hilfe und Feedback**-Menüelement wird in die Menüelemente **Hilfe** und **Feedback senden** unterteilt. Auf der **Hilfe**-Seite wird es einen **Häufig gestellte Fragen**-Abschnitt und eine **E-Mail-Support**-Schaltfläche zum Hochladen von Protokollen an Microsoft und Senden von E-Mails an die Supportabteilung Ihres Unternehmens geben, in denen die Probleme beschrieben werden. Die Option **Feedback senden** führt den Benutzer durch den Standardprozess zur Feedbackübermittlung von Microsoft, in dem der Benutzer angeben kann, ob ihm etwas gefällt, nicht gefällt und Vorschläge machen kann.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).



