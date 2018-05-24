---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 62028232e4d6c9ab20a05480811978234ed0a3c1
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>Die Early Edition für Microsoft Intune – Mai 2018

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
Sie werden bald in der Lage sein, App-Schutzrichtlinien so zu konfigurieren, das nicht kompatible Geräte explizit zurückgesetzt, blockiert oder gewarnt werden. Mit der neuesten Aktion *Zurücksetzen* werden Ihre Unternehmensdaten von einem Gerät entfernt. Im Falle eines Zurücksetzens wird der Gerätebenutzer über den Grund für das Zurücksetzen und Schritte zur Wiederherstellung benachrichtigt. Für einige Einstellungen, wie z. B. die Mindestversion des Betriebssystems, können Sie mehrere Aktionen anwenden, z. B. das Blockieren und Zurücksetzen.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Neue Inventurinformationen für Windows-Geräte <!-- 1333569 eeready -->

Für Windows-Geräte stehen die folgenden Inventurinformationen pro Gerät auf der Registerkarte **Hardware** bereit (**Gruppen** > **Alle mobilen Geräte** > **Geräte** > Gerät des Benutzers auswählen > **Eigenschaften anzeigen** > **Hardware**):
- TPM
- Antivirensoftware
- Antispyware
- Firewall
- UAC
- Akku
- Domänenname

Weitere Informationen dazu, wie diese Daten vom Konfigurationsdienstanbieter abgerufen werden, finden Sie unter den DeviceGuard-Einträgen im Artikel zum [Konfigurationsdienstanbieter für DeviceStatus](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp).

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
Sie können alle Benutzer, alle Geräte sowie alle Benutzer und alle Geräte in Bereichsgruppen zuweisen.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-Profile können bald Gruppenziele verwenden <!-- 1877935 -->
Derzeit können AutoPilot-Bereitstellungsprofile ausgewählten Geräten zugewiesen werden. Nach Veröffentlichung dieser Funktion erfolgt die Zuweisung dieser Profile wie folgt:
- Erstellen Sie (Azure AD-) Gruppen, die AutoPilot-Geräte enthalten.
- Weisen Sie die gewünschten Profile einer Azure AD-Gruppe zu. Das AutoPilot-Profil wird den AutoPilot-Geräten in dieser Gruppe zugewiesen.

### <a name="management-name-field-will-be-editable----1875989---"></a>Feld für Verwaltungsname kann bearbeitet werden <!-- 1875989 -->
Sie können das Feld für den Verwaltungsnamen auf dem Blatt **Eigenschaften** eines Geräts bearbeiten. Zum Bearbeiten dieses Felds wählen Sie **Geräte** > **Alle Geräte** > Gerät auswählen > **Eigenschaften** aus. Sie können das Feld für den Verwaltungsnamen zur eindeutigen Identifizierung eines Geräts verwenden.

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Ergänzungen zu den Einstellungen der Sicherheitsoptionen für lokale Geräte <!-- 1403702 -->
Sie können zusätzliche Einstellungen für Sicherheitsoptionen für lokale Geräte für Windows 10-Geräte konfigurieren. Zusätzliche Einstellungen sind zukünftig in den Bereichen Microsoft Netzwerk (Client), Microsoft-Netzwerk (Server), Netzwerkzugriff und -sicherheit und interaktive Anmeldung verfügbar. Diese Einstellungen finden Sie in der Endpoint Protection-Kategorie, wenn Sie eine Gerätekonfigurationsrichtlinie für Windows 10 erstellen.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Erforderliche Installation von Richtlinien, Apps, Zertifikaten und Netzwerkprofilen <!-- 1553555 -->
Administratoren können Endbenutzern den Zugriff auf Windows 10 RS4 Desktop verwehren, bis Richtlinien, Apps, Zertifikate und Netzwerkprofile während der Bereitstellung von AutoPilot-Geräten von Intune installiert wurden.

### <a name="rules-for-removing-devices----1609459---"></a>Regeln für das Entfernen von Geräten <!-- 1609459 -->
Neue Regeln, mit denen Sie Geräte automatisch entfernen können, die über einen festgelegten Zeitraum nicht mehr eingecheckt waren, sind zukünftig verfügbar. Um die neue Regel anzuzeigen, wechseln Sie in den Bereich **Intune**, und wählen Sie **Geräte** und anschließend **Device removal rules** (Regeln zur Geräteentfernung) aus.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Verhindern von Verbraucher-Apps und -Umgebungen auf dem Windows 10 Enterprise RS4 AutoPilot-Gerät<!-- 1621980 -->
Sie können die Installation von Verbraucher-Apps und -Umgebungen auf Ihren Windows 10 Enterprise RS4 AutoPilot-Geräten verhindern. Um dieses Feature anzuzeigen, wechseln Sie in **Intune** zu **Geräteregistrierung** > **Windows-Registrierung** > **Windows AutoPilot-Profile** > **Neu erstellen** > **Registrierungseinstellungen**. 

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

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>App-Schutzrichtlinien <!-- 679615 -->
Mit den Intune-App-Schutzrichtlinien können Sie globale Standardrichtlinien erstellen und damit den Schutz für alle Benutzer im gesamten Mandanten schnell aktivieren.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Benachrichtigungen

Derzeit gibt es keine aktiven Benachrichtigungen.

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).
