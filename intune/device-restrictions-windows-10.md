---
title: Intune-Einstellungen für Geräteeinschränkungen für Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: In diesem Artikel lernen Sie die Microsoft Intune-Einstellungen zur Steuerung von Geräteeinstellungen und -funktionen auf Windows 10-Geräten kennen.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 42e0798b0c2941d9ea45e75b367b69bc7dab548f
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321219"
---
# <a name="device-restriction-for-windows-10-and-newer-settings-in-intune"></a>Gerätebeschränkungen für Einstellungen unter Windows 10 (und höher) in Intune
In diesem Artikel erfahren Sie alle Einstellungen für Microsoft Intune-Geräteeinschränkungen, die Sie für Windows 10-Geräte konfigurieren können.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Allgemein
- **Bildschirmaufnahme (nur Mobilgerät):** Erlaubt dem Benutzer, den Bildschirm des Geräts als Bild zu erfassen.
- **Kopieren und einfügen (nur mobil):** Erlaubt Kopier- und Einfügevorgänge zwischen Apps auf dem Gerät.
- **Manuelle Aufhebung der Registrierung:** Erlaubt dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät.
   - Diese Richtlinieneinstellung wird nicht angewendet, wenn der Computer mit Azure Active Directory verknüpft ist und die automatische Registrierung aktiviert ist. 
   - Diese Richtlinieneinstellung gilt nicht für Computer, auf denen Windows 10 Home ausgeführt wird.
- **Manuelle Installation von Stammzertifikaten (nur Mobilgerät):** Hindert den Benutzer daran, Stammzertifikate und CAP-Zwischenzertifikate manuell zu installieren.

- **Kamera:** Erlaubt oder sperrt die Verwendung der Kamera auf dem Gerät.
- **OneDrive-Dateisynchronisierung:** Hindert das Gerät daran, Dateien mit OneDrive zu synchronisieren.
- **Wechselmedien:** Gibt an, ob externe Speichergeräte wie SD-Karten mit dem Gerät verwendet werden können.
- **Geolocation:** Gibt an, ob das Gerät Standortdienstinformationen verwenden kann.
- **Internetfreigabe:** Erlaubt die gemeinsame Nutzung der Internetverbindung auf dem Gerät.
- **Zurücksetzung des Telefons:** Steuert, ob Benutzer ihre Geräte auf die Werkseinstellungen zurücksetzen können.
- **USB-Verbindung (nur Mobilgerät):** Steuert, ob Geräte über eine USB-Verbindung auf externe Speichergeräte zugreifen können.
- **AntiTheft-Modus (nur Mobilgerät)**: Konfigurieren Sie, ob der Windows-AntiTheft-Modus aktiviert ist.
- **Cortana:** Aktiviert oder deaktiviert den Cortana-Sprach-Assistenten.
- **Sprachaufzeichnung (nur Mobilgerät):** Erlaubt oder sperrt die Verwendung der Sprachaufzeichnung des Geräts.
- **Bearbeitung des Gerätenamens:** Verhindert, dass der Endbenutzer den Gerätenamen ändert (nur Windows 10 Mobile).
- **Bereitstellungspakete hinzufügen:** Blockiert den Laufzeitkonfigurations-Agent, der Bereitstellungspakete installiert.
- **Bereitstellungspakete entfernen:** Blockiert den Laufzeitkonfigurations-Agent, der Bereitstellungspakete entfernt.
- **Geräteerkennung:** Verhindert, dass ein Gerät von anderen Geräten erkannt wird.
- **Programmumschaltung (nur mobile Geräte):** Blockiert die Programmumschaltung auf dem Gerät.
- **Dialogfeld bei SIM-Kartenfehler (nur mobile Geräte):** Blockiert die Anzeige einer Fehlermeldung auf dem Gerät, wenn keine SIM-Karte erkannt wird.
- **Ink-Arbeitsbereich:** Blockiert den Benutzerzugriff auf den Ink-Arbeitsbereich. Wenn diese Einstellung nicht konfiguriert ist, ist der Ink-Arbeitsbereich aktiviert (Feature ist aktiviert), und der Benutzer kann ihn über den Sperrbildschirm verwenden.
- **Automatische erneute Bereitstellung:** Ermöglicht es Benutzern mit Administratorrechten, alle Benutzerdaten und -einstellungen über **STRG+Windows+R** vom Sperrbildschirm des Geräts aus zu löschen. Das Gerät wird automatisch neu konfiguriert und bei der Verwaltung neu registriert.

## <a name="password"></a>Kennwort
-   **Kennwort:** Der Endbenutzer muss ein Kennwort eingeben, um auf das Gerät zugreifen zu können.
    -   **Erforderlicher Kennworttyp:** Gibt an, ob das Kennwort nur numerisch sein muss oder alphanumerisch.
    -   **Minimale Kennwortlänge:** Gilt nur für Windows 10 Mobile.
    -   **Anzahl von Anmeldefehlern, bevor das Gerät zurückgesetzt wird:** Für Geräte mit Microsoft 10: Wenn auf dem Gerät BitLocker aktiviert ist, wird in den BitLocker-Wiederherstellungsmodus gewechselt, sobald die Anzahl der von Ihnen angegebenen Anmeldefehler erreicht ist. Wenn BitLocker nicht für dieses Gerät aktiviert ist, wird diese Einstellung nicht angewendet.
Für Geräte mit Windows 10 Mobile: Das Gerät wird zurückgesetzt, sobald die Anzahl der von Ihnen angegebenen Anmeldeversuche fehlgeschlagen ist.
    -   **Maximaler Zeitraum der Inaktivität (in Minuten) bis zur Bildschirmsperrung:** Gibt den Zeitraum der Inaktivität für ein Gerät an, bevor der Bildschirm gesperrt wird.
    -   **Kennwortablauf (Tage):** Gibt die Zeitdauer an, nach der das Kennwort für das Gerät geändert werden muss.
    -   **Wiederverwendung vorheriger Kennwörter verhindern:** Gibt an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.
    -   **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt (nur Mobile):** Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss (nur Windows 10 Mobile).
    -   **Einfache Kennwörter:** Erlaubt die Verwendung einfacher Kennwörter wie 1111 oder 1234. Diese Einstellung ermöglicht es auch, die Verwendung von Windows-Bildcodes zu blockieren.
-   **Verschlüsselung**: Aktivieren der Verschlüsselung auf Zielgeräten

## <a name="personalization"></a>Personalization

- **URL zu Desktophintergrundbild (nur Desktop):** Gibt die URL zu einem Bild im JPEG-Format an, das Sie als Windows-Desktophintergrund verwenden möchten. Benutzer können diese nicht ändern.

## <a name="privacy"></a>Datenschutz

-   **Eingabepersonalisierung:** Verhindert die Verwendung cloudbasierter Sprachdienste für Cortana, Diktierfunktionen oder Microsoft Store-Apps. Wenn Sie diese Dienste zulassen, kann Microsoft Voice-Daten erfassen, um den Dienst zu verbessern.
-   **Automatisches Akzeptieren der Zustimmungsaufforderung des Benutzers zu Kopplung und Datenschutz:** Erlaubt Windows beim Ausführen von Apps das automatische Akzeptieren von Benachrichtigungen zur Zustimmung zu Kopplung und Datenschutz.
- **Benutzeraktivitäten veröffentlichen:** Legen Sie diese Einstellung auf **Blockieren** fest, um geteilte Aktivitäten und die Ermittlungen von kürzlich verwendeten Ressourcen in der Programmumschaltung zu vermeiden.
- **Nur lokale Aktivitäten:** Legen Sie diese Einstellungen auf **Blockieren** fest, um geteilte Aktivitäten und Ermittlungen von kürzlich in der Programmumschaltung verwendeten Ressourcen anhand von ausschließlich lokalen Aktivitäten zu vermeiden.

Sie können Informationen definieren, auf die alle Anwendungen auf dem Gerät zugreifen können. Zudem können Sie mithilfe von **App-bezogenen Datenschutzausnahmen** Ausnahmen für jede App definieren.

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen**: Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps**: Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender**: Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste**: Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera**: Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte**: Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail**: Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Standort**: Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten**: Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon**: Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung**: Legen Sie fest, ob diese App auf die Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen**: Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon**: Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Radios**: Einige Apps verwenden Radios (z.B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diese Radios ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben**: Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte**: Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden darf, d.h. bereits angeschlossene oder im Lieferumfang dieses PC, Tablets oder Telefons enthaltene Hardware. Hierzu zählen z.B. TV-Geräte und Projektoren.
- **Feedback und Diagnose**: Legen Sie fest, ob diese App auf Diagnoseinformationen zugreifen darf.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit Ihrem PC, Tablet oder Telefon gekoppelt sind.

## <a name="per-app-privacy-exceptions"></a>App-bezogene Datenschutzausnahmen

Sie können Apps hinzufügen, die ein anderes Datenschutzverhalten aufweisen als das unter „Standarddatenschutz“ definierte Verhalten.

- **Paketname**: App-Paketfamilienname
- **Name**: Der Name der App

### <a name="exceptions"></a>Ausnahmen

- **Kontoinformationen**: Legen Sie fest, ob diese App auf den Benutzernamen, das Bild und andere Kontaktinformationen zugreifen darf.
- **Hintergrund-Apps**: Legen Sie fest, ob diese App im Hintergrund ausgeführt werden darf.
- **Kalender**: Legen Sie fest, ob diese App auf den Kalender zugreifen darf.
- **Anrufliste**: Legen Sie fest, ob diese App auf Ihre Anrufliste zugreifen darf.
- **Kamera**: Legen Sie fest, ob diese App auf die Kamera zugreifen darf.
- **Kontakte**: Legen Sie fest, ob diese App auf Kontakte zugreifen darf.
- **E-Mail**: Legen Sie fest, ob diese App auf E-Mails zugreifen und diese versenden darf.
- **Standort**: Legen Sie fest, ob diese App auf Standortinformationen zugreifen darf.
- **Nachrichten**: Legen Sie fest, ob diese App SMS oder MMS-Nachrichten lesen oder senden darf.
- **Mikrofon**: Legen Sie fest, ob diese App das Mikrofon verwenden darf.
- **Bewegung**: Legen Sie fest, ob diese App auf die Gerätebewegungsinformationen zugreifen darf.
- **Benachrichtigungen**: Legen Sie fest, ob diese App auf Benachrichtigungen zugreifen darf.
- **Telefon**: Legen Sie fest, ob diese App auf das Telefon zugreifen darf.
- **Radios**: Einige Apps verwenden Radios (z.B. Bluetooth) auf Ihrem Gerät, um Daten zu senden und zu empfangen, und müssen diese Radios ein- oder ausschalten. Legen Sie fest, ob diese App diese Radios steuern kann.
- **Aufgaben**: Legen Sie fest, ob diese App auf Ihre Aufgaben zugreifen darf.
- **Vertrauenswürdige Geräte**: Legen Sie fest, ob diese App vertrauenswürdige Geräte verwenden darf, d.h. bereits angeschlossene oder im Lieferumfang dieses PC, Tablets oder Telefons enthaltene Hardware. Hierzu zählen z.B. TV-Geräte und Projektoren.
- **Feedback und Diagnose**: Legen Sie fest, ob diese App auf Diagnoseinformationen zugreifen darf.
- **Mit Geräten synchronisieren**: Legen Sie fest, ob diese App automatisch Informationen mit Drahtlosgeräten teilen und synchronisieren darf, die nicht explizit mit Ihrem PC, Tablet oder Telefon gekoppelt sind.

## <a name="locked-screen-experience"></a>Gesperrter Bildschirm

- **Info-Center-Benachrichtigungen (nur Mobilgerät):** Lässt Info-Center-Benachrichtigungen auf dem Gerätesperrbildschirm anzeigen (nur Windows 10 Mobile).
- **URL zu Bild für gesperrten Bildschirm (nur Desktop):** Gibt die URL zu einem Bild im JPEG-Format an, das als Hintergrund für den Windows-Sperrbildschirm verwendet wird. Benutzer können diese nicht ändern.
-   **Vom Benutzer konfigurierbares Bildschirmtimeout (nur Mobilgeräte):** Ermöglicht Benutzern das Einstellen der Zeitspanne. 
-   **Cortana auf Sperrbildschirm (nur Desktop):** Lässt nicht zu, dass der Benutzer mit Cortana interagiert, wenn auf dem Gerät der Sperrbildschirm zu sehen ist (nur Windows 10 Desktop).
-   **Popupbenachrichtigungen auf Sperrbildschirm:** Verhindert, dass Warnmeldungen auf dem Gerätesperrbildschirm angezeigt werden.
-   **Bildschirmtimeout (nur Mobilgerät):** Gibt die Zeit in Sekunden an, nach der der gesperrte Bildschirm ausgeschaltet wird.

## <a name="app-store"></a>App Store

-   **App Store (nur mobil):** Erlaubt oder sperrt die Verwendung des App Stores auf Windows 10 Mobile-Geräten.
-   **Apps aus Store automatisch aktualisieren:** Ermöglicht die automatische Aktualisierung von Apps, die aus dem Microsoft Store installiert wurden.
-   **Installation vertrauenswürdiger Apps:** Ermöglicht das Querladen von Apps, die mit einem vertrauenswürdigen Zertifikat signiert sind.
-   **Entwicklersperre aufheben:** Ermöglicht dem Endbenutzer, Windows-Entwicklereinstellungen – z.B. das Zulassen quergeladener Apps – zu ändern.
-   **Gemeinsam genutzte App-Benutzerdaten:** Ermöglicht Apps, die gemeinsame Nutzung von Daten durch verschiedene Benutzer auf dem gleichen Gerät zuzulassen.
-   **Nur privaten Store verwenden:** Aktivieren Sie diese Option, um Endbenutzern das Herunterladen von Apps nur aus Ihrem privaten Store zu ermöglichen.
-   **Store-App starten:** Hiermit werden alle Apps deaktiviert, die bereits auf dem Gerät installiert waren oder aus dem Microsoft Store heruntergeladen wurden.
-   **App-Daten in Systemvolume installieren:** Hindert Apps daran, Daten auf dem Systemvolume des Geräts zu speichern.
-   **Apps auf Systemlaufwerk installieren:** Hindert Apps daran, Daten auf dem Systemlaufwerk des Geräts zu speichern.
-   **Game DVR (nur Desktop):** Konfiguriert, ob Aufzeichnen und Senden von Spielen zulässig ist.
-   **Nur Apps aus dem Store**: Konfiguriert, ob Benutzer Apps von anderen Orten als aus dem App-Store installieren können.

## <a name="edge-browser"></a>Microsoft Edge-Browser

-   **Microsoft Edge-Browser (nur mobil):** Erlaubt die Verwendung des Edge-Webbrowsers auf dem Gerät.
-   **Adressleisten-Dropdown (nur Desktop):** Verhindert, dass Microsoft Edge bei der Eingabe weiterhin eine Liste mit Vorschlägen in einer Dropdownliste anzeigt. So kann die zwischen Microsoft Edge und Microsoft-Diensten genutzte Netzwerkbandbreite minimiert werden.
-   **Favoriten zwischen Microsoft-Browsern synchronisieren (nur Desktop):** Erlaubt Windows das Synchronisieren von Favoriten zwischen Internet Explorer und Microsoft Edge.
-   **DNT-Kopfzeilen senden:** Konfiguriert den Microsoft Edge-Browser zum Senden von DNT-Headern (Do Not Track, nicht nachverfolgen) an Websites, die Benutzer besuchen.
-   **Cookies:** Erlaubt Browsern das Speichern von Internetcookies auf dem Gerät.
-   **Javascript:** Erlaubt die Ausführung von Skripts wie z.B. JavaScript im Microsoft Edge-Browser.
-   **Popups:** Blockiert Popupfenster im Browser (gilt nur für Windows 10 Desktop).
-   **Suchvorschläge:** Ermöglicht der Such-Engine, Websites während der Eingabe von Suchausdrücken vorzuschlagen.
-   **Datenverkehr im Intranet an Internet Explorer senden:** Erlaubt Benutzern, Intranetsites in Internet Explorer zu öffnen (nur Windows 10 Desktop).
-   **AutoAusfüllen:** Erlaubt Benutzern, die Einstellungen für AutoAusfüllen im Browser zu ändern (nur Windows 10 Desktop).
-   **Kennwort-Manager:** Aktiviert oder deaktiviert den Microsoft Edge-Kennwort-Manager.
-   **Speicherort der Websiteliste für den Unternehmensmodus:** Gibt an, wo Sie die Liste der Websites finden, die im Unternehmensmodus geöffnet werden. Benutzer können diese Liste nicht bearbeiten.<br>(Nur Windows 10 Desktop)
-   **Entwicklungstools:** Hindert den Endbenutzer daran, die Microsoft Edge-Entwicklertools aufzurufen.
-   **Erweiterungen:** Erlaubt dem Benutzer, Microsoft Edge-Erweiterungen auf dem Gerät zu installieren.
-   **InPrivate-Browsen:** Hindert den Endbenutzer daran, InPrivate-Browsersitzungen zu öffnen.
-   **Anzeigen der „Willkommen“-Seite:** Verhindert, dass die Einführungsseite bei der ersten Ausführung von Microsoft Edge angezeigt wird.
    -   **URL für erste Ausführung:** Gibt die URL einer Seite an, die bei der ersten Ausführung von Microsoft Edge angezeigt wird (nur Windows 10 Mobile).
-   **Startseiten:** Fügt eine Liste der Websites hinzu, die Sie im Microsoft Edge-Browser als Startseiten verwendet möchten (nur Desktop).
-   **Änderungen an Startseite:** Ermöglicht Benutzern das Ändern der Startseiten, die beim Öffnen von Microsoft Edge angezeigt werden. Nutzen Sie die Einstellung der Startseiten, um die Seite oder Liste von Seiten zu erstellen, die beim Starten von Microsoft Edge geöffnet werden.
-   **Zugriff auf about:flags-Seite blockieren:** Hindert den Benutzer am Zugriff auf die about:flags-Seite in Microsoft Edge, die Entwickler- und experimentelle Einstellungen enthält.
-   **WebRTC-LocalHost-IP-Adresse:** Blockiert die Anzeige der Localhost-IP-Adresse des Benutzers bei Anrufen über das Internet-RTC-Protokoll.
-   **Standardsuch-Engine:** Gibt die zu verwendende Standardsuch-Engine an. Endbenutzer können diesen Wert jederzeit ändern.
-   **Browserdaten beim Beenden löschen:** Löscht Verlauf und Browserdaten, wenn der Benutzer Microsoft Edge beendet.
-   **Datenerfassung für Livekacheln:** Beendet das Sammeln von Daten durch Windows aus den Livekacheln, wenn der Benutzer eine Seite an das Startmenü von Microsoft Edge anheften.
-  **Favoritenliste:** Definiert den Pfad zur Favoritendatei. Beispiel: http://contoso.com/favorites.html.
-  **Favoritenänderungen einschränken:** Legen Sie **Blockieren** fest, um zu verhindern, dass Benutzer die Favoritenliste hinzufügen, importieren, sortieren oder bearbeiten. 

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen

- **SmartScreen für Microsoft Edge**: Aktivieren Sie Edge SmartScreen für den Zugriff auf Website- und Dateidownloads.
- **Zugriff auf schädliche Websites**: Hindern Sie Benutzer daran, die Warnungen des Windows Defender SmartScreen-Filters zu ignorieren, und blockieren Sie sie, damit sie die Website nicht besuchen.
- **Download nicht überprüfter Dateien**: Hindern Sie Benutzer daran, die Warnungen des Windows Defender SmartScreen-Filters zu ignorieren, und blockieren Sie sie, damit sie nicht überprüfte Dateien herunterladen.

## <a name="search"></a>Suchen
- **SafeSearch (nur Mobilgeräte):** Steuert, wie Cortana nicht jugendfreie Inhalte in den Suchergebnissen filtert. Sie können **Streng** oder **Mittel** auswählen oder dem Endbenutzer ermöglichen, seine eigenen Einstellungen zu wählen.
- **Display web results in search** (Webergebnisse in der Suche anzeigen): Blockieren oder Zulassen, dass Webergebnisse für Suchvorgänge auf dem Gerät angezeigt werden.

## <a name="cloud-and-storage"></a>Cloud und Speicher
-   **Microsoft-Konto:** Erlaubt dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen.
-   **Nicht-Microsoft-Konto:** Erlaubt dem Benutzer, dem Gerät E-Mail-Konten hinzuzufügen, die nicht mit einem Microsoft-Konto verknüpft sind.
-   **Synchronisierung der Einstellungen für Microsoft-Konto:** Erlaubt das Synchronisieren der mit einem Microsoft-Konto verknüpften Geräte- und App-Einstellungen zwischen Geräten.

## <a name="cellular-and-connectivity"></a>Mobilfunk und Konnektivität

-   **Mobilfunkdatenkanal:** Verhindert, dass Benutzer Daten verbrauchen wie z.B. beim Browsen im Web, wenn sie mit einem Mobilfunknetz verbunden sind. 
-   **Datenroaming:** Erlaubt beim Zugriff auf Daten das Roaming zwischen Netzwerken.
-   **VPN über Mobilfunknetz:** Steuert, ob das Gerät auf VPN-Verbindungen zugreifen kann, wenn es mit einem Mobilfunknetz verbunden ist.
-   **VPN-Roaming über Mobilfunknetz:** Steuert, ob das Gerät beim Roaming in einem Mobilfunknetz auf VPN-Verbindungen zugreifen kann.
-   **Bluetooth:** Steuert, ob der Benutzer Bluetooth auf dem Gerät aktivieren und konfigurieren kann.
-   **Bluetooth-Erkennbarkeit:** Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte.
-   **Bluetooth-Vorabkopplung:** Ermöglicht das Konfigurieren spezifischer Bluetooth-Geräte für automatisches Koppeln mit einem Hostgerät.
-   **Bluetooth-Werbung:** Ermöglicht das Empfangen von Werbung per Bluetooth durch das Gerät.
-   **Dienst für verbundene Geräte:** Ermöglicht die Entscheidung, ob dem Dienst für verbundene Geräte die Ermittlung von und Verbindung mit anderen Bluetooth-Geräten erlaubt wird.
-   **NFC:** Erlaubt dem Benutzer das Aktivieren und Konfigurieren von Funktionen, die NFC (Near Field Communication, Nahfeldkommunikation) verwenden, auf dem Gerät.
-   **WLAN:** Erlaubt dem Benutzer das Aktivieren und Konfigurieren von WLAN auf dem Gerät (nur Windows 10 Mobile).
-   **Automatische Verbindung mit WLAN-Hotspots herstellen:** Ermöglicht automatische Verbindungen des Geräts mit unverschlüsselten WLAN-Hotspots und das automatische Akzeptieren der Geschäftsbedingungen für die Verbindung.
-   **Manuelle WLAN-Konfiguration:** Steuert, ob die Benutzer eigene WLAN-Verbindungen konfigurieren dürfen oder ob nur über WLAN-Profile konfigurierte Verbindungen verwendet werden dürfen (nur Windows 10 Mobile).
-   **Intervall für WLAN-Suche:** Gibt an, wie oft Geräte nach WLAN-Netzwerken suchen. Geben Sie einen Wert zwischen 1 (am häufigsten) und 500 (am seltensten) an.
-   **Zulässige Bluetooth-Dienste:** Gibt in Form von hexadezimalen Zeichenfolgen eine Liste zulässiger Bluetooth-Dienste und -Profile an.

## <a name="control-panel-and-settings"></a>Systemsteuerung und Einstellungen

-   **App „Einstellungen“:** Blockiert den Zugriff auf die Windows-Einstellungen-App.
    -   **System:** Blockiert den Zugriff auf den Systembereich der Einstellungen-App.
        -   **Änderung der Energie- und Energiesparmoduseinstellungen (nur Desktop):** Verhindert, dass der Endbenutzer Energie- und Energiesparmoduseinstellungen auf dem Gerät ändert.
    -   **Geräte:** Blockiert den Zugriff auf den Gerätebereich der Einstellungen-App.
    -   **Netzwerk und Internet:** Blockiert den Zugriff auf den Netzwerk- und Internet-Bereich der Einstellungen-App.
    -   **Personalisierung:** Blockiert den Zugriff auf den Personalisierungsbereich der Einstellungen-App.
    -   **Konten:** Blockiert den Zugriff auf den Kontenbereich der Einstellungen-App.
    -   **Zeit und Sprache:** Blockiert den Zugriff auf den Zeit- und Sprachenbereich der Einstellungen-App.
        -   **Änderung der Systemzeit:** Verhindert, dass der Endbenutzer auf dem Gerät Datum und Uhrzeit ändert.
        -   **Änderung von Regionseinstellungen (nur Desktop):** Verhindert, dass der Endbenutzer Regionseinstellungen auf dem Gerät ändert.
        -   **Änderung der Spracheinstellungen (nur Desktop):** Verhindert, dass der Benutzer Spracheinstellungen auf dem Gerät ändert.
    -   **Gaming**: Blockiert den Zugriff auf die Gaming-App in den Einstellungen.
    -   **Erleichterte Bedienung:** Blockiert den Zugriff auf den Bereich „Erleichterte Bedienung“ der Einstellungen-App.
    -   **Datenschutz:** Blockiert den Zugriff auf den Datenschutzbereich der Einstellungen-App.
    -   **Update und Sicherheit:** Blockiert den Zugriff auf den Update- und Sicherheitsbereich der Einstellungen-App.

## <a name="start"></a>Starten

- **Apps von der Taskleiste lösen:** Hindert den Benutzer daran, Apps vom Startmenü zu lösen.
- **Dokumente im Startmenü:** Blendet den Ordner „Dokumente“ im Windows-Startmenü aus oder ein.
- **Downloads im Startmenü:** Blendet den Ordner „Downloads“ im Windows-Startmenü aus oder ein.
- **Datei-Explorer im Startmenü:** Blendet die Datei-Explorer-App im Windows-Startmenü aus oder ein.
- **Heimnetzgruppe im Startmenü:** Blendet den Ordner „Heimnetzgruppe“ im Windows-Startmenü aus oder ein.
- **Musik im Startmenü:** Blendet den Ordner „Musik“ im Windows-Startmenü aus oder ein.
- **Netzwerk im Startmenü:** Blendet den Ordner „Netzwerk“ im Windows-Startmenü aus oder ein.
- **Persönlicher Ordner im Startmenü**: Blendet den persönlichen Ordner im Windows-Startmenü aus oder ein.
- **Bilder im Startmenü:** Blendet den Ordner für Bilder im Windows-Startmenü aus oder ein.
- **Einstellungen im Startmenü:** Blendet die Einstellungen-App im Windows-Startmenü aus oder ein.
- **Videos im Startmenü:** Blendet den Ordner für Videos im Windows-Startmenü aus oder ein.

## <a name="display"></a>Anzeige

- **GDI-Skalierung für Apps aktivieren**
- **GDI-Skalierung für Apps deaktivieren**

  Mit der GDI-DPI-Skalierung können Apps, die nicht mit DPI-Werten kompatibel sind, mit monitorspezifischen DPI-Werten kompatibel sein. Geben Sie die Legacy-Apps an, bei denen die GDI-DPI-Skalierung aktiviert ist. Wenn die GDI-DPI-Skalierung so konfiguriert ist, dass sie sowohl ein- als auch ausgeschaltet wird, wird die Skalierung für die App deaktiviert.

## <a name="kiosk-preview---obsolete"></a>Kiosk (Vorschauversion) (Veraltet)

Diese Einstellungen sind schreibgeschützt und können nicht verändert werden. Informationen zum Konfigurieren des Kioskmodus finden Sie unter [Kiosk settings in Windows 10 and later (Kioskeinstellungen für Windows 10 und höher)](kiosk-settings.md).

Ein Kiosk-Gerät führt in der Regel eine App oder eine bestimmte Gruppe von Apps aus. Benutzer werden daran gehindert, auf Features oder Funktionen auf dem Gerät außerhalb von Kiosk-Apps zuzugreifen.

- **Kioskmodus**: Ermittelt den Typ des Kioskmodus, der von der Richtlinie unterstützt wird. Zu den Optionen gehören:

  - **Nicht konfiguriert**: (Standard). Die Richtlinie aktiviert keinen Kioskmodus. 
  - **Kiosk mit einzelner App**: Das Profil erlaubt dem Gerät, nur eine App auszuführen. Wenn sich der Benutzer anmeldet, wird eine bestimmte App gestartet. Dieser Modus hindert den Benutzer auch daran, neue Apps zu öffnen oder die Apps, die ausgeführt wird, zu ändern.
  - **Kiosk mit mehreren Apps**: Das Profil erlaubt dem Gerät, mehrere Apps auszuführen. Es sind nur die Apps, die Sie hinzufügen, für den Benutzer verfügbar. Der Vorteil eines Kiosks mit mehreren Apps oder eines Geräts mit festem Zweck ist eine leicht verständliche Benutzererfahrung für einzelne Personen, da sie nur auf die Apps zugreifen, die sie benötigen, und die Apps entfernen, die sie nicht benötigen.

#### <a name="single-app-kiosks"></a>Kiosks für einzelne Apps
Legen Sie folgende Einstellungen fest:

- **Benutzerkonto:** Geben Sie das (auf das Gerät bezogene) lokale Benutzerkonto, das AD-Domänenkonto oder die Azure AD-Kontoanmeldeinformationen ein, das bzw. die der Kiosk-App zugeordnet ist.
  - Lokales Konto: wird als `devicename\accountname`, `.\accountname` oder `accountname` eingegeben
  - Domänenkonto: wird als `domain\accountname` eingegeben
  - Azure AD-Konto: wird als `AzureAD\emailaddress` eingegeben Stellen Sie sicher, dass Sie „AzureAD“ eingeben, da es sich dabei um einen festen Domänennamen handelt. Geben Sie anschließend die Azure AD-E-Mail-Adresse ein. Geben Sie beispielsweise `AzureAD\user@contoso.onmicrosoft.com` ein.

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Wenn Sie ein Azure AD-Konto für den Kioskmodus verwenden, geben Sie `AzureAD\user@yourorganization.com` ein.

- **Anwendungsbenutzermodell-ID (AUMID) der App**: Geben Sie die AUMID der Kiosk-App ein. Weitere Informationen finden Sie unter [Find the Application User Model ID of an installed app (Ermitteln der Anwendungsbenutzer-ID einer installierten App)](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

#### <a name="multi-app-kiosks"></a>Kiosks für mehrere Apps
[Kiosks für mehrere Apps](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) verwenden eine Kioskkonfiguration, mit der die zugelassenen Apps aufgelistet werden, sowie andere Einstellungen. 

Verwenden Sie die Schaltfläche **Hinzufügen**, um eine Kioskkonfiguration zu erstellen oder eine vorhandene auszuwählen. Legen Sie folgende Einstellungen fest:

- **Kioskkonfigurationsname**: Geben Sie einen Anzeigenamen an, der zur Identifikation einer bestimmten Konfiguration dient.

- **Kiosk-Apps**: Geben Sie die Apps ein, die im Startmenü verfügbar sein sollen. Die von Ihnen hinzugefügten Apps sind die einzigen Apps, die der Benutzer öffnen kann.

  - **App-Typ**: Wählen Sie den Typ der Kiosk-App aus:
    - **Win32-App**: Eine herkömmliche Desktop-App. Sie benötigen den vollqualifizierten Pfadnamen der ausführbaren Datei bezogen auf das Gerät.
    - **UWP-App**: Eine universelle Windows-App. Sie benötigen die [AUMID für die App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

  - **Bezeichner**: Geben Sie entweder den vollqualifizierten Pfadnamen für die ausführbare Datei (Win32-Apps) oder die [AUMID der App](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP-Apps) ein.

- **Taskleiste**: Wählen Sie aus, ob Sie die Taskleiste **aktivieren** (anzeigen) oder sie im Kioskmodus **nicht konfiguriert** (ausgeblendet) lassen möchten.

- **Layout des Startmenüs**: Geben Sie eine XML-Datei ein, die beschreibt, wie die Apps im Startmenü dargestellt werden. [Anpassen und Exportieren des Startlayouts](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout): bietet Anweisungen und XML-Beispiele.


  [Erstellen eines Windows 10-Kiosks, in dem mehrere Apps ausgeführt werden](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file): bietet weitere Details zur Verwendung und Erstellung von XML-Dateien.

- **Zugewiesene Benutzer**: Fügen Sie mindestens ein Benutzerkonto hinzu, das die von Ihnen hinzugefügten Apps verwenden kann. Wenn sich ein Benutzer mit einem Konto anmeldet, sind nur die in der Konfiguration definierten Apps verfügbar. Das Konto ist entweder für das Gerät lokal oder stellt eine Azure AD-Kontoanmeldung dar, die der Kiosk-App zugeordnet ist.

    Für Kiosks in öffentlichen Umgebungen, für die die automatische Anmeldung aktiviert ist, muss ein Benutzertyp mit den geringsten Berechtigungen (z.B. das lokale Standardbenutzerkonto) verwendet werden. Verwenden Sie das `domain\user@tenant.com`-Format, um ein Azure Active Directory-Konto (AD) für den Kioskmodus zu konfigurieren.

## <a name="windows-defender-antivirus"></a>Windows Defender Antivirus

-   **Echtzeitüberwachung:** Aktiviert die Echtzeitüberwachung auf Schadsoftware, Spyware und andere unerwünschte Software.
-   **Verhaltensüberwachung:** Ermöglicht Defender, Geräte auf bestimmte bekannte Muster verdächtiger Aktivitäten zu überprüfen.
-   **Netzwerkinspektionssystem (NIS):** NIS trägt zum Schutz von Geräten vor netzwerkbasierten Exploits bei. Es verwendet die Signaturen bekannter Sicherheitsrisiken aus dem Microsoft Endpoint Protection Center, um schädlichen Datenverkehr zu erkennen und zu blockieren.
-   **Alle Downloads überprüfen:** Steuert, ob Defender alle aus dem Internet heruntergeladenen Dateien überprüft.
-   **In Microsoft-Webbrowsern geladene Skripts überprüfen:** Ermöglicht Defender die Überprüfung von Skripts, die in Internet Explorer verwendet werden.
-   **Endbenutzerzugriff auf Defender:** Steuert, ob die Benutzeroberfläche von Windows Defender für Endbenutzer ausgeblendet ist.
Wenn diese Einstellung geändert wird, wird die Änderung wirksam, wenn der Endbenutzer-PC das nächste Mal neu gestartet wird.
-   **Intervall für Signaturaktualisierung (in Stunden):** Gibt das Intervall an, in dem Defender auf neue Signaturdateien prüft.
-   **Datei- und Programmaktivität überwachen:** Ermöglicht Defender die Überwachung der Datei- und Programmaktivität auf Geräten.
-   **Tage bis zum Löschen von in Quarantäne befindlicher Schadsoftware:** Ermöglicht Defender die fortgesetzte Nachverfolgung behandelter Schadsoftware für die angegebene Anzahl von Tagen, damit Sie zuvor betroffene Geräte manuell überprüfen können. Wenn Sie die Anzahl von Tagen auf **0** festlegen, bleibt Schadsoftware im Quarantäneordner und wird nicht automatisch entfernt.
-   **CPU-Nutzungslimit während einer Überprüfung:** Ermöglicht die Begrenzung der CPU-Nutzung, die bei Überprüfungen genutzt werden darf (von **1** bis **100**).
-   **Archivdateien überprüfen:** Ermöglicht Defender die Überprüfung von Archivdateien wie ZIP- oder CAB-Dateien.
-   **Eingehende E-Mail überprüfen:** Ermöglicht Defender das Überprüfen von E-Mail-Nachrichten beim Eingang auf dem Gerät.
-   **Bei einer vollständigen Überprüfung Wechseldatenträger überprüfen:** Ermöglicht Defender das Überprüfen von Wechseldatenträgern wie USB-Sticks.
-   **Bei einer vollständigen Überprüfung zugeordnete Netzlaufwerke überprüfen:** Ermöglicht Defender das Überprüfen von Dateien auf zugeordneten Netzwerklaufwerken.<br>Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.
-   **Über Netzwerkordner geöffnete Dateien überprüfen:** Ermöglicht Defender das Überprüfen von Dateien auf freigegebenen Netzlaufwerken (z.B. Dateien, auf die über einen UNC-Pfad zugegriffen wird).
Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.
-   **Cloudschutz:** Erlaubt oder sperrt den Empfang von Informationen über Schadsoftwareaktivitäten der von Ihnen verwalteten Geräten durch den Microsoft Active Protection Service. Diese Informationen werden verwendet, um den Dienst in der Zukunft zu verbessern.
-   **Vor dem Senden von Beispielen bei Benutzern nachfragen:** Steuert, ob potenziell schädliche Dateien, die möglicherweise genauer analysiert werden müssen, automatisch an Microsoft gesendet werden.
-   **Uhrzeit für die Durchführung einer täglichen Schnellüberprüfung:** Ermöglicht Ihnen die Planung einer Schnellüberprüfung, die täglich zum ausgewählten Zeitpunkt erfolgt.
-   **Art der durchzuführenden Systemüberprüfung:** Ermöglicht die Angabe der Überprüfungsebene für eine geplante Systemüberprüfung.
-   **Möglicherweise unerwünschte Software erkennen:** Ermöglicht die Auswahl einer der folgenden Schutzebenen, wenn Windows potenziell unerwünschte Software erkennt:
        - **Blockieren**
        - **Überprüfen** Weitere Informationen zu potenziell unerwünschten Apps finden Sie in [diesem Thema](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus).
-   **Aktionen für erkannte Schadsoftwarebedrohungen:** Aktivieren Sie diese Option, um die Maßnahmen zu bestimmen, die Defender bei den einzelnen erkannten Bedrohungsstufen (Niedrig, Mittel, Hoch und Schwerwiegend) ergreifen soll. Sie können folgende Maßnahmen ergreifen:
    -   **Bereinigen**
    -   **Quarantäne**
    -   **Entfernen**
    -   **Zulassen**
    -   **Benutzerdefiniert**
    -   **Blockieren**

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender Antivirus-Ausschlüsse

-   **Dateien und Ordner, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen:** Fügt Dateien und Ordner wie **C:\Pfad** oder **%ProgramFiles%\Pfad\Dateiname.exe** der Ausschlussliste hinzu. Diese Dateien und Ordner werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
-   **Dateierweiterungen, die bei Überprüfungen und Echtzeitschutz ausgeschlossen werden sollen:** Fügt der Ausschlussliste eine oder mehrere Erweiterungen wie **jpg** oder **txt** hinzu. Dateien mit diesen Erweiterungen werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.
-   **Prozesse, die von Überprüfungen und Echtzeitschutz ausgenommen werden sollen:** Fügt der Ausschlussliste einen oder mehrere Prozesse vom Typ **.exe**, **.com** oder **.scr** hinzu. Diese Prozesse werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.

## <a name="network-proxy"></a>Netzwerkproxy

-   **Proxyeinstellungen automatisch ermitteln:** Bei Aktivierung versucht das Gerät, den Pfad zu einem PAC-Skript zu finden.
-   **Proxyskript verwenden:** Wählen Sie diese Option, um einen Pfad zu einem PAC-Skript zum Konfigurieren des Proxyservers anzugeben.
    -   **Adress-URL für Setupskript:** Geben Sie die URL eines PAC-Skripts an, das Sie verwenden möchten, um den Proxyserver zu konfigurieren.
-   **Manuellen Proxyserver verwenden:** Wählen Sie diese Option, wenn Sie manuell Proxyserverinformationen angeben möchten.
    -   **Adresse**: Geben Sie den Namen oder die IP-Adresse des Proxyservers an.
    -   **Portnummer:** Geben Sie die Portnummer Ihres Proxyservers ein.
    -   **Proxyausnahmen:** Geben Sie URLs an, die den Proxyserver nicht verwenden dürfen. Trennen Sie die einzelnen Elemente durch Semikola.
    -   **Proxyserver für lokale Adresse umgehen**: Aktivieren Sie diese Option, wenn Sie den Proxyserver nicht für lokale Adressen in Ihrem Intranet verwenden möchten.

## <a name="windows-spotlight"></a>Windows-Blickpunkt

- **Windows-Blickpunkt:** Verwenden Sie diese Einstellung, um auf Windows 10-Geräten alle Funktionen von Windows-Blickpunkt zu blockieren. Wenn Sie diese Einstellung blockieren, sind die folgenden Einstellungen nicht verfügbar.
    - **Windows-Blickpunkt auf dem Sperrbildschirm:** Verhindert, dass Windows-Blickpunkt Informationen auf dem Gerätesperrbildschirm anzeigt.
    - **Drittanbietervorschläge in Windows-Blickpunkt:** Verhindert, dass Windows-Blickpunkt Inhalte vorschlägt, die nicht von Microsoft stammen.
    - **Endbenutzerfeatures:** Blockiert Endbenutzerfeatures wie Startmenüvorschläge und Mitgliedschaftsbenachrichtigungen.
    - **Windows-Tipps:** Blockiert die Anzeige von Popuptipps in Windows.
    - **Windows-Blickpunkt im Info-Center:** Verhindert, dass Vorschläge von Windows-Blickpunkt wie neue Apps oder Sicherheitsinhalte im Windows-Info-Center angezeigt werden.
    - **Personalisierung von Windows-Blickpunkt:** Verhindert, dass Windows-Blickpunkt Ergebnisse basierend auf der Nutzung eines Geräts personalisiert.
    - **Windows-Begrüßungsseite:** Blockiert die Windows-Begrüßungsseite, die dem Benutzer Informationen zu neuen oder aktualisierten Funktionen anzeigt.

## <a name="projection"></a>Projektion

- **Benutzereingabe über Empfänger der drahtlosen Anzeige:** Blockiert Benutzereingaben über Empfänger der drahtlosen Anzeige.
- **Projektion auf diesem PC:** Verhindert, dass andere Geräte den PC für die Projektion erkennen.
- **PIN für Kopplung erforderlich:** Erfordert eine PIN beim Herstellen der Verbindung mit einem Projektionsgerät.

## <a name="cloud-printer"></a>Clouddrucker

- **URL für Druckerermittlung**: Endpunkt für die Erkennung von Clouddruckern
- **Autoritäts-URL für Druckerzugriff**: Authentifizierungsendpunkt für den Abruf von OAuth-Token
- **GUID für native Azure-Client-App**: Eine GUID einer Clientanwendung, die zum Abrufen von OAuth-Token von der OAuthAuthority berechtigt ist
- **Druckdienstressourcen-URI**: OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckdienst
- **Maximal abgefragte Drucker (nur Mobile)**: Maximale Anzahl von Druckern, die von einem Ermittlungsendpunkt abgefragt werden sollen
- **Ressourcen-URI für Druckerermittlungsdienst**: OAuth-Ressourcen-URI für den im Azure-Portal konfigurierten Druckererkennungsdienst

## <a name="local-printer"></a>Lokaler Drucker
- **Drucker**: Liste der lokalen Drucker, die hinzugefügt wurden.
- **Standarddrucker**: Festlegen als Standarddrucker.
- **Benutzerzugriff für das Hinzufügen neuer Drucker**: Zulassen oder Blockieren der Verwendung von lokalen Druckern.

## <a name="reporting-and-telemetry"></a>Berichterstellung und Telemetrie

- **Nutzungsdaten freigeben**: Wählen Sie die Ebene der Diagnosedatenübermittlung.
- **Telemetrieproxyserver**

  Geben Sie den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) oder die IP-Adresse eines Proxyservers an, um Anforderungen zu Benutzererfahrung und Telemetrie im verbundenen Modus über eine SSL-Verbindung (Secure Sockets Layer) weiterzuleiten. Das Format dieser Einstellung lautet *Server*:*Port*. Wenn beim benannten Proxy ein Fehler auftritt oder kein Proxy angegeben wurde, obwohl diese Richtlinie aktiviert ist, werden die Daten zu Benutzererfahrung und Telemetrie im verbundenen Modus nicht übertragen und verbleiben auf dem lokalen Gerät.

   Beispiele für das Format:

   IPv4: 192.246.246.106:100<br>
 IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100<br> FQDN: www.contoso.com:345

## <a name="messaging"></a>Messaging

- **Nachrichtensynchronisierung (nur mobil)**: Deaktivieren Sie das Feature „Nachrichten – Überall“ sowie die SMS-Sicherung und -Wiederherstellung.
- **MMS (nur mobil)**: Deaktivieren Sie die Funktion zum Senden/Empfangen von MMS auf dem Gerät.
- **RCS (nur mobil)**: Deaktivieren Sie die Funktion für RCS-Sendevorgänge/Empfangsvorgänge (Rich Communication Services) auf dem Gerät.
