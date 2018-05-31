---
title: Einstellungen für Windows 10-Richtlinien
description: Verwenden Sie die in diesem Thema aufgeführten Richtlinieneinstellungen, um integrierte und benutzerdefinierte Einstellungen für registrierte Windows 10 Desktop- und Windows 10-Mobilgeräte zu konfigurieren.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 202f15766aa740755669ab246739a5331ea328a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31027645"
---
# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Intune-Richtlinieneinstellungen für Windows 10-Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Dieses Thema enthält Informationen zum Verständnis der Intune-Richtlinieneinstellungen, die Sie zum Verwalten von Windows 10-Geräten verwenden können. Lesen Sie dieses Thema neben den Vorgehensweisen unter [Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Zwei Richtlinientypen stehen zur Verfügung:

- **Benutzerdefinierte Richtlinie**: Stellen Sie mithilfe der **benutzerdefinierten Richtlinie** von Microsoft Intune für Windows 10 und Windows 10 Mobile Einstellungen für OMA-URI (Open Mobile Alliance Uniform Resource Identifier) bereit, um Features auf Geräten zu steuern. Windows 10 stellt viele CSP-Einstellungen zur Verfügung, z. B. den [Richtlinienkonfigurationsdienst-Anbieter (Policy Configuration Service Provider; Policy CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Allgemeine Konfigurationsrichtlinie**: Verwenden Sie diesen Richtlinientyp, wenn Sie Einstellungen aus der integrierten Liste auswählen möchten, die in Microsoft Intune enthalten ist.

## <a name="custom-policy-settings"></a>Benutzerdefinierte Richtlinieneinstellungen

Geben Sie die folgenden Einstellungen in einer benutzerdefinierten Richtlinie an.

### <a name="general-settings"></a>Allgemeine Einstellungen

Geben Sie einen Namen und eine optionale Beschreibung für diese Richtlinie ein, damit Sie sie in der Intune-Konsole besser identifizieren können.

### <a name="oma-uri-settings"></a>OMA-URI-Einstellungen

Geben Sie für jede OMA-URI-Einstellung, die Sie hinzufügen möchten, die folgenden Informationen ein:

- **Einstellungsname**: Geben Sie einen eindeutigen Namen für die OMA-URI-Einstellung ein, damit Sie sie in der Liste der Einstellungen leichter identifizieren können. Weitere Informationen zu URI-Einstellungen finden Sie unter [Einführung in Konfigurationsdienstanbieter (Configuration Service Providers, CSPs) für IT-Experten](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Beschreibung der Einstellung**: Geben Sie optional eine Beschreibung für die Einstellung ein.
- **Datentyp**: Wählen Sie aus den folgenden Datentypen aus:
    - **Zeichenfolge**
    - **Zeichenfolge (XML)**
    - **Datum und Uhrzeit**
    - **Ganze Zahl**
    - **Gleitkomma**
    - **Boolesch**
- **OMA-URI (Groß-/Kleinschreibung beachten)**: Geben Sie den OMA-URI an, für den Sie eine Einstellung festlegen möchten.
- **Wert**: Geben Sie den Wert an, der mit der von Ihnen eingegebenen OMA-URI verknüpft werden soll.

### <a name="example"></a>Beispiel
Im folgenden Screenshot ist die Einstellung **Connectivity/AllowVPNOverCellular** aktiviert. Dadurch kann ein Windows 10-Gerät eine VPN-Verbindung über ein Mobilfunknetz öffnen.

> ![Beispiel für eine benutzerdefinierte Richtlinie mit VPN-Einstellungen](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>Suchen konfigurierbarer Richtlinien

Eine vollständige Liste aller Konfigurationsdienstanbieter (CSP), die von Windows 10 unterstützt werden, finden Sie in der [Konfigurationsdienstanbieter-Referenz](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) in der Windows-Dokumentationsbibliothek.

Nicht alle Einstellungen sind mit allen Windows 10-Versionen kompatibel. Die Tabelle im Windows-Abschnitt enthält entsprechende Informationen, welche Versionen für die einzelnen Konfigurationsdienstanbieter unterstützt werden.

Darüber hinaus unterstützt Intune nicht alle Einstellungen, die in diesem Abschnitt aufgeführt werden. Öffnen Sie den Abschnitt für die jeweilige Einstellung, um herauszufinden, ob die gewünschte Einstellung von Intune unterstützt wird. Jede Einstellungsseite zeigt ihren unterstützten Vorgang an. Damit die Einstellung mit Intune funktioniert, muss sie die Vorgänge **Hinzufügen** oder **Ersetzen** unterstützen.

## <a name="general-configuration-policy-settings"></a>Allgemeine Konfigurationsrichtlinieneinstellungen

Verwenden Sie die **allgemeine Microsoft Intune-Konfigurationsrichtlinie** für Windows 10, um integrierte Einstellungen für registrierte Windows 10 Desktop- und Windows 10 Mobile-Geräte zu konfigurieren.

### <a name="password"></a>Kennwort

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|
|**Anfordern eines Kennworts zum Entsperren von Geräten**|-|
|**Erforderlicher Kennworttyp**|Gibt an, ob das Kennwort alphanumerisch sein muss oder nur numerisch.|
|**Erforderlicher Kennworttyp** - **Minimale Anzahl von Zeichensätzen**| Gibt an, wie viele der verschiedenen Zeichen (Kleinbuchstaben, Großbuchstaben, Zahlen und Symbole) im Kennwort enthalten sein müssen.|
|**Minimale Kennwortlänge**|Gilt nur für Windows 10 Mobile|
|**Anzahl zulässiger wiederholter Anmeldefehler, bevor das Gerät zurückgesetzt wird**.|Für Geräte mit Microsoft 10: Wenn auf dem Gerät BitLocker aktiviert ist, wird in den BitLocker-Wiederherstellungsmodus gewechselt, sobald die Anzahl der von Ihnen angegebenen Anmeldeversuche fehlgeschlagen ist. Wenn BitLocker nicht für dieses Gerät aktiviert ist, wird diese Einstellung nicht angewendet.<br>Für Geräte mit Windows 10 Mobile: Das Gerät wird zurückgesetzt, sobald die Anzahl der von Ihnen angegebenen Anmeldeversuche fehlgeschlagen ist.|
|**Minuten der Inaktivität, bevor der Bildschirm ausgeschaltet wird**|Gibt den Zeitraum an, für den sich das Gerät im Leerlauf befinden muss, bevor der Bildschirm gesperrt wird.|
|**Kennwortablauf (Tage)**|Gibt die Zeitspanne an, nach der das Kennwort für das Gerät geändert werden muss.|
|**Kennwortverlauf speichern**|Gibt an, ob Sie verhindern möchten, dass der Benutzer zuvor verwendete Kennwörter erstellt.|
|**Kennwortverlauf speichern** - **Wiederverwendung vorheriger Kennwörter verhindern**|Gibt an, wie viele zuvor verwendete Kennwörter vom Gerät gespeichert werden.|
|**Kennwort anfordern, wenn das Gerät aus dem Leerlauf zurückkehrt**|Gibt an, dass der Benutzer ein Kennwort zum Entsperren des Geräts eingeben muss (nur Windows 10 Mobile).|

### <a name="encryption"></a>Verschlüsselung

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|
|**Verschlüsselung auf mobilem Gerät anfordern**|Ermöglicht die Verschlüsselung auf Zielgeräten.<br>(Nur Windows 10 Mobile)|

### <a name="system"></a>System

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|
|**Bildschirmaufnahme zulassen**|Ermöglicht dem Benutzer, den Bildschirm des Geräts als Bild zu erfassen (nur Windows 10 Mobile)|
|**Manuelles Aufheben der Registrierung zulassen**|Ermöglicht dem Benutzer das manuelle Löschen des Unternehmensbereichskontos vom Gerät|
|**Manuelle Installation des Stammzertifikats zulassen**|Betrifft Windows 10 Mobile|
|**Senden von Diagnose- und Verwendungsdaten an Microsoft zulassen**|Folgende Werte sind möglich:<br><br>**Nein**: Keine Daten werden an Microsoft gesendet.<br>**Einfach** – begrenzte Informationen werden an Microsoft gesendet<br>**Erweitert** – Erweiterte Diagnosen werden an Microsoft gesendet<br>**Vollständig (empfohlen)**: Das Gerät sendet die gleichen Daten wie mit **Erweitert** sowie zusätzliche Daten über den Gerätezustand.|


### <a name="account-and-synchronization"></a>Konto und Synchronisierung

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|---------------------|
|**Microsoft-Konto zulassen**|Ermöglicht dem Benutzer, das Gerät einem Microsoft-Konto zuzuordnen|
|**Manuelles Hinzufügen von Nicht-Microsoft-Konten zulassen**|Ermöglicht dem Benutzer, dem Gerät E-Mail-Konten hinzuzufügen, die nicht mit einem Microsoft-Konto verknüpft sind|
|**Synchronisierung von Einstellungen für Microsoft-Konten zulassen**|Ermöglicht das Synchronisieren der mit einem Microsoft-Konto verknüpften Geräte- und App-Einstellungen zwischen Geräten|

### <a name="microsoft-edge"></a>Microsoft Edge

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|
|**Webbrowser zulassen**|Ermöglicht die Verwendung des Microsoft Edge-Webbrowsers auf dem Gerät.<br>(Nur Windows 10 Mobile)|
|**Suchvorschläge auf der Adressleiste zulassen**|Ermöglicht dem Suchmodul, Websites während der Eingabe von Suchausdrücken vorzuschlagen.|
|**Senden von Intranetdatenverkehr an Internet Explorer zulassen**|Ermöglicht Benutzern, Intranetsites in Internet Explorer zu öffnen.<br>(Nur Windows 10 Desktop)|
|**Nicht verfolgen (Do not track) zulassen**|Konfiguriert den Microsoft Edge-Browser zum Senden von DNT-Headern (Do Not Track, nicht nachverfolgen) an Websites, die Benutzer besuchen.|
|**SmartScreen aktivieren**||
|**Active Scripting zulassen**|Lässt die Ausführung von Skripts wie z.B. JavaScript im Microsoft Edge-Browser zu|
|**Popups zulassen**|Gilt nur für Windows 10 Desktop|
|**Cookies zulassen**||
|**AutoAusfüllen zulassen**|Ermöglicht Benutzern, die Einstellungen für AutoVervollständigen im Browser zu ändern.<br>(Nur Windows 10 Desktop)|
|**Kennwort-Manager zulassen**|Aktiviert oder deaktiviert den Microsoft Edge-Kennwort-Manager.|
|**Ort der Standortliste für Enterprise-Modus**|Gibt an, wo Sie die Liste der Websites finden, die im Unternehmensmodus geöffnet werden. Benutzer können diese Liste nicht bearbeiten.<br>(Nur Windows 10 Desktop)|

### <a name="apps"></a>Apps

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|---------------------|
|**Anwendungsspeicher zulassen**|Gilt nur für Windows 10 Mobile|



### <a name="cellular"></a>Mobilfunk

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|---------------------|
|**Datenroaming zulassen**|Ermöglicht beim Zugriff auf Daten das Roaming zwischen Netzwerken|
|**VPN über Mobilfunk zulassen**|Steuert, ob das Gerät auf VPN-Verbindungen zugreifen kann, wenn es mit einem Mobilfunknetz verbunden ist|
|**VPN-Roaming über Mobilfunk zulassen**|Steuert, ob das Gerät beim Roaming in einem Mobilfunknetz auf VPN-Verbindungen zugreifen kann|

### <a name="hardware"></a>Hardware

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|
|**Kamera zulassen**|-|
|**Wechselspeichermedien zulassen**|Gibt an, ob externe Speichergeräte wie SD-Karten mit dem Gerät verwendet werden können|
|**WLAN zulassen**|Gilt nur für Windows 10 Mobile|
|**Internetfreigabe zulassen**|Ermöglicht die gemeinsame Nutzung der Internetverbindung auf dem Gerät.|
|**Manuelle WLAN-Konfiguration zulassen**|Steuert, ob die Benutzer eigene WLAN-Verbindungen konfigurieren dürfen oder ob nur über WLAN-Profile konfigurierte Verbindungen verwendet werden dürfen<br>(Nur Windows 10 Mobile)|
|**Automatische Verbindung mit freien WLAN-Hotspots zulassen**|Ermöglicht automatische Verbindungen des Geräts mit unverschlüsselten WLAN-Hotspots und das automatische Akzeptieren der Geschäftsbedingungen für die Verbindung|
|**Geolocation zulassen**|Gibt an, ob das Gerät Ortungsdienstinformationen verwenden kann|
|**NFC zulassen**|Ermöglicht die Verwendung von NFC-Funktionen (Near Field Communications) auf dem Gerät|
|**Bluetooth zulassen**|-|
|**Sichtbaren Modus für Bluetooth zulassen**|Ermöglicht die Erkennung dieses Geräts durch andere Bluetooth-Geräte|
|**Bluetooth-Werbung zulassen**|Ermöglicht Geräten dem Empfang von Werbung über Bluetooth|
|**Handyzurücksetzung zulassen**|Steuert, ob Benutzer ihre Geräte auf Werkseinstellungen zurücksetzen können.|
|**USB-Verbindung zulassen**|Steuert, ob die Geräte über eine USB-Verbindung auf externe Speichergeräte zugreifen können|
|**Diebstahlschutzmodus zulassen**|Konfiguriert, ob der Windows-Diebstahlschutzmodus aktiviert ist.|

### <a name="features"></a>Features

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|---------------------|
|**Kopieren und Einfügen zulassen**|Gilt nur für Windows 10 Mobile|
|**Sprachaufzeichnung zulassen**|Gilt nur für Windows 10 Mobile|
|**Cortana zulassen**|Aktivieren oder deaktivieren des Cortana-Sprach-Assistenten|
|**Info-Center-Benachrichtigungen zulassen**|Aktivieren oder deaktivieren von Wartungscenterbenachrichtigungen auf dem Gerätesperrbildschirm<br>(Nur Windows 10 Mobile)|

### <a name="windows-defender"></a>Windows Defender

Alle Einstellungen gelten für nur Windows 10 Desktop.

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|----------------------|---------------------|
|**Echtzeitüberwachung zulassen**|Ermöglicht die Echtzeitüberwachung auf Schadsoftware, Spyware und andere unerwünschte Software.|
|**Verhaltensüberwachung zulassen**|Ermöglicht Defender, Geräte auf bestimmte bekannte Muster verdächtiger Aktivitäten zu überprüfen.|
|**Netzwerkinspektionssystem aktivieren**|Das Netzwerkinspektionssystem (NIS) trägt zum Schutz von Geräten vor netzwerkbasierten Sicherheitslücken bei, indem die Signaturen bekannter Sicherheitsrisiken aus dem Endpoint Protection-Center von Microsoft verwendet werden, um schädlichen Datenverkehr zu erkennen und zu blockieren.|
|**Alle Downloads überprüfen**|Steuert, ob Defender alle aus dem Internet heruntergeladenen Dateien überprüft.|
|**Skriptüberprüfung zulassen**|Ermöglicht Defender die Überprüfung von Skripts, die in Internet Explorer verwendet werden.|
|**Datei- und Programmaktivität überwachen**|Ermöglicht Defender die Überwachung der Datei- und Programmaktivität auf Geräten.|
|**Tage für Nachverfolgung behandelter Schadsoftware**|Ermöglicht Defender die fortgesetzte Nachverfolgung behandelter Schadsoftware für die angegebene Anzahl von Tagen, damit Sie zuvor betroffene Geräte manuell überprüfen können. Wenn Sie die Anzahl von Tagen auf **0** festlegen, bleibt Schadsoftware im Quarantäneordner und wird nicht automatisch entfernt. |
|**Zugriff auf die Clientbenutzeroberfläche zulassen**|Steuert, ob die Benutzeroberfläche von Windows Defender für Benutzer ausgeblendet ist.<br>Wenn diese Einstellung geändert wird, wird die Änderung wirksam, wenn der Endbenutzer-PC das nächste Mal neu gestartet wird.|
|**Tägliche Schnellüberprüfung planen**|Ermöglicht Ihnen die Planung einer Schnellüberprüfung, die täglich zum ausgewählten Zeitpunkt erfolgt.|
|**Systemüberprüfung planen**|Ermöglicht Ihnen, eine vollständige Überprüfung oder eine Schnellüberprüfung des Systems zu planen, die regelmäßig am ausgewählten Tag und zur ausgewählten Zeit ausgeführt wird.|
|**CPU-Auslastung während einer Überprüfung begrenzen**|Ermöglicht die Begrenzung des Umfangs an CPU, der bei Überprüfungen genutzt werden darf (von **1** bis **100**).|
|**Archivdateien überprüfen**|Ermöglicht Defender die Überprüfung von Archivdateien wie ZIP- oder CAB-Dateien.|
|**E-Mail-Nachrichten überprüfen**|Ermöglicht Defender das Überprüfen von E-Mail-Nachrichten beim Eingang auf dem Gerät.|
|**Wechseldatenträger überprüfen**|Ermöglicht Defender das Überprüfen von Wechseldatenträgern wie USB-Sticks.|
|**Zugeordnete Netzwerklaufwerke überprüfen**|Ermöglicht Defender das Überprüfen von Dateien auf zugeordneten Netzwerklaufwerken.<br>Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender eventuell gefundene Schadsoftware nicht entfernen.|
|**Dateien überprüfen, die in freigegebenen Netzwerkordnern geöffnet wurden**|Ermöglicht Defender das Überprüfen von Dateien auf freigegebenen Netzlaufwerken (z.B. solche, auf die über einen UNC-Pfad zugegriffen wird).<br>Wenn die Dateien auf dem Laufwerk schreibgeschützt sind, kann Defender gefundene Schadsoftware nicht entfernen.|
|**Intervall zum Aktualisieren von Signaturen**|Gibt das Intervall an, in dem Defender auf neue Signaturdateien prüft.|
|**Cloudschutz zulassen**|Lässt zu oder verhindert, dass Microsoft Active Protection Service Informationen über Schadsoftwareaktivitäten von den von Ihnen verwalteten Geräten erhält. Diese Informationen werden verwendet, um den Dienst in der Zukunft zu verbessern.|
|**Beim Senden von Beispielen beim Benutzer nachfragen**|Steuert, ob die Dateien automatisch an Microsoft gesendet werden, die möglicherweise von Microsoft genauer analysiert werden müssen, um festzustellen, ob sie schädlich sind.|
|**Erkennung möglicherweise unerwünschter Anwendungen**|Schützt registrierte Windows-Desktopgeräte gegen die Ausführung von Software, die von Windows Defender als möglicherweise unerwünscht eingestuft wird. Sie können verhindern, dass diese Anwendungen ausgeführt werden, oder den Überwachungsmodus verwenden, um zu melden, wenn eine möglicherweise unerwünschte Anwendung installiert wird.|
|**Von der Überprüfung oder dem Echtzeitschutz auszuschließende Dateien und Ordner**|Fügt Dateien und Ordner wie **C:\Pfad** oder **%ProgramFiles%\Pfad\Dateiname.exe** der Ausschlussliste hinzu. Diese Dateien und Ordner werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.|
|**Dateierweiterungen, die beim Ausführen einer Überprüfung oder bei Verwendung des Echtzeitschutzes auszuschließen sind**|Fügen Sie Dateierweiterungen wie **JPG** oder **TXT** der Ausschlussliste hinzu. Dateien mit diesen Erweiterungen werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.|
|**Prozesse, die beim Ausführen einer Überprüfung oder bei Verwendung des Echtzeitschutzes auszuschließen sind**|Fügt Prozesse des Typs **.exe**, **.com** oder **.scr** der Ausschlussliste hinzu. Diese Prozesse werden nicht in Echtzeitüberprüfungen oder geplante Überprüfungen einbezogen.|


### <a name="updates"></a>Updates

|Name der Einstellung|Erforderliche zusätzliche Informationen (wo erforderlich)|
|----------------|---------------|
|**Automatische Updates zulassen**|Lässt automatische Updates zu. Konfigurieren Sie eine der folgenden Einstellungen, um das Updateverhalten zu steuern:<br />**Download benachrichtigen**<br />**Automatische Installation während der Wartung**<br />**Automatische Installation und Neustart während der Wartung**<br />**Zur festgelegten Zeit automatisch installieren und neu starten**: Beachten Sie, wenn diese Option ausgewählt ist, können Sie auch die folgenden Einstellungen konfigurieren: **Benachrichtigung für Endbenutzer unterdrücken** und **Installationstag für geplante Updates definieren**.<br>(Nur Windows 10 Desktop)|
|**Features der Vorabversion zulassen**|Bietet Microsoft die Möglichkeit, Einstellungen und Features der Vorabversion für Windows 10-Geräte bereitzustellen. Sie können auswählen, ob nur Einstellungen oder alle Einstellungen und Features der Vorabversion installiert werden sollen.|

### <a name="see-also"></a>Siehe auch
[Verwalten von Einstellungen und Features auf Ihren Geräten mit Microsoft Intune-Richtlinien](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
