---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b003fde011fd3a727c7c7a163fedb1dae6779425
ms.sourcegitcommit: 407191a92ef356a3d196b6f9959b9b033190ca2c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Die Early Edition für Microsoft Intune (April 2018)

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

<!-- 1804 start -->

### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Anzeigen der Anrufer-ID im persönlichen Profil – Android for Work <!--1098984 -->
Wenn Sie ein persönliches Profil auf einem Gerät verwenden, sehen Endbenutzer möglicherweise keine Anrufer-ID-Details von einem Arbeitskontakt. 

Seit diesem Update gibt es eine neue Einstellung unter **Android for Work** > **Geräteeinschränkungen** > **Arbeitsprofileinstellungen**:
- Anrufer-ID des Arbeitskontakts im persönlichen Profil anzeigen

Wenn aktiviert (nicht konfiguriert), werden die Anruferdetails des Arbeitskontakts im persönlichen Profil angezeigt. Wenn blockiert, wird die Anrufernummer des Arbeitskontakts im persönlichen Profil nicht angezeigt. 

Gilt für: Android-Arbeitsprofilgeräte unter Android OS 6.0 und höher.

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>Neue Einstellungen für Windows Defender Credential Guard in den Endpoint Protection-Einstellungen <!--1102252 --><!--from 1802-->

Neue [Windows Defender Central Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)-Einstellungen werden unter **Gerätekonfiguration** > **Profile** > **Endpoint Protection** hinzugefügt. Die folgenden Einstellungen werden hinzugefügt:

- Plattformsicherheitsstufe: Legen Sie fest, welche Plattformsicherheitsstufe beim nächsten Neustart aktiviert wird. Für die virtualisierungsbasierte Sicherheit ist ein sicherer Start erforderlich. Falls gewünscht kann die virtualisierungsbasierte Sicherheit auch zusammen mit der Verwendung der Schutzfunktionen des direkten Remotezugriffs (Direct Memory Access, DMA) aktiviert werden. Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf richtig konfigurierten Geräten aktiviert.
- Virtualisierungsbasierte Sicherheit: Legen Sie fest, dass beim nächsten Neustart die virtualisierungsbasierte Sicherheit aktiviert wird.
- Windows Defender Credential Guard: Aktivieren Sie Credential Guard gemeinsam mit der virtualisierungsbasierten Sicherheit, um beim nächsten Neustart die Anmeldeinformationen besser zu schützen, wenn die Plattformsicherheitsstufe sowohl mit dem sicheren Start als auch mit der virtualisierungsbasierten Sicherheit aktiviert ist. U.a. sind folgende Optionen verfügbar: **Disabled**, **Enabled with UEFI lock**, **Enabled without lock** und **Not configured** (Deaktiviert, Mit UEFI-Sperre aktiviert, Ohne Sperre aktiviert, Nicht konfiguriert).
  - Über die Option „Deaktiviert“ wird Credential Guard per Remoteverbindung deaktiviert, wenn das Programm zuvor über die Aktion „Ohne Sperre aktiviert“ aktiviert wurde.

  - Über die Option „Mit UEFI-Sperre aktiviert“ wird gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden kann. Wenn Sie Credential Guard deaktivieren möchten, nachdem Sie diese Einstellung verwendet haben, müssen Sie die Gruppenrichtlinie auf „Deaktiviert“ festlegen und die Sicherheitsfunktion von jedem Computer mit einem anwesenden Benutzer entfernen, um die in der UEFI gespeicherte Konfiguration zu bereinigen. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

  - Über die Option „Ohne Sperre aktiviert“ kann Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie deaktiviert werden. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

  - Mit der Option „Nicht konfiguriert“ bleibt die Richtlinieneinstellung nicht definiert. Die Richtlinieneinstellung wird von der Gruppenrichtlinie nicht in die Registrierung geschrieben und hat so keinerlei Auswirkungen auf Computer oder Benutzer. Wenn es eine aktuellen Einstellung in der Registrierung gibt, wird diese nicht verändert.

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Kennungsunterstützung für die MAM-PIN unter Android<!-- 1438086 -->

Intune-Administratoren können zukünftig eine Anforderung für den Anwendungsstart festlegen, um eine Kennung anstatt einer numerischen MAM-PIN zu erzwingen. Wenn dies konfiguriert ist, muss der Benutzer eine Kennung festlegen und verwenden, wenn er dazu aufgefordert wird, bevor der Zugriff auf MAM-aktivierte Apps gewährt wird. Eine Kennung ist als numerische PIN mit mindestens einem Sonderzeichen oder einem Groß-/Kleinbuchstaben definiert. Intune unterstützt Kennungen auf ähnliche Weise wie die vorhandene numerische PIN. Es kann eine Mindestlänge über die Administratorkonsole festgelegt werden, sodass wiederholte Zeichen und Sequenzen möglich sind. Für dieses Feature ist die neueste Unternehmensportalversion unter Android erforderlich. Dieses Feature ist bereits für iOS verfügbar.

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blockieren von Kamera und Bildschirmaufnahmen unter Android for Work <!-- 1098977 eeready-->
Es werden zwei neue Eigenschaften zum Blockieren beim Konfigurieren der Geräteeinschränkungen für Android-Geräte hinzugefügt: 
- Kamera: Der Zugriff auf alle Kameras auf dem Gerät wird blockiert.
- Bildschirmaufnahme: Die Bildschirmaufnahme wird blockiert,. Zudem wird verhindert, dass der Inhalt auf Anzeigegeräten angezeigt wird, die über keine sichere Videoausgabe verfügen.

Gilt für Android for Work.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Unterstützung von branchenspezifischen Apps für macOS <!-- 1473977 -->
Microsoft Intune stellt eine Funktion zur Installation von macOS-LOB-Apps aus dem Azure-Portal bereit. Sie können eine macOS-LOB-App zu Intune hinzufügen, nachdem sie von dem in GitHub verfügbaren Tool vorab verarbeitet wurde. Wählen Sie im Azure-Portal auf dem Blatt **Intune** die Option **Mobile Apps** aus. Wählen Sie auf dem Blatt **Mobile Apps** die Option **Apps** > **Hinzufügen** aus. Wählen Sie auf dem Blatt **App hinzufügen** die Option **Branchen-App** aus. 

### <a name="support-for-user-less-devices----1637553---"></a>Unterstützung für Geräte ohne Benutzer <!-- 1637553 -->
Intune unterstützt die Möglichkeit, Konformität auf einem benutzerlosen Gerät zu bewerten, z.B. einem Microsoft Surface Hub-Gerät. Die Konformitätsrichtlinie kann sich auf bestimmte Geräte beziehen. Die Konformität (und auch Nichtkonformität) kann für Geräte festgelegt werden, die über keinen zugewiesenen Benutzer verfügen.

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1403702 -->
Sie können zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte für Windows 10-Geräte konfigurieren. Zusätzliche Einstellungen sind zukünftig in den Bereichen Microsoft Netzwerk (Client), Microsoft-Netzwerk (Server), Netzwerkzugriff und -sicherheit und interaktive Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Erforderliche Installation von Richtlinien, Apps, Zertifikaten und Netzwerkprofilen <!-- 1553555 -->
Administratoren können Endbenutzern den Zugriff auf Windows 10 RS4 Desktop verwehren, bis Richtlinien, Apps, Zertifikate und Netzwerkprofile während der Bereitstellung von AutoPilot-Geräten von Intune installiert wurden.

### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind zukünftig verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Geräteentfernung) aus.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 AutoPilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Um dieses Feature anzuzeigen, wechseln Sie in **Intune** zu **Geräteregistrierung** > **Windows-Registrierung** > **Windows AutoPilot-Profile** > **Neu erstellen** > **Registrierungseinstellungen**. 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>Advanced Threat Protection, in Intune integriert <!-- 1629303 -->
[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) zeigt die Risikostufe von Windows 10-Geräten an. Wenn Intune Windows 10-Gerät auf Konformität überprüft, wird die ATP-Risikobewertung in diese Auswertung mit einbezogen. Sie können ATP mit dem bedingten Zugriff verwenden, um Ihr Netzwerk zu schützen.

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Neue Schritte für die Registrierung für Benutzer auf Geräten mit macOS High Sierra 10.13.2 und höher <!--1734567 -->
Mit macOS high Sierra 10.13.2 wurde das Konzept der „vom Benutzer genehmigten“ MDM-Registrierung eingeführt. Zukünftig kann Intune mithilfe genehmigter Registrierungen einige sicherheitsrelevante Einstellungen verwalten. Weitere Informationen finden Sie in der Dokumentation zur Apple-Unterstützung: https://support.apple.com/HT208019.

Geräte, die mithilfe des macOS-Unternehmensportals registriert wurden, werden so lange als „nicht vom Benutzer genehmigt“ angesehen, bis der Endbenutzer sie in den Systemeinstellungen manuell genehmigt. Dafür werden Benutzer im macOS-Unternehmensportal unter macOS 10.13.2 und höher nun direkt aufgefordert, ihre Registrierung am Ende des Registrierungsprozesses manuell zu genehmigen. Die Intune-Administratorkonsole meldet, ob ein registriertes Gerät vom Benutzer genehmigt wurde.

### <a name="delete-autopilot-devices----1713650---"></a>Löschen von AutoPilot-Geräten <!-- 1713650 -->
Intune-Administratoren können AutoPilot-Geräte löschen.

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Integrierte App-Zuweisung in Android for Work (AFW) für die Gruppen „Alle Benutzer“ und „Alle Geräte“ <!-- 1813073 -->
Sie können die integrierten Gruppen **Alle Benutzer** und **Alle Geräte** für die AFW-App-Zuweisung nutzen. Weitere Informationen finden Sie unter [Einschließen und Ausschließen von App-Zuweisungen in Microsoft Intune](apps-inc-exl-assignments.md).

### <a name="improved-device-deletion-experience---1832333---"></a>Verbesserte Erfahrung bei der Gerätelöschung <!--1832333 -->
Sie müssen nicht länger Unternehmensdaten entfernen oder das Gerät auf Werkseinstellungen zurücksetzen, bevor sie es aus Intune löschen.

Melden Sie sich für die neue Benutzererfahrung in Intune an, und wählen Sie **Geräte** > **Alle Geräte** > Name des Geräts > **Löschen** aus.

 Wenn Sie die Bestätigung zum Zurücksetzen bzw. der Deaktivierung beibehalten möchten, können Sie die Standardvorgehensweise für den Gerätelebenszyklus verwenden, indem Sie vor der Option **Löschen** die Optionen **Entfernen von Unternehmensdaten** und **Auf Werkseinstellungen zurücksetzen** ausgeben. 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-Profile können bald Gruppenziele verwenden <!-- 1877935 -->
Derzeit können AutoPilot-Bereitstellungsprofile ausgewählten Geräten zugewiesen werden. Ab Ende April gibt es eine neue Vorgehensweise zum Zuweisen dieser Profile:
- Erstellen Sie (Azure AD-) Gruppen, die AutoPilot-Geräte enthalten.
- Weisen Sie die gewünschten Profile einer Azure AD-Gruppe zu. Das AutoPilot-Profil wird den AutoPilot-Geräten in dieser Gruppe zugewiesen.

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>Wiedergeben von Sound im Modus für verlorene Geräte <!-- 1629303 -->
Wenn sich überwachte iOS-Geräte im [Modus für verlorene Geräte](device-lost-mode.md) in MDM (Mobile Device Management, Verwaltung mobiler Geräte) befinden, können Sie einen Sound wiedergeben (**Geräte** > **Alle Geräte** > iOS-Gerät auswählen > **Übersicht** > **More**  (Mehr)). Der Sound wird so lange wiedergegeben, bis der Modus für verlorene Geräte beendet wird, oder bis der Benutzer den Sound auf dem Gerät deaktiviert. Gilt für Geräte unter iOS 9.3 und höher.

### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune installiert benötigte Apps, die von Benutzern deinstalliert werden. <!-- 1947010 -->
Wenn ein Endbenutzer eine benötigte App deinstalliert, wird Intune die App automatisch innerhalb von 24 Stunden neu installieren, anstatt auf den 7-tägigen Auswertungszyklus zu warten.

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Verwenden eines benutzerdefinierten Antragstellernames auf dem SCEP-Zertifikat <!-- 2064190 -->
Sie können den allgemeinen Namen **OnPremisesSamAccountName** für einen benutzerdefinierten Antragsteller auf einem SCEP-Zertifikatprofil verwenden. Sie können z. B. `CN={OnPremisesSamAccountName})` verwenden.

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Senden von Diagnoseberichten in der Unternehmensportal-App für macOS <!-- 2216677 -->
Die Unternehmensportal-App für macOS-Geräte wird aktualisiert, um die Kundenerfahrung beim Melden von auf Intune bezogene Fehler zu verbessern. Ihre Mitarbeiter können über die Unternehmensportal-App folgende Aktionen ausführen:
- Diagnoseberichte direkt für das Microsoft-Entwicklerteam hochladen
- Die ID eines Vorfalls per E-Mail an das IT-Supportteams Ihres Unternehmens senden

### <a name="always-on-vpn-for-windows-10---1333666---"></a>Always On-VPN für Windows 10 <!--1333666 -->

Derzeit kann [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) auf Windows 10-Geräten mit einem benutzerdefinierten VPN (virtuelles privates Netzwerk), das über den OMA-URI erstellt wurde, verwendet werden.

Mit diesem Update können Administratoren Always On für VPN-Profile auf Windows 10 direkt in Intune im Azure-Portal aktivieren. Always On-VPN-Profile stellen automatisch eine Verbindung her, wenn Folgendes passiert:

- Benutzer melden sich an ihren Geräten an.
- Das Netzwerk auf dem Gerät ändert sich.
- Der Bildschirm wird auf dem Gerät wieder eingeschaltet, nachdem er ausgeschaltet war.

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Verbesserte Fehlermeldungen bei Uploadfehlern für MDM-Pushzertifikate <!-- 2172331 -->

In der Fehlermeldung wird erklärt, dass dieselbe Apple-ID beim Erneuern eines vorhandenen MDM-Zertifikats verwendet werden muss.

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Geräteprofildiagramm und Statusliste zeigen alle Geräte in einer Gruppe <!-- 1449153 eeready -->
Wenn Sie ein Geräteprofil konfigurieren (**Gerätekonfiguration** > **Profile**), wählen Sie das Geräteprofil aus, z.B. iOS. Sie weisen dieses Profil einer Gruppe zu, die iOS-Geräte und Nicht-iOS-Geräte enthält. Im Grafikdiagramm ist zu sehen, dass das Profil dem iOS-Gerät *und* dem Nicht-iOS-Gerät zugewiesen wird (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**). Wenn Sie das Grafikdiagramm auf der Registerkarte **Übersicht** auswählen, werden unter **Gerätestatus** alle Geräte der Gruppe aufgeführt, nicht nur iOS-Geräte. 

Nach diesem Update wird auf dem Grafikdiagramm (**Gerätekonfiguration** > **Profile** > vorhandenes Profil auswählen > **Übersicht**) nur die Anzahl für das spezifische Geräteprofil angezeigt. Wenn z.B. das Gerätekonfigurationsprofil für iOS-Geräte gilt, wird im Diagramm nur die Anzahl der iOS-Geräte aufgelistet. Wenn Sie das Grafikdiagramm auswählen und **Gerätestatus** öffnen, werden nur iOS-Geräte aufgelistet.

Während dieses Updates wird das Benutzerdiagramm vorübergehend entfernt. 


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

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Die Möglichkeit, erforderliche branchenspezifische Apps (LOB) für alle Benutzer von Windows 10 Desktop-Geräten bereitzustellen <!-- 1627835 RS4 -->.
Kunden können erforderliche branchenspezifische Apps unter Windows 10 bereitstellen, um in Gerätekontexte zu installieren. Dadurch können diese Apps für alle Benutzer auf dem Gerät verfügbar sein. Dies gilt nur für Windows 10 Desktop-Geräte.

### <a name="company-portal-enrollment-improved----1874230--"></a>Verbesserte Unternehmensportal-Registrierung <!-- 1874230-->
Benutzer, die mithilfe des Unternehmensportals unter Windows 10 Version 1703 oder höher ein Gerät registrieren, können den ersten Schritt der Registrierung ausführen, ohne die App verlassen zu müssen.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aktualisieren der „Hilfe und Feedback“-Oberfläche in der Unternehmensportal-App für Android <!--1631531 -->

Die „Hilfe und Feedback“-Benutzeroberfläche in der Unternehmensportal-App für Android wird aktualisiert, um Android-Apps nach bewährten Methoden auszurichten. Die Unternehmensportal-App für Android wird in den nächsten Monaten aktualisiert. Das **Hilfe und Feedback**-Menüelement wird in die Menüelemente **Hilfe** und **Feedback senden** unterteilt. Auf der **Hilfe**-Seite wird es einen **Häufig gestellte Fragen**-Abschnitt und eine **E-Mail-Support**-Schaltfläche zum Hochladen von Protokollen an Microsoft und Senden von E-Mails an die Supportabteilung Ihres Unternehmens geben, in denen die Probleme beschrieben werden. Die Option **Feedback senden** führt den Benutzer durch den Standardprozess zur Feedbackübermittlung von Microsoft, in dem der Benutzer angeben kann, ob ihm etwas gefällt, nicht gefällt und Vorschläge machen kann.

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Neue Druckereinstellungen für Education-Profile <!-- 1308900 -->

Für Education-Profile sind neue Einstellungen in der Kategorie **Drucker** unter **Drucker** > **Standarddrucker** > **Neue Drucker hinzufügen** verfügbar.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-Websites können die App „Intune Managed Browser“ erfordern und unterstützen die einmalige Anmeldung für diese (öffentliche Vorschau) <!-- 710595 -->   
Mithilfe von Azure Active Directory (Azure AD) können Sie den Zugriff auf Websites durch mobile Geräte auf die App „Intune Managed Browser“ beschränken. Im verwalteten Browser bleiben die Websitedaten sicher und getrennt von den persönlichen Daten des Benutzers. Zusätzlich unterstützt der Managed Browser die Funktionen für einmaliges Anmelden für Websites, die von Azure AD geschützt werden. Das Anmelden beim Managed Browser oder das Verwenden desselben auf einem Gerät mit einer anderen App, die von Intune verwaltet wird, ermöglicht es dem Managed Browser, auf Unternehmenswebsites zuzugreifen, die von Azure AD geschützt werden, ohne dass der Benutzer seine Anmeldeinformationen eingeben muss. Diese Funktion gilt für Websites wie Outlook Web Access (OWA) und SharePoint Online sowie für andere Unternehmenswebsites wie Intranetressourcen, auf die über den Azure-App-Proxy zugegriffen wird.




## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.


### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).


