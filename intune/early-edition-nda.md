---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ad49b983bd5dc72a3355cba5645192456a555e38
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321253"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Die Early Edition für Microsoft Intune: Juli 2018

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

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Weitere Synchronisierungsoptionen in der Unternehmensportal-App für Windows <!-- 2683177 -->
In der Unternehmensportal-App für Windows wird eine neue Gerätesynchronisierungsaktion zu den Sprunglisten der Windows-Taskleiste und dem Startmenü hinzugefügt. Navigieren Sie zu einer dieser Optionen, um Ihre Geräte schnell zu synchronisieren und Zugriff auf Unternehmensressourcen zu erhalten.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Zurücksetzen von Gerätekennungen über die Unternehmensportal-App für Windows 10 <!-- 2101282 --> 
Ihre Mitarbeiter können schon bald die PIN bzw. die Kennung ihres Geräts direkt über die Unternehmensportal-App für Windows 10 zurücksetzen. Diese Funktion ist dann jeweils auf remoten und lokal verwalteten Intune-Geräten verfügbar, die Zurücksetzungen der Kennung unterstützen. Je nach Gerätetyp entfernt eine Anforderung, die für ein Remotegerät gestellt wird, entweder die aktuelle Kennung des Geräts oder erstellt eine temporäre Kennung. Benutzer, die eine Zurücksetzung für ein lokales Gerät anfordern, werden an die App „Einstellungen“ des Geräts weitergeleitet.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Geänderte Durchsuchen-Funktion in der Unternehmensportal-App für Windows <!-- 2317227 -->  
Beim Durchsuchen oder Suchen nach Apps in der Unternehmensportal-App für Windows können Sie zwischen der Ansicht **Kacheln** und der neu hinzugefügten Ansicht **Details** wechseln. In der neuen Ansicht werden Details zu Anwendungen wie Namen, Herausgeber, Veröffentlichungsdatum und Installationsstatus angezeigt.  

Auf der Seite **Apps** wird die Ansicht **Installiert** hinzugefügt, über die Sie Details zu abgeschlossenen und laufenden App-Installationen anzeigen können. Möchten Sie uns Ihre Meinung oder Anregungen zu den neuesten Änderungen mitteilen? Über die Unternehmensportal-App können Sie uns Feedback senden.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Verbesserungen an den Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager <!-- 675800 -->
Wenn ein Geräteregistrierungs-Manager (DEM) sich in der Unternehmensportal-App für Windows anmeldet, listet die App nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserungen werden Timeouts vermindert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte zu laden.  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Verwendung von VPP-Gerätelizenzen, zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung <!-- 1608345 -->
Sie können Gerätelizenzen des Volume Purchase Program (VPP) verwenden, um das Unternehmensportal während der Registrierungsvorgänge des Programms zur Geräteregistrierung (Device Enrollment Program, DEP) vorab bereitzustellen. Geben Sie dazu bei der Erstellung oder Bearbeitung eines Registrierungsprofils das VPP-Token an, das Sie zum Installieren des Unternehmensportals verwenden möchten. Stellen Sie sicher, dass Ihr Token nicht abläuft, und dass Sie über genügend Lizenzen für die Unternehmensportal-App verfügen. In Fällen, in denen das Token abläuft oder über keine Lizenzen mehr verfügt, überträgt Intune stattdessen das App Store-Unternehmensportal mithilfe von Push (dafür ist die Eingabe eine Apple-ID erforderlich).


### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massenlöschung von Geräten auf dem Blatt „Geräte“ <!-- 1793693 -->
Sie können mehrere Geräte gleichzeitig über das Blatt „Geräte“ löschen. Wählen Sie **Geräte** > **Alle Geräte** aus, wählen Sie die Geräte aus, die Sie löschen möchten, und klicken Sie auf **Löschen**. Es wird eine Warnung für die Geräte ausgegeben, die nicht gelöscht werden können.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Neues WLAN-Gerätekonfigurationsprofil für Windows 10 und höher <!-- 1879077 -->
Aktuell können Sie WLAN-Profile mithilfe von XML-Dateien importieren und exportieren. Sie können ein WLAN-Gerätekonfigurationsprofil genau wie für andere Plattformen auch direkt in Intune erstellen.

Um ein Profil zu erstellen, öffnen Sie **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **Windows 10 und höher** > **WLAN**. 

Gilt für Windows 10 und höher.

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Dateierweiterung branchenspezifischer Windows-Apps (LOB-Apps) <!-- 1884873 -->
Die Dateierweiterungen für Windows-LOB-Apps umfassen jetzt *.msi*, *.appx*, *.appxbundle*, *.msix* und *.msixbundle*. Sie können eine App in Microsoft Intune hinzufügen, indem Sie **Mobile Apps** > **Apps** > **Hinzufügen** auswählen. Der Bereich **App hinzufügen** wird geöffnet. Dort können Sie den **App-Typ** auswählen. Wählen Sie für Windows-LOB-Apps **Branchenspezifische App** als App-Typ aus, wählen Sie **App-Paketdatei** aus, und geben Sie dann eine Installationsdatei mit der entsprechenden Erweiterung ein.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Das automatisch dem Konfigurationsprofil zugewiesene Windows Defender ATP-Konfigurationspaket <!-- 2144658 -->
Wenn Sie [Advanced Threat Protection verwenden und Geräte in Intune onboarden](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile), laden Sie derzeit ein Konfigurationspaket herunter und fügen es Ihrem Konfigurationsprofil hinzu. In einem zukünftigen Update ruft Intune das Paket automatisch aus dem Windows Defender Security Center ab und fügt es Ihrem Profil hinzu.

Gilt für Windows 10 und höher.


### <a name="check-for-sccm-compliance----2192052---"></a>Überprüfung auf SCCM-Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (SCCM) (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). SCCM sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle SCCM-Signale auffordern, „compliant“ (konform) zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. In SCCM hat diese Anforderung den Zustand „Installed“ (Installiert). Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und wenn die Lizenzen für das Unternehmensportal knapp werden.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Erforderliche Bestätigung zur Löschung von VPP-Token, die für die Vorabbereitstellung des Unternehmensportals verwendet werden <!-- 2237634 -->
Für die Löschung eines VPP-Tokens (Volume Purchase Program) ist eine Bestätigung notwendig, falls das Token zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwendet wird.


#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Zusätzliche Sicherheitseinstellungen für Windows Installer <!-- 2282430 -->
Sie können Benutzern erlauben, App-Installationen zu steuern. Wenn diese Option aktiviert ist, werden Installationen, die normalerweise wegen Sicherheitsverstößen unterbrochen werden würden, weiterhin ausgeführt. Sie können festlegen, dass Windows Installer bei der Installation eines beliebigen Programms auf einem System erhöhte Berechtigungen verwendet. Zusätzlich können Sie festlegen, dass Windows Information Protection-Elemente (WIP) indiziert und die zugehörigen Metadaten an einem nicht verschlüsselten Speicherort gespeichert werden. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente weder indiziert noch in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Diese Optionen sind standardmäßig deaktiviert. 


<!-- 1806 start -->


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können zukünftig auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts <!-- 1506985 -->

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Start und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird die Sicherheit von MAM-fähigen Apps (Mobile Application Management, mobile Anwendungsverwaltung) durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus-Sprachpakete <!-- 1833450 -->
Als Intune-Administrator können Sie zukünftig zusätzliche Sprachen für Office 365 Pro Plus-Apps bereitstellen, die über Intune verwaltet werden. In der Liste der verfügbaren Sprachpakete ist auch der **Typ** der Sprachpakete angegeben (grundlegende Sprachunterstützung, Sprache teilweise unterstützt und Sprachkorrekturhilfen). Klicken Sie im Azure-Portal auf **Microsoft Intune** > **Mobile Apps** > **Apps** > **Hinzufügen**. Wählen Sie auf dem Blatt **App hinzufügen** in der Liste **App-Typ** unter **Office 365 Suite** den Eintrag **Windows 10** aus. Klicken Sie auf dem Blatt **Einstellungen der App-Suite** auf **Sprachen**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Neues Update zur Verbesserung der Benutzerfreundlichkeit der Unternehmensportalwebsite <!--2000968 -->
Die Unternehmensportalwebsite bzw. der iOS-App-Katalog wird auf der Grundlage von Kundenfeedback um neue Features ergänzt. Dadurch werden auf Android-, iOS- und Windows-Geräten bereits vorhandene Funktionen verbessert, und die Benutzerfreundlichkeit erhöht sich. Bestimmte Bereiche der Website – z.B. Gerätedetails, Feedback und Support sowie die Geräteübersicht – werden mit einem neuen, modernen und dynamischen Design ausgestattet. Weiterhin sind enthalten:

- optimierte Workflows auf allen Geräteplattformen
- eine verbesserte Geräteidentifikation und optimierte Registrierungsworkflows
- aussagekräftigere Fehlermeldungen
- eine benutzerfreundlichere Sprache und weniger Fachbegriffe
- Möglichkeit, direkte Links zu Apps zu teilen
- Verbesserte Leistung bei großen App-Katalogen
- verbesserte Barrierefreiheit für alle Benutzer

Das Update ist derzeit als Vorschauversion verfügbar. Sie können sich unter http://aka.ms/webcpflighting für die Vorschauversion registrieren.


<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts <!-- 1506985 --> 

Durch die erzwungene Verwendung einer nicht biometrischen Kennung beim App-Kaltstart und bei Timeouts nach einer vom Administrator festgelegten Zeitdauer wird zukünftig die Sicherheit von MAM-fähigen Apps durch Intune erhöht, indem die Nutzung einer biometrischen Kennung für den Zugriff auf Unternehmensdaten beschränkt wird. Die Einstellungen betreffen Benutzer, die Touch ID (iOS), Face ID (iOS), Android Biometric oder andere biometrische Authentifizierungsmethoden für den Zugriff auf ihre APP-/MAM-fähigen Anwendungen verwenden. Intune-Administratoren bieten die Einstellungen mehr Kontrolle über den Benutzerzugriff. So können Szenarios vermieden werden, in denen ein Gerät, für das mehrere Fingerabdrücke oder andere biometrische Zugriffsmethoden verwendet werden, dem falschen Benutzer Zugriff auf Unternehmensdaten gestattet. Öffnen Sie im Azure-Portal **Microsoft Intune**. Klicken Sie auf **Mobile Apps** > **App-Schutzrichtlinien** > **Richtlinie hinzufügen** > **Einstellungen**. Im Abschnitt **Zugriff** können Sie die entsprechenden Einstellungen vornehmen.


<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Die Möglichkeit, erforderliche branchenspezifische Apps (LOB) für alle Benutzer von Windows 10 Desktop-Geräten bereitzustellen <!-- 1627835 RS4 -->.
Kunden können erforderliche branchenspezifische Apps unter Windows 10 bereitstellen, um in Gerätekontexte zu installieren. Dadurch können diese Apps für alle Benutzer auf dem Gerät verfügbar sein. Dies gilt nur für Windows 10 Desktop-Geräte.

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
