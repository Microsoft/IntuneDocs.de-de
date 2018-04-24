---
title: Einstellungen für Windows-Richtlinien
description: 'Verwenden Sie die allgemeine Windows-Konfigurationsrichtlinie (Windows 8.1 und höher) von Intune, um Einstellungen für registrierte Windows 8- und Windows 8.1-Geräte zu konfigurieren:'
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ccd5bd201de59537dbf99ea9e19d84dbf80c1a20
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="windows-policy-settings-in-microsoft-intune"></a>Einstellungen für Windows-Richtlinien in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Verwenden Sie die **allgemeine Windows-Konfigurationsrichtlinie (Windows 8.1 und höher)** von Microsoft Intune, um die folgenden Einstellungen für registrierte Windows 8-, Windows 8.1- und Windows RT 8.1-Geräte zu konfigurieren:

## <a name="applicability-settings"></a>Anwendbarkeitseinstellungen

|Name der Einstellung|Details|
|----------------|----------------------------------|
|**Alle Konfigurationen auf Windows 10 anwenden**|Aktiviert Einstellungen in dieser Richtlinie, die zusätzlich zu Windows 8- und Windows 8.1-Geräten auf Windows 10-Geräte angewendet werden.|

## <a name="security-settings"></a>Sicherheitseinstellungen

|Name der Einstellung|Details|
|----------------|------|
|**Erforderlicher Kennworttyp**|Gibt den erforderlichen Typ des Kennworts an, z.B. nur alphanumerisch oder numerisch.|
|**Erforderlicher Kennworttyp – Mindestanzahl von Zeichensätzen**|Gibt an, wie viele verschiedene Zeichensätze im Kennwort enthalten sein müssen. Es gibt vier Zeichensätze: Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole. Für iOS-Geräte gibt diese Einstellung jedoch die erforderliche Anzahl von Symbolen im Kennwort an.|
|**Minimale Kennwortlänge**|Konfiguriert die erforderliche Mindestlänge (in Zeichen) für das Kennwort.|
|**Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird**|Setzt das Gerät zurück, wenn diese Anzahl von Anmeldeversuchen fehlschlägt.|
|**Minuten der Inaktivität, bevor der Bildschirm ausgeschaltet wird**|Gibt die Anzahl von Minuten an, die ein Gerät im Leerlauf sein muss, bevor ein Kennwort zum Entsperren erforderlich ist.|
|**Kennwortablauf (Tage)**|Gibt die Anzahl der Tage an, bevor das Gerätekennwort geändert werden muss.|
|**Kennwortverlauf speichern**|Gibt an, ob der Benutzer zuvor verwendete Kennwörter konfigurieren kann.|
|**Kennwortverlauf speichern** – **Wiederverwendung vorheriger Kennwörter verhindern**|Gibt an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.|
|**Bildkennwort und PIN zulassen**|Aktiviert die Verwendung eines Bildkennworts und einer PIN. Mit einem Bildkennwort kann sich der Benutzer mit Gesten auf einem Bild anmelden. Mit einer PIN kann sich der Benutzer mit einem vierstelligen Code schnell anmelden.|

## <a name="encryption-settings"></a>Verschlüsselungseinstellungen

|                           Name der Einstellung                           |                     Details                      |
|------------------------------------------------------------------|--------------------------------------------------|
| <strong>Verschlüsselung auf mobilen Geräten vorschreiben</strong><sup>1</sup> | Erfordert die Verschlüsselung der Dateien auf dem Gerät. |

<sup>1</sup> Zusätzliche Informationen für Geräte unter Windows 8.1

-   Um die Verschlüsselung auf Geräten zu erzwingen, die Windows 8.1 ausführen, installieren Sie das [MDM-Clientupdate für Windows von Dezember 2014](http://support.microsoft.com/kb/3013816) auf jedem Gerät.

-   Wenn Sie diese Einstellung für Windows 8.1-Geräte aktivieren, müssen alle Benutzer des Geräts ein Microsoft-Konto haben.

-   Damit die Verschlüsselung funktioniert, muss das Gerät die Hardwarezertifizierungsanforderungen für Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) erfüllen.

-   Wenn Sie die Verschlüsselung auf einem Gerät erzwingen, ist der Wiederherstellungsschlüssel nur über das Microsoft-Konto des Benutzers zugänglich, auf das dieser über sein eigenes OneDrive-Konto zugreift. Sie können diesen Schlüssel nicht im Auftrag eines Benutzers wiederherstellen.

## <a name="malware-settings"></a>Malwareeinstellungen

|Name der Einstellung|Details|
|----------------|-----|
|**Netzwerkfirewall erforderlich**|Erfordert, dass die Windows-Firewall aktiviert sein muss.|
|**SmartScreen aktivieren**|Erfordert, dass Windows SmartScreen verwendet werden muss.|

## <a name="system-settings"></a>Systemeinstellungen

|Name der Einstellung|Details|
|----------------|-------|
|**Automatische Updates erforderlich**|Aktiviert die Einstellung für automatische Updates auf Geräten.|
|**Automatische Updates erforderlich – Mindestklassifizierung von Updates, die automatisch installiert werden**|Wählt die Klassifizierungen der Updates aus, die automatisch installiert werden:<br /><br />-   **Wichtig** – Installiert alle Updates, die als wichtig klassifiziert sind.<br />-   **Empfohlen** – Installiert alle Updates, die als wichtig oder empfohlen klassifiziert sind.|
|**Benutzerkontensteuerung**|Erfordert, dass die Benutzerkontensteuerung (User Account Control; UAC) auf Geräten verwendet werden muss.|
|**Übermitteln von Diagnosedaten zulassen**|Ermöglicht, dass das Gerät Diagnoseinformationen an Microsoft übermittelt.|


## <a name="cloud-settings--documents-and-data"></a>Cloudeinstellungen – Dokumente und Daten

|Name der Einstellung|Details|
|----------------|------|
|**URL der Arbeitsordner**|Legt die URL des Arbeitsordners so fest, dass Dokumente auf verschiedenen Geräten synchronisiert werden können.|

## <a name="email-settings"></a>E-Mail-Einstellungen

|Name der Einstellung|Details|
|----------------|-----|
|**Microsoft-Konto in Windows Mail-Anwendung optional machen**|Ermöglicht den Zugriff auf die Windows Mail-Anwendung ohne Microsoft-Konto.|

## <a name="application-settings---browser"></a>Anwendungseinstellungen – Browser

|Name der Einstellung|Details|
|----------------|-----|
|**AutoAusfüllen zulassen**|Ermöglicht Benutzern, die Einstellungen für AutoVervollständigen im Browser zu ändern.|
|**Popupblocker zulassen**|Aktiviert oder deaktiviert den Popupblocker des Browsers.|
|**Plug-Ins zulassen**|Ermöglicht Benutzern, Plug-Ins zu Internet Explorer hinzuzufügen.|
|**Active Scripting zulassen**|Ermöglicht dem Browser, Skripts auszuführen, z.B. ActiveX-Skripts.|
|**Betrugswarnung zulassen**|Aktiviert oder deaktiviert Warnungen zu potenziell betrügerischen Websites.|
|**Wechsel zu Intranetsite nach Eingabe eines einzelnen Worts zulassen**|Ermöglicht die Verwendung eines einzelnen Worts, um Internet Explorer auf eine Website wie „Bing“ weiterzuleiten.|
|**Automatische Erkennung des Intranets zulassen**|Hilft bei der Konfiguration der Sicherheit für Intranetsites in Internet Explorer.|
|**Sicherheitsstufe für Internet**|Legt die Internet Explorer-Sicherheitsstufe für Internetsites fest.|
|**Sicherheitsstufe für Intranet**|Legt die Internet Explorer-Sicherheitsstufe für Intranetsites fest.|
|**Sicherheitsstufe für vertrauenswürdige Sites**|Konfiguriert die Sicherheitsstufe für die Zone vertrauenswürdiger Sites.|
|**Sicherheitsstufe für eingeschränkte Sites**|Konfiguriert die Sicherheitsstufe für Zone eingeschränkter Sites.|
|**DNT-Kopfzeile senden**|Hiermit wird ein DNT-Header (Do Not Track, nicht nachverfolgen) an besuchte Websites in Internet Explorer gesendet.|
|**Zugriff auf das Menü „Unternehmensmodus“ zulassen**|Ermöglicht dem Benutzer, auf die Menüoptionen für den Unternehmensmodus von Internet Explorer zuzugreifen.<br>Wenn Sie diese Einstellung ausgewählt haben, können Sie auch einen **Speicherort des Protokollberichts** angeben. Dieser enthält eine URL zu einem Bericht, in dem Websites angezeigt werden, für die Benutzer Zugriff im Unternehmensmodus aktiviert haben.|
|**Ort der Standortliste für Enterprise-Modus**|Gibt den Speicherort der Liste der Websites an, die den Unternehmensmodus verwenden, wenn er aktiv ist.|

## <a name="device-capabilities-settings---cellular"></a>Einstellungen für Gerätefunktionen - Mobiltelefon

|Name der Einstellung|Details|
|----------------|----|
|**Datenroaming zulassen**|Ermöglicht das Datenroaming, wenn das Gerät in einem Mobilfunknetz verwendet wird.|



### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
