---
title: Sicherheitsrichtlinieneinstellungen für mobile Geräte
description: Verwenden Sie Intune, um eine Vielzahl von Einstellungen zu konfigurieren, die Sie für verwaltete Geräte in Ihrer Organisation bereitstellen können.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 83536a4d9858454505a84a2e394ace1119255049
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31031854"
---
# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Sicherheitsrichtlinieneinstellungen für mobile Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> Microsoft Intune bietet nun separate Konfigurationsrichtlinien für jede Geräteplattform. Diese Richtlinien enthalten die neuesten Einstellungen, die Sie verwenden können. Sie können die Sicherheitsrichtlinie für mobile Geräte weiterhin nutzen, wobei alle vorhandenen Bereitstellungen weiterhin funktionieren. Sie sollten allerdings die Migration zu den neuen Konfigurationsrichtlinien so bald wie möglich planen, da die Sicherheitsrichtlinie für mobile Geräte in Zukunft entfernt werden wird.

Sie können die Intune-Sicherheitsrichtlinien für mobile Geräte verwenden, um eine Vielzahl von Einstellungen zu konfigurieren, die Sie für verwaltete Geräte in Ihrer Organisation bereitstellen können. Diese Einstellungen werden dazu verwendet, die Funktionalität und die Sicherheit Ihrer Geräte zu steuern.

Sie können die Sicherheitsrichtlinien für mobile Geräte für die folgenden Gerätetypen erstellen und bereitstellen:

-   Windows RT 8.1-Geräte und registrierte Windows 8.1-Geräte

-   Windows RT

-   Windows Phone 8 und Windows Phone 8.1

-   iOS

-   Android und Samsung KNOX Standard

> [!NOTE]
> Einige Einstellungen sind auf einigen Geräten nicht anwendbar. In den nachfolgenden Tabellen finden Sie eine vollständige Liste der Einstellungen, die Sie konfigurieren können.
> Ab Oktober 2016 wird Microsoft Intune die Unterstützung für Windows 8-Unternehmensportal-Apps beenden. Microsoft Intune wird auch die Unterstützung für die Windows Phone 8- und WinRT-Plattformen beenden. Die Registrierung oder Aktualisierung von Windows Phone 8- oder WinRT-Geräten wird daher nicht mehr möglich sein. Bereits registrierte Windows Phone 8-, WinRT- und Windows 8-Geräte können weiterhin verwaltet werden. Aktualisieren Sie Windows Phone 8- und Windows 8-Geräte auf Windows Phone 8.1 und Windows 8.1, und nutzen Sie die entsprechenden Windows Phone 8.1- und Windows 8.1-Unternehmensportal-Apps, um weiterhin Apps an diese Geräte verteilen zu können.

## <a name="security-settings"></a>Sicherheitseinstellungen

|                                                                                                                                                                                        Name der Einstellung                                                                                                                                                                                         | Windows 8.1 und Windows RT 8.1 | Windows RT | Windows Phone 8 und Windows Phone 8.1 |       iOS       | Android und Samsung KNOX Standard |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------|---------------------------------------|-----------------|-----------------------------------|
|                                                                                                                                                                <strong>Anfordern eines Kennworts zum Entsperren mobiler Geräte</strong>                                                                                                                                                                 |               Nein               |     Nein     |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                 <strong>Erforderlicher Kennworttyp</strong><br /><br />Diese Einstellung gibt den erforderlichen Typ des Kennworts an, z.B. nur numerisch oder alphanumerisch.                                                                                                                 |              Ja                |    Ja      |                  Ja                   |       Ja        |                Nein                 |
| <strong>Erforderlicher Kennworttyp – Mindestanzahl von Zeichensätzen</strong><br /><br />Es gibt vier Zeichensätze: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. Diese Einstellung gibt an, wie viele Zeichensätze im Kennwort enthalten sein müssen. Für iOS-Geräte wird hiermit jedoch die erforderliche Anzahl von Symbolzeichen im Kennwort angegeben. |              Ja                |    Ja      |                  Ja                   |       Ja        |                Nein                 |
|                                                                                                                                                                          <strong>Minimale Kennwortlänge</strong>                                                                                                                                                                           |              Ja                |    Ja      |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                                               <strong>Einfache Kennwörter zulassen</strong><br /><br />Einfache Kennwörter sind z. B. '0000' und '1234'.                                                                                                                                                |               Nein               |     Nein     |                  Ja                   |       Ja        |                Nein                 |
|                                                                                                                                                  <strong>Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird</strong>                                                                                                                                                   |              Ja                |    Ja      |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                                                         <strong>Minuten Inaktivität bis zur Abschaltung des Bildschirms</strong><sup>1</sup>                                                                                                                                                          |              Ja                |    Ja      |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                                                                         <strong>Kennwortablauf (Tage)</strong>                                                                                                                                                                         |              Ja                |    Ja      |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                                                                         <strong>Kennwortverlauf speichern</strong>                                                                                                                                                                          |              Ja                |    Ja      |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                                              <strong>Kennwortverlauf speichern</strong> – <strong>Wiederverwendung vorheriger Kennwörter verhindern</strong>                                                                                                                                              |              Ja                |    Ja      |                  Ja                   |       Ja        |                Ja                 |
|                                                                                                                                                                              <strong>Kennwortqualität</strong>                                                                                                                                                                              |               Nein               |     Nein     |                  Nein                   |       Nein        |                Ja                 |
|                                                                                                                                                                       <strong>Bildkennwort und PIN zulassen</strong>                                                                                                                                                                       |              Ja                |    Ja      |                  Nein                   |       Nein        |                Nein                 |
|                                                                                                                                                             <strong>Minuten Inaktivität vor Anforderung des Kennworts</strong>                                                                                                                                                              |               Nein               |     Nein     |                  Nein                   |       Ja        |                Nein                 |
|                                                                                                                                                                          <strong>Fingerabdruckentsperrung zulassen</strong>                                                                                                                                                                          |               Nein               |     Nein     |                  Nein                   | iOS 7 und höher |                Nein                 |

<sup>1</sup> Wenn Sie für iOS-Geräte die Einstellungen **Minuten Inaktivität bis zur Abschaltung des Bildschirms** und **Minuten Inaktivität vor Anforderung des Kennworts** konfigurieren, werden diese nacheinander angewendet. Wenn Sie beispielsweise den Wert für beide Einstellungen auf **5** Minuten einstellen, wird der Bildschirm automatisch nach 5 Minuten deaktiviert, und das Gerät wird nach weiteren 5 Minuten gesperrt. Wenn der Benutzer den Bildschirm jedoch manuell deaktiviert, wird die zweite Einstellung sofort angewendet. Im selben Beispiel wird das Gerät 5 Minuten später gesperrt, nachdem der Benutzer den Bildschirm deaktiviert hat.

Wenn Sie eine Kennwortlängenrichtlinie für Geräte mit Windows RT bereitstellen, müssen Benutzer ihr Kennwort zurücksetzen, selbst wenn ihr aktuelles Kennwort den Richtlinienanforderungen entspricht.

## <a name="encryption-settings"></a>Verschlüsselungseinstellungen

|                                                                                                                                     Name der Einstellung                                                                                                                                     | Windows 8.1 und Windows RT 8.1 | Windows RT |              Windows Phone 8 und Windows Phone 8.1              | iOS | Android und Samsung KNOX Standard |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------|------------|-----------------------------------------------------------------|-----|-----------------------------------|
| <strong>Verschlüsselung auf mobilen Geräten vorschreiben</strong><sup>1</sup><br /><br />Für Windows Phone 8-Geräte müssen Sie hier <strong>Ja</strong>festlegen.<br /><br />Aktivieren Sie zum Verwenden der Verschlüsselung auf iOS-Geräten die Einstellung <strong>Kennwort zum Entsperren mobiler Geräte erforderlich</strong>. |              Ja                |     Nein     |                               Ja                                | Nein  |                Ja                 |
|                                                                    <strong>Verschlüsselung auf Speicherkarten vorschreiben</strong><br /><br />Diese Einstellung gilt auch für Geräte, die mit Exchange ActiveSync verwaltet werden.                                                                     |              Nicht zutreffend               |    Nicht zutreffend     | Nicht zutreffend <br />Apps und zugehörige Daten werden automatisch verschlüsselt. | Nicht zutreffend |                Ja                 |

<sup>1</sup>Hier finden Sie zusätzliche Informationen für Geräte mit Windows 8.1:

-   Um die Verschlüsselung auf Geräten zu erzwingen, die Windows 8.1 ausführen, installieren Sie das [MDM-Clientupdate für Windows von Dezember 2014](http://support.microsoft.com/kb/3013816) auf jedem Gerät.

-   Wenn Sie diese Einstellung für Windows 8.1-Geräte aktivieren, müssen alle Benutzer des Geräts ein Microsoft-Konto haben.

-   Damit die Verschlüsselung funktioniert, muss das Gerät die Hardwarezertifizierungsanforderungen für Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) erfüllen.

-   Wenn Sie die Verschlüsselung auf einem Gerät erzwingen, ist der Wiederherstellungsschlüssel nur über das Microsoft-Konto des Benutzers zugänglich, auf das dieser über sein eigenes OneDrive-Konto zugreift. Sie können diesen Schlüssel nicht im Auftrag eines Benutzers wiederherstellen.

## <a name="malware-settings"></a>Malwareeinstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Netzwerkfirewall erforderlich**|Ja |Nein|Nein|Nein|Nein|
|**SmartScreen aktivieren**|Ja |Nein|Nein|Nein|Nein|

## <a name="system-settings"></a>Systemeinstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Automatische Updates erforderlich**|Ja |Nein|Nein|Nein|Nein|
|**Automatische Updates erforderlich – Mindestklassifizierung von Updates, die automatisch installiert werden**<br /><br />Wählen Sie die Klassifizierungen der Updates, die automatisch installiert werden:<br /><br />- **Wichtig**. Installiert alle Updates, die als wichtig klassifiziert sind.<br /><br />- **Empfohlen**. Installiert alle Updates, die als wichtig oder empfohlen klassifiziert sind.|Ja |Nein|Nein|Nein|Nein|
|**Bildschirmaufnahme zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja |Ja (nur Samsung KNOX Standard)|
|**Kontrollcenter auf Sperrbildschirm zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Benachrichtigungsansicht auf Sperrbildschirm zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Ansicht „Heute“ auf Sperrbildschirm zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Benutzerkontensteuerung**|Ja |Nein|Nein|Nein|Nein|
|**Übermitteln von Diagnosedaten zulassen**|Ja |Nein|Nur Windows Phone 8.1|Ja |Ja (nur Samsung KNOX Standard)|
|**Nicht vertrauenswürdige TLS-Zertifikate zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Persönliche Wallet-Software während Sperrung zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Zurücksetzen auf Werkseinstellungen zulassen**|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|


## <a name="cloud-settings--documents-and-data"></a>Cloudeinstellungen – Dokumente und Daten

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Sicherung in iCloud zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Dokumentsynchronisierung in iCloud zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Fotostream-Synchronisierung auf iCloud zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Verschlüsselte Sicherung erforderlich**|Nein|Nein|Nein|Ja |Nein|
|**URL der Arbeitsordner**<br /><br />Diese Einstellung legt die URL des Arbeitsordners so fest, dass Dokumente auf verschiedenen Geräten synchronisiert werden können.|Ja |Nein|Nein|Nein|Nein|
|**Google-Sicherung zulassen**|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|

## <a name="cloud-settings--accounts-and-synchronization"></a>Cloudeinstellungen – Konten und Synchronisierung

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Microsoft-Konto zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|
|**Automatische Synchronisierung von Google-Konto zulassen**|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|

## <a name="email-settings"></a>E-Mail-Einstellungen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Das Herunterladen von E-Mail-Anlagen durch Benutzer zulassen**<sup>1</sup>|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|**Synchronisierungszeitraum für E-Mail** <br /><br />Diese Einstellung gilt auch für Geräte, die mit Exchange ActiveSync verwaltet werden.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|**Synchronisierung mit Exchange für mobile Geräte zulassen, von denen diese Einstellungen nicht vollständig unterstützt werden (Exchange ActiveSync)** <br /><br />Diese Einstellung gilt auch für Geräte, die mit Exchange ActiveSync verwaltet werden.|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|Nicht zutreffend|
|**Microsoft-Konto in Windows Mail-Anwendung optional machen**|Ja |Nein|Nein|Nein|Nein|
|**Benutzerdefinierte E-Mail-Konten zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|

## <a name="application-settings---browser"></a>Anwendungseinstellungen – Browser

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Webbrowser zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja |Ja (nur Samsung KNOX Standard)|
|**AutoAusfüllen zulassen**|Ja |Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Popupblocker zulassen**|Ja |Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Cookies zulassen**|Nein|Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Plug-Ins zulassen**|Ja |Nein|Nein|Nein|Nein|
|**Active Scripting zulassen**|Ja |Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Betrugswarnung zulassen**|Ja |Nein|Nein|Ja |Nein|
|**Wechsel zu Intranetsite nach Eingabe eines einzelnen Worts zulassen**<br /><br />(Diese Einstellung ermöglicht die Verwendung eines einzelnen Wortes, um Internet Explorer auf eine Website zu leiten, z.B. „Bing“.)|Ja |Nein|Nein|Nein|Nein|
|**Automatische Erkennung des Intranets zulassen**|Ja |Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für Internet**|Ja |Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für Intranet**|Ja |Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für vertrauenswürdige Sites**|Ja |Nein|Nein|Nein|Nein|
|**Sicherheitsstufe für eingeschränkte Sites**|Ja |Nein|Nein|Nein|Nein|
|**DNT-Kopfzeile senden**|Ja |Nein|Nein|Nein|Nein|
|**Zugriff auf das Menü „Unternehmensmodus“ zulassen**|Ja |Nein|Nein|Nein|Nein|
|**Ort der Standortliste für Enterprise-Modus**|Ja |Nein|Nein|Nein|Nein|

## <a name="application-settings---apps"></a>Anwendungseinstellungen – Apps

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Anwendungsspeicher zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja |Ja (nur Samsung KNOX Standard)|
|**Kennwort für den Zugriff auf den Anwendungsspeicher erforderlich**|Nein|Nein|Nein|Ja |Nein|
|**In-App-Einkäufe zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Verwaltete Dokumente in anderen nicht verwalteten Apps zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Nicht verwaltete Dokumente in anderen verwalteten Apps zulassen**|Nein|Nein|Nein|iOS 7 und höher|Nein|
|**Videokonferenz zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Nicht jugendfreie Inhalte im Medienstore zulassen**|Nein|Nein|Nein|Ja |Nein|
|**App-Installation zulassen**|Nein|Nein|Nein|iOS 6 und höher|Nein|

## <a name="application-settings---gaming"></a>Anwendungseinstellungen – Spiele

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Game Center-Freunde zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Spielen für mehrere Spieler zulassen**|Nein|Nein|Nein|Ja |Nein|

## <a name="device-capabilities-settings---hardware"></a>Einstellungen für Gerätefunktionen - Hardware

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Kamera zulassen**|Nein|Nein|Nur Windows Phone 8.1|Ja |Ja |
|**Wechselspeichermedien zulassen**|Nein|Nein|Ja |Nein|Ja (nur Samsung KNOX Standard)|
|**WLAN zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (nur Samsung KNOX Standard)|
|**WLAN-Tethering zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (nur Samsung KNOX Standard)|
|**Automatische Verbindung mit freien WLAN-Hotspots zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|
|**WLAN-Hotspotmeldung zulassen**<br /><br />Diese Einstellung sendet Informationen über WLAN-Verbindungen, um nahegelegene Verbindungen zu ermitteln.|Nein|Nein|Nur Windows Phone 8.1|Nein|Nein|
|**Geolocation zulassen**<br /><br />Diese Einstellung erlaubt dem Gerät die Nutzung von Standortinformationen.|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (nur Samsung KNOX Standard)|
|**NFC zulassen**<br /><br />Diese Einstellung erlaubt Vorgänge, die NFC (Near Field Communication) verwenden.|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (nur Samsung KNOX Standard)|
|**Bluetooth zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (nur Samsung KNOX Standard)|
|**Ausschalten zulassen**<br>Wenn diese Einstellung deaktiviert ist, funktioniert die Einstellung **Anzahl der zulässigen wiederholten Anmeldefehler, bevor die Gerätedaten zurückgesetzt werden** für Samsung KNOX Standard-Geräte nicht.|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|

## <a name="device-capabilities-settings---cellular"></a>Einstellungen für Gerätefunktionen - Mobiltelefon

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Sprachroaming zulassen**|Nein|Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Datenroaming zulassen**|Ja |Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Automatische Synchronisierung beim Roaming zulassen**|Nein|Nein|Nein|Ja |Nein|
|**SMS- und MMS-Nachrichten zulassen**|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|

## <a name="device-capabilities-settings---features"></a>Einstellungen für Gerätefunktionen - Funktionen

|Name der Einstellung|Windows 8.1 und Windows RT 8.1|Windows RT|Windows Phone 8 und Windows Phone 8.1|iOS|Android und Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Sprach-Assistent zulassen**|Nein|Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Sprach-Assistent bei gesperrtem Gerät zulassen**|Nein|Nein|Nein|Ja |Nein|
|**Sprachwahl zulassen**|Nein|Nein|Nein|Ja |Ja (nur Samsung KNOX Standard)|
|**Kopieren und Einfügen zulassen**|Nein|Nein|Nur Windows Phone 8.1|Nein|Ja (nur Samsung KNOX Standard)|
|**Gemeinsame Nutzung der Zwischenablage durch Anwendungen zulassen**|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|
|**YouTube zulassen**|Nein|Nein|Nein|Nein|Ja (nur Samsung KNOX Standard)|

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
