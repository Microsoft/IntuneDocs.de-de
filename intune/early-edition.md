---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e91745abb7c3409b31724101b3071157407acec9
ms.sourcegitcommit: 54fc806036f84a8667cf8f74086358bccd30aa7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>Die Early Edition für Microsoft Intune – März 2018

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

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Unterstützen von mehreren Exchange-Connectors <!-- 2070451 -->

Sie werden nicht länger auf einen Microsoft Intune Exchange-Connector pro Mandant beschränkt. Intune unterstützt mehrere Exchange-Connectors, sodass Sie Intune mithilfe von mehreren lokalen Exchange-Organisationen für bedingten Zugriff einrichten können.

Mit einem lokalen Exchange-Connector von Intune können Sie den Zugriff von Geräten auf Ihre lokalen Exchange-Postfächer verwalten. Dies ist abhängig davon, ob ein Gerät bei Intune registriert ist, und ob es den Gerätekompatibilitätsrichtlinien von Intune entspricht. Um einen Connector einzurichten, müssen Sie den lokalen Exchange-Connector von Intune aus dem Azure-Portal herunterladen und ihn auf einem Server in Ihrer Exchange-Organisation installieren. Klicken Sie im Microsoft Intune-Dashboard auf **Lokaler Zugriff** und dann unter **Setup** auf **Exchange ActiveSync-Connector**. Laden Sie den lokalen Exchange-Connector herunter, und installieren Sie ihn auf einem Server in Ihrer Exchange-Organisation. Da Sie nun nicht länger auf einen Exchange-Connector pro Mandant beschränkt werden, wenn Sie weitere Exchange-Organisationen haben, können Sie anhand des gleichen Durchgangs einen Connector für jede weitere Exchange-Organisation herunterladen und installieren.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Unterstützung für den neuen Cisco AnyConnect-Client für iOS <!-- 1333708 -->

Neue VPN-Profile, die für Cisco AnyConnect für iOS erstellt wurden, funktionieren mit Cisco AnyConnect 4.0.7x oder höher. Bereits existierende iOS Cisco AnyConnect VPN-Profile werden als **Cisco Legacy AnyConnect** bezeichnet und werden auch weiterhin mit Cisco AnyConnect 4.0.5x funktionieren.

> [!NOTE]
> Diese Änderung gilt nur für iOS. Es wird weiterhin nur eine Option von Cisco AnyConnect für Android, Android for Work und macOS geben. 

#### <a name="more-information"></a>Weitere Informationen

Zur Unterstützung der neuen App müssen Sie ein neues iOS Cisco AnyConnect VPN-Profil erstellen, da die neue Cisco AnyConnect-App und die Cisco Legacy AnyConnect-App unterschiedliche Apps sind. Wenn Sie den AnyConnect-Client in Ihrer Umgebung verwalten, müssen Sie die neue Cisco AnyConnect-App ebenfalls bereitstellen. Um ein Upgrade auszuführen, müssen Sie Ihr Cisco Legacy AnyConnect VPN-Profil löschen und die Cisco Legacy AnyConnect-App entfernen. 

Die NAC-Integration (Network Access Control, Netzwerk-Zugriffssteuerung) funktioniert für das erste Release des neuen AnyConnect-Clients nicht. Zusammen mit Cisco wird versucht, eine NAC-Integration in einem zukünftigen Intune-Release bereitzustellen.

### <a name="enhanced-jailbreak-detection----846515---"></a>Verbesserte Erkennung von Jailbreaks <!-- 846515 -->

Die verbesserte Erkennung von Jailbreaks ist eine neue Kompatibilitätseinstellung, die in Intune die Auswertung von Geräten mit Jailbreaks verbessert. Durch die Einstellung checkt das Gerät häufiger mit Intune ein, wozu der Ortungsdienst des Geräts benötigt wird und was Auswirkungen auf den Batterieverbrauch hat.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Die Möglichkeit, erforderliche branchenspezifische Apps (LOB) für alle Benutzer von Windows 10 Desktop-Geräten bereitzustellen <!-- 1627835 RS4 -->.
Kunden können erforderliche branchenspezifische Apps unter Windows 10 bereitstellen, um in Gerätekontexte zu installieren. Dadurch können diese Apps für alle Benutzer auf dem Gerät verfügbar sein. Dies gilt nur für Windows 10 Desktop-Geräte. 

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Ablaufende branchenspezifische Apps für Microsoft Intune <!-- 748789 -->
Im Azure-Portal werden Sie von Intune über ablaufende branchenspezifische Apps benachrichtigt. Beim Hochladen einer neuen Version der branchenspezifischen App entfernt Intune die Ablaufbenachrichtigung aus der Liste.

### <a name="company-portal-enrollment-improved----1874230--"></a>Verbesserte Unternehmensportal-Registrierung <!-- 1874230-->
Benutzer, die mithilfe des Unternehmensportals unter Windows 10 Version 1703 oder höher ein Gerät registrieren, können den ersten Schritt der Registrierung ausführen, ohne die App verlassen zu müssen.

### <a name="new-management-name-column----1333586---"></a>Namensspalte „New Management“ <!-- 1333586 -->
Eine neu Spalte mit dem Namen **Verwaltungsname** wird dem Blatt „Geräte“ hinzugefügt. Dies ist ein automatisch generierter und nicht bearbeitbarer Name, der basierend auf der folgenden Formel vom Gerät zugewiesen wird: 
- Standardname für alle Geräte: <username>_<devicetype>_<enrollmenttimestamp>
- Für Geräte, die durch Massenhinzufügen hinzugefügt wurden: <PackageId/ProfileId>_<DeviceType>_<EnrollmentTime> 
 
Dies ist eine optionale Spalte im Blatt „Geräte“. Dies wird nicht standardmäßig verfügbar sein, und Sie können nur über die Spaltenauswahl auf sie zugreifen. Diese neue Spalte hat keine Auswirkungen auf den Gerätenamen.

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Neue Einstellungen für Benachrichtigungen des Windows Defender Security Centers über Gerätekonfigurationsprofile <!-- 1631906 -->

Den Benachrichtigungen des Windows Defender Security Centers (WDSC) über Gerätekonfigurationsprofile werden drei neue Einstellungen hinzugefügt.

Administratoren können Folgendes durchführen:

- Sie können Identitäten verbergen.
- Sie können Hardware und deren Untereinstellungen verbergen.
- Sie können Ransomware verbergen (Wiederherstellung von Onedrive for Business-Daten).

Wenn Sie diese Aspekte der WDSC-App ausblenden, können Endbenutzer diese Einstellungen nicht konfigurieren, und alle mit den ausgeblendeten Komponenten verknüpften Benachrichtigungen werden nicht generiert.

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>Ausgerichtete MAM-Richtlinien, die auf Verwaltungsstatus basieren <!-- 1665993 -->

Sie können MAM-Richtlinien, die auf dem Verwaltungsstatus des Geräts basieren, gezielt ausrichten.

- **iOS-Geräte**: Sie können nicht verwaltete Geräte (nur MAM) oder von Intune verwaltete Geräte gezielt ausrichten.
- **Android-Geräte**: Sie können nicht verwaltete Geräte, von Intune verwaltete Geräte und von Intune verwaltete Android Enterprise-Profile (früher Android for Work) gezielt ausrichten.

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>Konfigurieren von Gatekeeper zum Steuern der Downloadquelle der macOS-App <!-- 1690459-->

Sie können Gatekeeper konfigurieren, um Ihre Geräte vor Apps zu schützen, indem Sie steuern, von wo die Apps heruntergeladen werden können. Sie können die folgenden Downloadquellen konfigurieren: **Mac App Store**, **Mac App Store and identified developers** (Mac App Store und verifizierte Entwickler) und **Anywhere**. Außerdem können Sie konfigurieren, dass Benutzer eine App installieren können, indem sie STRG drücken und gleichzeitig klicken, um diese Gatekeeper-Steuerelemente außer Kraft zu setzen.

Diese Einstellungen finden Sie unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

### <a name="configure-the-mac-application-firewall----1690461---"></a>Konfigurieren der Firewall der Mac-Anwendung <!-- 1690461 -->

Sie können die Firewall der Mac-Anwendung konfigurieren. Damit können Sie Verbindungen auf einer „pro Anwendung“-Basis anstatt einer „per Port“-Basis steuern. Dies erleichtert es Ihnen, die Vorteile des Firewall-Schutzes zu nutzen und zu verhindern, dass unerwünschte Apps die Kontrolle über für zulässige Apps offenen Netzwerk-Ports übernehmen.
 
Dieses Feature kann unter **Gerätekonfiguration** -> **Profil erstellen** -> **macOS** -> **Endpoint Protection**.

Nachdem Sie die Firewall-Einstellung aktivieren, können Sie die Firewall mithilfe von zwei Strategien konfigurieren:

- Blockieren von allen eingehenden Verbindungen

   Sie können alle eingehenden Verbindungen für die Zielgeräte blockieren. Wenn Sie diese Option auswählen, werden eingehende Verbindungen für alle Apps blockiert. 

- Zulassen oder Blockieren von bestimmten Apps

   Sie können den Empfang von eingehenden Verbindungen für bestimmte Apps zulassen oder blockieren. Sie können auch den geschützten Modus aktivieren, um zu verhindern, dass der Computer auf Suchanforderungen reagiert.
 
#### <a name="more-information"></a>Weitere Informationen

- Blockieren von allen eingehenden Verbindungen

   Dadurch wird verhindert, dass alle Freigabedienste (z.B. Dateifreigabe und Bildschirmfreigabe) eingehende Verbindungen empfangen. Die folgenden Systemdienste sind noch zum Empfangen von eingehenden Verbindungen zugelassen:
   - configd - implementiert DHCP und andere Netzwerkkonfigurationsservices
   - mDNSResponder - implementiert Bonjour
   - racoon -  implementiert IPSec

   Stellen Sie sicher, dass **Eingehende Verbindungen** auf **Nicht konfiguriert** (und nicht auf **Block** (Blockieren)) festgelegt ist, um Freigabedienste zu verwenden.

- Geschützter Modus

   Aktivieren Sie diese Option, um den Computer daran zu hindern, auf Suchanforderungen zu reagieren. Der Computer antwortet weiterhin auf eingehende Anforderungen von autorisierten Apps. Unerwartete Anforderungen, wie z.B. ICMP (Ping), werden ignoriert.
 

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aktualisieren der „Hilfe und Feedback“-Oberfläche in der Unternehmensportal-App für Android <!--1631531 -->

Die „Hilfe und Feedback“-Benutzeroberfläche in der Unternehmensportal-App für Android wird aktualisiert, um Android-Apps nach bewährten Methoden auszurichten. Die Unternehmensportal-App für Android wird in den nächsten Monaten aktualisiert. Das **Hilfe und Feedback**-Menüelement wird in die Menüelemente **Hilfe** und **Feedback senden** unterteilt. Auf der **Hilfe**-Seite wird es einen **Häufig gestellte Fragen**-Abschnitt und eine **E-Mail-Support**-Schaltfläche zum Hochladen von Protokollen an Microsoft und Senden von E-Mails an die Supportabteilung Ihres Unternehmens geben, in denen die Probleme beschrieben werden. Die Option **Feedback senden** führt den Benutzer durch den Standardprozess zur Feedbackübermittlung von Microsoft, in dem der Benutzer angeben kann, ob ihm etwas gefällt, nicht gefällt und Vorschläge machen kann.

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Benutzerdefinierte Buchkategorien für eBooks im Volume Purchase Program (VPP) <!-- 1488911 -->
Sie können benutzerdefinierte eBook-Kategorien erstellen und dann VPP eBooks diesen benutzerdefinierten eBook-Kategorien zuweisen. Endbenutzer können dann die neu erstellten eBook-Kategorien und den Kategorien zugewiesene Bücher sehen.

#### <a name="company-portal-for-android-visual-updates---976944---"></a>Visuelle Updates des Unternehmensportals für Android <!--976944 -->

Die Unternehmensportal-App wird für Android aktualisiert, um den [Material Design](https://material.io/)-Richtlinien von Android zu folgen. Beim Release der App werden im Artikel [What's new in app UI](whats-new-app-ui.md) (Was gibt es Neues auf der App-Benutzeroberfläche) Abbildungen der neuen Symbole veröffentlicht. 

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Unterstützung des Edge-Browsers für mobile Geräte für die App-Schutzrichtlinien von Intune <!-- 1817882 -->

Microsoft Edge für mobile Geräte unterstützt die App-Schutzrichtlinien, die in Intune definiert sind.

### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763-eeready--"></a>Verwenden eines vollständig definierten Namens als Antragsteller für das SCEP-Zertifikat <!--2221763 eeready-->
Wenn Sie ein SCEP-Zertifikatsprofil erstellen, geben Sie den Antragstellernamen ein. Sie können den vollständigen definierten Namen als Antragstellernamen verwenden. Wählen Sie für **Antragstellername** die Option **benutzerdefiniert** aus, und geben Sie dann `CN={{OnPrem_Distinguished_Name}}` ein. Damit Sie die `{{OnPrem_Distinguished_Name}}`-Variable verwenden können, stellen Sie sicher, dass das `onpremisesdistingishedname`-Benutzerattribut mithilfe von [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) mit Azure AD synchronisiert ist. 

### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837-eeready--"></a>iOS-Geräte werden alle 15 Minuten zur Eingabe einer PIN aufgefordert <!--1550837 eeready-->
Nachdem eine Konformitäts- oder Konfigurationsrichtlinie einem iOS-Gerät hinzugefügt wurde, werden Benutzer alle 15 Minuten aufgefordert, eine PIN festzulegen. Benutzer erhalten kontinuierlich eine Aufforderung, bis sie eine PIN festgelegt haben.

### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983-eeready--"></a>Aktivieren der Kontaktfreigabe über Bluetooth: Android for Work <!--1098983 eeready-->
In der Standardeinstellung verhindert Android, dass Kontakte im Arbeitsprofil mit Bluetooth-Geräten synchronisiert werden. Das Ergebnis ist, dass Arbeitsprofilkontakte nicht auf der Anrufer-ID für Bluetooth-Geräte angezeigt werden.

Zukünftig gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Kontaktfreigabe über Bluetooth

Der Intune-Administrator kann diese Einstellungen konfigurieren, um die Freigabe zu aktivieren. Dieses Feature ist nützlich, wenn Sie ein Gerät mit einem Bluetooth-Gerät in einem Fahrzeug koppeln möchten, das die Anrufer-ID für Freisprechgeräte anzeigt. Wenn das Feature aktiviert ist, werden Arbeitsprofilkontakte angezeigt. Wenn das Feature nicht aktiviert ist, werden Arbeitsprofilkontakte nicht angezeigt.

Gilt für: Android-Arbeitsprofilgeräte unter Android OS 6.0 und höher.

### <a name="schedule-your-automatic-updates---1805514---"></a>Planen von automatischen Updates <!--1805514 -->

Mit Intune können Sie die Installation von automatischen Updates mithilfe von [Einstellungen für Windows-Updateringe](windows-update-for-business-configure.md) steuern. Sie können daraufhin sich wiederholende Updates planen, einschließlich der Woche, dem Tag und der Uhrzeit. 

### <a name="disable-checks-on-device-restart---1805490---"></a>Deaktivieren von Prüfungen bei Geräteneustart <!--1805490 -->

Mit Intune können Sie die [Verwaltung von Softwareupdates](windows-update-for-business-configure.md) steuern. Die Eigenschaft **Neustartüberprüfungen** wird standardmäßig hinzugefügt und aktiviert. Wählen Sie **Überspringen** aus, um die üblichen Überprüfungen zu überspringen, wenn Sie ein Gerät neu starten (z.B. aktive Benutzer, Akkustand usw.). 

<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Neues Diagramm zum Trend von fehlgeschlagenen Registrierungen und Tabelle mit Gründen für das Fehlschlagen <!-- 1471783 -->

Auf der Seite „Registrierungsübersicht“ können Sie den Trend von fehlgeschlagenen Registrierungen und die fünf häufigsten Gründe für das Fehlschlagen anzeigen lassen. Wenn Sie auf das Diagramm oder die Tabelle klicken, können Sie sich im Detail Informationen zu den Fehlern ansehen und erhalten Ratschläge zur Fehlerbehebung und zur Wiederherstellung.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Anpassen des Unternehmsportaldesigns mit Hexadezimalcode <!--1049561 -->

Sie können die Designfarben in den Unternehmensportal-Apps mithilfe von Hexadezimalcode anpassen. Wenn Sie Ihren Hexadezimalcode eingeben, legt Intune fest, welche Textfarbe [gemäß den WCAG 2.0-Standards](http://www.w3.org/TR/WCAG20) den stärksten Kontrast zur Hintergrundfarbe bildet. In einer Vorschau können Sie die Textfarbe und das Unternehmenslogo mit den Farben unter **Mobile Apps** > **Unternehmensportal** abgleichen. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Neue Einstellungen für Windows Defender Credential Guard in den Endpoint Protection-Einstellungen <!--1102252 --> 

Neue [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard]-Einstellungen werden unter **Gerätekonfiguration** > **Profile** > **Endpoint Protection** hinzugefügt. Die folgenden Einstellungen werden hinzugefügt: 

- Plattformsicherheitsstufe: Legen Sie fest, welche Plattformsicherheitsstufe beim nächsten Neustart aktiviert wird. Für die virtualisierungsbasierte Sicherheit ist ein sicherer Start erforderlich. Falls gewünscht kann die virtualisierungsbasierte Sicherheit auch zusammen mit der Verwendung der Schutzfunktionen des direkten Remotezugriffs (Direct Memory Access, DMA) aktiviert werden. Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf richtig konfigurierten Geräten aktiviert.
- Virtualisierungsbasierte Sicherheit: Legen Sie fest, dass beim nächsten Neustart die virtualisierungsbasierte Sicherheit aktiviert wird. 
- Windows Defender Credential Guard: Aktivieren Sie Credential Guard gemeinsam mit der virtualisierungsbasierten Sicherheit, um beim nächsten Neustart die Anmeldeinformationen besser zu schützen, wenn die Plattformsicherheitsstufe sowohl mit dem sicheren Start als auch mit der virtualisierungsbasierten Sicherheit aktiviert ist. U.a. sind folgende Optionen verfügbar: **Disabled**, **Enabled with UEFI lock**, **Enabled without lock** und **Not configured** (Deaktiviert, Mit UEFI-Sperre aktiviert, Ohne Sperre aktiviert, Nicht konfiguriert). 
  - Über die Option „Deaktiviert“ wird Credential Guard per Remoteverbindung deaktiviert, wenn das Programm zuvor über die Aktion „Ohne Sperre aktiviert“ aktiviert wurde.

  - Über die Option „Mit UEFI-Sperre aktiviert“ wird gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden kann. Wenn Sie Credential Guard deaktivieren möchten, nachdem Sie diese Einstellung verwendet haben, müssen Sie die Gruppenrichtlinie auf „Deaktiviert“ festlegen und die Sicherheitsfunktion von jedem Computer mit einem anwesenden Benutzer entfernen, um die in der UEFI gespeicherte Konfiguration zu bereinigen. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

  - Über die Option „Ohne Sperre aktiviert“ kann Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie deaktiviert werden. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

  - Mit der Option „Nicht konfiguriert“ bleibt die Richtlinieneinstellung nicht definiert. Die Richtlinieneinstellung wird von der Gruppenrichtlinie nicht in die Registrierung geschrieben und hat so keinerlei Auswirkungen auf Computer oder Benutzer. Wenn es eine aktuellen Einstellung in der Registrierung gibt, wird diese nicht verändert.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Zurücksetzen von Kennwörtern für Android O-Geräte <!-- 1238299 -->
Sie können die Passwörter für registrierte Android O-Geräte zurücksetzen. Wenn Sie eine „Passwort zurücksetzen“-Anforderung an ein Android O-Gerät senden, legt dieses ein neues Passwort zum Entsperren des Geräts oder eine verwaltete Profilabfrage für den aktuellen Benutzer fest. Ein Passwort oder eine Abfrage wird dann gesendet, wenn das Gerät über einen Profilbesitzer oder einen Gerätebesitzer verfügt. Sie treten umgehend in Kraft.

### <a name="local-device-security-option-settings----1251887---"></a>Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1251887 -->
Mithilfe der neuen Einstellungen der Sicherheitsoptionen für lokale Geräte können Sie Sicherheitseinstellungen auf Windows 10-Geräten aktivieren. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Neue Druckereinstellungen für Education-Profile <!-- 1308900 -->

Für Education-Profile sind neue Einstellungen in der Kategorie **Drucker** unter **Drucker** > **Standarddrucker** > **Neue Drucker hinzufügen** verfügbar. 

### <a name="ios-app-provisioning-configuration----1581650---"></a>Bereitstellungskonfiguration für iOS-Apps <!-- 1581650 -->
Sie können Bereitstellungskonfigurationen für iOS-Apps zuweisen, um zu vermeiden, dass Ihre Apps ablaufen, indem Sie Sicherheitsgruppen ein- bzw. ausschließen.

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Neue Einstellungen für Windows Defender Application Guard <!-- 1631890 -->

- **Enable graphics acceleration** (Grafikbeschleunigung aktivieren)

Administratoren können einen virtuellen Grafikprozessor für Windows Defender Application Guard aktivieren. Über diese Einstellung kann die CPU Grafiken auslagern, die an die vGPU rendern. Dadurch kann die Leistung verbessert werden, wenn Sie mit grafikintensiven Websites arbeiten oder ein Video im Container ansehen.

- **SaveFilestoHost**

Administratoren können aktivieren, dass Dateien von Microsoft Edge, das im Container ausgeführt wird, an das Hostdateisystem übergeben werden. Wenn Sie diese Einstellung aktivieren, können Benutzer Dateien von Microsoft Edge in den Container auf dem Hostdateisystem herunterladen.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Ein- und Ausschließen von App-Zuweisungen basierend auf Gruppen für Android Enterprise <!-- 1813081 -->
Android Enterprise (ehemals Android for Work) unterstützt bei der App-Zuweisung und nach dem Auswählen eines Zuweisungstyps die Exclude-Funktion.

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ausrichten von Konformitätsrichtlinien auf Geräte in Gerätegruppen <!--1307012 -->

Sie können Konformitätsrichtlinien gezielt auf Benutzer in Benutzergruppen ausrichten. Sie können Konformitätsrichtlinien gezielt auf Benutzer in Benutzergruppen ausrichten.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

### <a name="configure-an-ios-app-pin----1586774---"></a>Konfigurieren einer PIN für eine iOS-App <!-- 1586774 -->
Bald erhalten Sie eine PIN für angesteuerte iOS-Apps. Sie können die Anforderungen für die PIN und das Ablaufdatum in Tagen im Azure-Portal konfigurieren. Falls erforderlich wird von dem Benutzer verlangt, eine neue PIN festzulegen und zu verwenden, bevor er Zugriff auf eine iOS-App erhält. Nur iOS-Apps, die einen App-Schutz mit dem Intune App SDK aktiviert haben, unterstützen diese Funktion.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen die einmalige Anmeldung für diese (öffentliche Vorschau) <!-- 710595 -->   
Mithilfe von Azure Active Directory (Azure AD) können Sie den Zugriff auf Websites durch mobile Geräte auf die App „Intune Managed Browser“ beschränken. Im verwalteten Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Umleiten von macOS-Benutzern zur neuen Unternehmensportal-App <!--1380728-->   
Wenn ein Benutzer sich bei der Website des Unternehmensportals anmeldet, um sein macOS-Gerät zu registrieren, wird dieser zum Download der neuen Unternehmensportal-App für macOS umgeleitet, um den Vorgang abzuschließen. Dies tritt bei macOS-Geräten auf, die OS X El Capitan 10.11 oder höher verwenden. 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Verbesserte Fehlermeldungen für den Fall, wenn ein Benutzer die Höchstzahl von zur Registrierung erlaubten Geräten erreicht <!-- 1270370 -->
Statt einer generischen Fehlermeldung sehen Benutzer mit Android-Geräten eine an Benutzer gerichtete, handlungsrelevante Fehlermeldung: „You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.“ (Sie haben die maximale Anzahl an Geräten registriert, die von Ihrem IT-Administrator erlaubt wurden. Bitte entfernen Sie ein registriertes Gerät, oder wenden Sie sich an Ihren IT-Administrator.“)



## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.



### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


