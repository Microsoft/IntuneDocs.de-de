---
title: Early Edition
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 72585982cd27962981f581a99f0ea361642df0ee
ms.sourcegitcommit: ba0699cc351954960b222223c60c4ecd50edc829
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49652137"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Die Early Edition für Microsoft Intune – Oktober 2018

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Verwenden der von Microsoft empfohlenen Einstellungen mit Sicherheitsbaselines <!-- 2055484 -->
Intune lässt sich mit anderen Diensten integrieren, die sich auf Sicherheit konzentrieren, einschließlich Windows Defender ATP und Office 365 ATP. Die Kunden fordern eine gemeinsame Strategie und einen einheitlichen Satz von End-to-End-Sicherheitsworkflows für die Microsoft 365-Dienste. Unser Ziel ist es, Strategien aufeinander abzustimmen, um Lösungen zu entwickeln, die Sicherheitsvorgänge und allgemeine Administratoraufgaben miteinander verbinden. In Intune beabsichtigen wir, dieses Ziel zu erreichen, indem wir eine Reihe der von Microsoft empfohlenen „Sicherheitsbaselines“ (**Intune** > **Sicherheitsbaselines**) veröffentlichen.  Ein Administrator kann Sicherheitsrichtlinien direkt aus diesen Baselines erstellen und diese dann für seine Benutzer bereitstellen. Sie können auch die Empfehlungen für bewährte Methoden anpassen, um die Anforderungen ihres Unternehmens zu erfüllen. Intune stellt sicher, dass die Geräte den Anforderungen dieser Baselines entsprechen, und benachrichtigt die Administratoren von Benutzern oder Geräten, die nicht den Anforderungen entsprechen.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>Autopilot-Unterstützung für zu Azure Active Directory Hybrid beigetretene Geräte <!-- 1048100 -->
Sie können zu Azure Active Directory Hybrid beigetretene Geräte mithilfe von Autopilot einrichten. Geräte müssen mit dem Netzwerk Ihres Unternehmens verbunden sein, um das Hybrid-Autopilot-Feature nutzen zu können.

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

### <a name="enrollment-abandonment-report----1382924---"></a>Bericht zum Registrierungsabbruch <!-- 1382924 -->
Ein neuer Bericht, der Details zu abgebrochenen Registrierungen enthält, wird unter **Geräteregistrierung** > **Überwachen** verfügbar sein.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Bereitgestellte WIP-Richtlinien ohne Benutzerregistrierung <!-- 1434452 -->
WIP-Richtlinien (Windows Information Protection) können bereitgestellt werden, ohne dass MDM-Benutzer ihr Windows 10-Gerät registrieren müssen. Diese Konfiguration ermöglicht es Unternehmen, ihre Unternehmensdokumente auf der Grundlage der WIP-Konfiguration zu schützen, während der Benutzer die Verwaltung seiner eigenen Windows-Geräte beibehalten kann. Sobald Dokumente durch eine WIP-Richtlinie geschützt sind, können die geschützten Daten von einem Intune-Administrator selektiv zurückgesetzt werden. Durch die Auswahl von Benutzer und Gerät und das Senden einer Anforderung zum Zurücksetzen werden alle Daten, die durch die WIP-Richtlinie geschützt waren, unbrauchbar. Wählen Sie über Intune im Azure-Portal die Option **Mobile App** > **Selektive App-Zurücksetzung** aus.


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Hinzufügen eines benutzerdefinierten Markenbildes für die Unternehmensportal-App <!-- 1916266 -->
Als Microsoft Intune-Administrator können Sie ein benutzerdefiniertes Markenbild hochladen, das als Hintergrundbild auf der Profilseite des Benutzers in der Unternehmensportal-App angezeigt wird. Weitere Informationen zum Konfigurieren der Unternehmensportal-App finden Sie unter [Konfigurieren der Microsoft Intune-Unternehmensportal-App](company-portal-app.md).

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Gruppieren von mit Windows Autopilot registrierten Geräten nach Korrelator-ID <!-- 2075110 -->
Intune unterstützt die Gruppierung von Windows-Geräten nach einer Korrelator-ID, wenn sie mit [Autopilot für bestehende Geräte](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) über den Configuration Manager registriert werden. Die Korrelator-ID ist ein Parameter der Autopilot-Konfigurationsdatei. Intune legt das [Azure AD-Geräteattribut enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) automatisch auf „OfflineAutopilotprofile-\<Korrelator-ID\>“ fest. Dadurch können beliebige dynamische Azure AD-Gruppen basierend auf der Korrelator-ID über das Attribut „enrollmentprofileName“ für Offlineregistrierungen von Autopilot erstellt werden. 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Unterstützung für iOS 12 OAuth in iOS-E-Mail-Profilen <!--2155106 -->
Die iOS-E-Mail-Profile von Intune unterstützen iOS 12 OAuth. Um dieses Feature anzuzeigen, wählen Sie **Intune** > **Gerätekonfiguration** > **Profile** > **Profil erstellen** > **OAuth** aus. Wenn diese Einstellung aktiviert ist, ergeben sich die folgenden beiden Schritte:
1. Geräte, die bereits ein Zielgerät darstellen, erhalten ein neues Profil.
2. Endbenutzer werden erneut zur Eingabe ihrer Anmeldeinformationen aufgefordert.

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Neue Standardeinstellung „Erforderlicher Kennworttyp“ für Android, Android Enterprise<!-- 2649963 -->
Wenn Sie eine neue Konformitätsrichtlinie erstellen (**Intune** > **Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Android** oder **Android Enterprise** für Plattform > Systemsicherheit), ändert sich der Standardwert für **Erforderlicher Kennworttyp**: Aktuelle Standardeinstellung: Gerätestandard Neuer Standard: Mindestens numerisch Gilt für: Android, Android Enterprise

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Zuweisen von Autopilot-Profilen zur virtuellen Gruppe „Alle Geräte“ <!--2715522 -->
Sie können Autopilot-Profile zur virtuellen Gruppe „Alle Geräte“ zuweisen. Wählen Sie dazu **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** aus. Wählen Sie dann ein Profil > **Zuweisungen** > und unter **Zuweisen zu** wählen Sie **Alle Geräte** aus.

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Neues Feature zu Azure Active Directory-Nutzungsbedingungen <!-- 2870393 -->
Azure Active Directory verfügt über ein Feature für Nutzungsbedingungen, das Sie anstelle der bestehenden Intune-Nutzungsbedingungen verwenden können. Die Azure AD Nutzungsbedingungen bieten mehr Flexibilität bei der Anzeige von Bedingungen (Umfang und Zeitpunkt), eine bessere Lokalisierungsunterstützung, mehr Kontrolle über die Darstellung von Nutzungsbedingungen und eine verbesserte Berichterstellung. Die Azure AD-Nutzungsbedingungen erfordern Azure Active Directory Premium P1, das ebenfalls Teil der Enterprise Mobility + Security E3 Suite ist.


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune behält die lokalisierte Sprache für Office bei, wenn Office auf den Computern der Endbenutzer aktualisiert wird <!-- 2971030 -->
Wenn Intune Office auf den Computern Ihrer Endbenutzer installiert, erhalten sie automatisch dieselben Sprachpakete wie bei früheren MSI-Office-Installationen. 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Intune-APP-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten <!-- 2244713 -->
Sie werden die Steuerung der Intune-APP-Datenübertragungseinstellungen auf iOS-MDM-registrierten Geräten von der Angabe der Identität des registrierten Benutzers trennen können. Administratoren, die IntuneMAMUPN nicht verwenden, werden keine Verhaltensänderung feststellen. Wenn diese Funktion verfügbar ist, sollten Administratoren, die mit IntuneMAMUPN das Datenübertragungsverhalten auf registrierten Geräten steuern, die neuen Einstellungen überprüfen und ihre APP-Einstellungen nach Bedarf aktualisieren.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Verwenden eines vorinstallierten Schlüssels in einem Windows 10-WLAN-Profil <!-- 2662938 -->
Sie werden einen vorinstallierten Schlüssel (Pre-Shared Key, PSK) mit dem WPA/WPA2-Personal-Sicherheitsprotokoll verwenden können, um ein WLAN-Konfigurationsprofil für Windows 10 zu authentifizieren.
Derzeit müssen Sie ein WLAN-Profil importieren oder ein benutzerdefiniertes Profil erstellen, um einen vorinstallierten Schlüssel zu verwenden. [WLAN-Einstellungen für Geräte mit Windows 10 und höher in Intune](wi-fi-settings-windows.md) werden die aktuellen Einstellungen aufgeführt. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>App-Schutzrichtlinieneinstellungen (APP) für Webdaten <!-- 2662995 -->
App-Richtlinieneinstellungen für Webinhalte auf Android- und iOS-Geräten werden aktualisiert, um sowohl HTTP- und HTTPS-Weblinks als auch Datenübertragungen über universelle iOS-Links und Android-App-Links besser zu verarbeiten.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Erhöhen der Synchronisierungshäufigkeit von Autopilot-Geräten auf alle 12 Stunden <!-- 2753673 -->
Autopilot-Geräte werden alle 12 Stunden statt alle 24 Stunden synchronisiert.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Updates der Intune-Angebotsseite und Umbenennen von Knoten <!--2867309 -->
Updates der Intune-Angebotsseite enthalten neue und geänderte Überwachungskacheln und Diagramme für eine bessere Visualisierung von Daten. Der Knoten **Mobile Apps** ändert sich in **Client-Apps**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Höherer Endbenutzerzugriff über die Unternehmensportal-App <!-- 772203 -->
Endbenutzer werden mit der Unternehmensportal-App auf wichtige Kontoaktionen wie das Zurücksetzen des Kennworts und ihres AAD-Profils zugreifen können.  

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

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Verbesserungen an den Funktionen der Unternehmensportal-App für Geräteregistrierungs-Manager <!-- 675800 -->
Wenn ein Geräteregistrierungs-Manager (DEM) sich in der Unternehmensportal-App für Windows anmeldet, listet die App nur das aktuell ausgeführte Gerät des DEM auf. Durch diese Verbesserungen werden Timeouts vermindert, die in der Vergangenheit aufgetreten sind, wenn die App versucht hat, alle durch den DEM registrierten Geräte zu laden.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Überprüfen des Configuration Manager auf Konformität <!-- 2192052 -->
Ein zukünftiges Update enthält eine neue Einstellung für die System Center Configuration Manager-Konformität (**Gerätekonformität** > **Richtlinien** > **Richtlinie erstellen** > **Windows 10**). Der Configuration Manager sendet Signale an die Intune-Konformität. Über die Intune-Einstellung können Sie alle Configuration Manager-Signale auffordern, „konform“ zurückzugeben.

Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

Gilt für: Windows 10 und höher

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Warnungen für ablaufende VPP-Token oder Ausreizung der Unternehmensportal-Lizenz <!-- 2237572 -->
Wenn Sie das Volume Purchase Programm (VPP) zur Vorabbereitstellung des Unternehmensportals während der DEP-Registrierung verwenden, warnt Intune Sie, wenn das VPP-Token vor dem Ablauf steht und wenn die Lizenzen für das Unternehmensportal knapp werden.

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Sperren von Drittanbietertastaturen auf iOS-Geräten mithilfe der APP-Einstellungen <!-- 1248481 -->
Intune-Administratoren können zukünftig auf iOS-Geräten beim Zugriff auf Organisationsdaten, die in durch Richtlinien geschützten Apps hinterlegt sind, Tastaturen von Drittanbietern sperren. Wenn die Anwendungsschutzrichtlinie (APP) zur Sperrung von Drittanbietertastaturen konfiguriert ist, wird dem Gerätebenutzer eine Nachricht angezeigt, wenn dieser zum ersten Mal mit einer solchen Tastatur auf Unternehmensdaten zugreifen möchte. Dabei wird dem Benutzer nur die native Tastatur angezeigt. Alle anderen Tastaturen werden gesperrt und sind nicht sichtbar. Die Dialogmeldung wird dem Gerätebenutzer nur einmal angezeigt. 

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



