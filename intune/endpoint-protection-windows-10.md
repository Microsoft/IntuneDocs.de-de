---
title: "Einstellungen von Microsoft Intune Endpoint Protection für Windows 10"
titlesuffix: 
description: "In diesem Artikel erfahren Sie mehr zu den Intune-Einstellungen zur Steuerung von Endpoint Protection wie z.B. BitLocker auf Windows 10-Geräten."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02a32f678b40b2b40535984e17b41e0a864d8fdf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="create-endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Erstellen von Endpoint Protection-Einstellungen für Windows 10 und höher in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Mit dem Endpoint Protection-Profil können Sie Sicherheitsfeatures auf Windows 10-Geräten steuern, z.B. BitLocker und Windows Defender.

In diesem Artikel erfahren Sie, wie Sie Endpoint Protection-Profile erstellen können.

> [!Note]
> Diese Einstellungen werden nicht auf der Home Edition und auf der Professional Edition von Windows 10 unterstützt.

## <a name="create-an-endpoint-protection-profile"></a>Erstellen eines Endpoint Protection-Profils

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
3. Wählen Sie auf dem Blatt **Intune** die Option **Gerätekonfiguration** aus.
2. Klicken Sie auf dem Blatt **Gerätekonfiguration** im Abschnitt **Verwalten** auf **Profile**.
3. Klicken Sie auf dem Blatt „Profile“ auf **Profil erstellen**.
4. Geben Sie auf dem Blatt **Profil erstellen** einen **Namen** und eine **Beschreibung** für das Gerätefunktionsprofil ein.
5. Wählen Sie in der Dropdownliste **Plattform** die Option **Windows 10 und höher** aus.
6. Wählen Sie in der Dropdownliste **Profiltyp** die Option **Endpoint Protection** aus.
7. Konfigurieren Sie die gewünschten Einstellungen. Die Angaben in diesem Artikel helfen Ihnen dabei, zu verstehen, was die Auswirkungen jeder Einstellung sind. Wenn Sie fertig sind, wählen Sie **OK** aus.
8. Wechseln Sie zurück zum Blatt **Profil erstellen**, und klicken Sie auf **Erstellen**.

Das Profil wird erstellt und auf dem Blatt mit der Profilliste angezeigt.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Application Guard ist nur für Windows 10-Geräte (64-Bit) verfügbar. Mithilfe von diesem Profil wird eine Win32-Komponente zur Aktivierung von Application Guard installiert.

- **Application Guard:** Legen Sie fest, ob nicht genehmigten Websites in einem virtualisierten Hyper-V-Browsercontainer geöffnet werden sollen.
- **Verhalten der Zwischenablage:** Legen Sie zulässige Aktionen für das Kopieren und Einfügen zwischen dem lokalen Computer dem virtuellen Browser von Application Guard fest.
- **Externer Inhalt auf Unternehmenswebsites:** Legen Sie fest, ob das Laden von Inhalten blockiert werden soll, die von nicht genehmigten Websites stammen.
- **Aus virtuellem Browser drucken:** Legen Sie fest, ob PDF-Drucker, XPS-Drucker, lokale Drucker und/oder Netzwerkdrucker Inhalte aus dem virtuellen Browser drucken können.
- **Protokolle speichern:** Legen Sie fest, ob Protokolle für Ereignisse gespeichert werden, die während einer Browsersitzung von Application Guard auftreten.
- **Benutzergenerierte Browserdaten beibehalten:** Legen Sie fest, ob Benutzerdaten (z.B. Kennwörter, Favoriten und Cookies) gespeichert werden, die während einer virtuellen Browsersitzung von Application Guard erstellt werden.
- **Grafikbeschleunigung:** Lädt Websites mit vielen Grafiken schneller, wenn Sie innerhalb der virtuellen Browsersitzung von Application Guard arbeiten, indem der Zugriff auf einen virtuellen Grafikprozessor aktiviert wird.


## <a name="windows-defender-firewall"></a>Windows Defender Firewall

### <a name="global-settings"></a>Globale Einstellungen

Diese Einstellungen können auf alle Netzwerktypen angewendet werden.

- **File Transfer Protocol:** Legen Sie fest, ob statusbehaftetes FTP blockiert werden soll.
- **Leerlaufzeit für Sicherheitszuordnung vor Löschvorgang:** Legen Sie fest, ob Sicherheitszuordnungen gelöscht werden, wenn für *n* Sekunden kein Netzwerkdatenverkehr erkannt wird.
- **Codierung vorinstallierter Schlüssel:** Legen Sie fest, ob vorinstallierte Schlüssel mithilfe von UTF-8 codiert werden.
- **IPsec-Ausnahmen:** Legen Sie fest, ob bestimmter Datenverkehr von IPsec ausgenommen werden soll, einschließlich **Neighbor Discovery-IPv6-Codes vom Typ ICMP**, **ICMP**, **Router Discovery-IPv6-Codes vom Typ ICMP** und **IPv4- und IPv6-DHCP-Netzwerkdatenverkehr**.
- **Überprüfung der Zertifikatssperrliste:** Legen Sie einen Wert dafür fest, wie die Überprüfung der Zertifikatssperrliste erzwungen wird, einschließlich **Überprüfung der Zertifikatssperrliste deaktivieren**, **Überprüfung der Zertifikatssperrliste nur bei gesperrtem Zertifikat fehlerhaft** und **Überprüfung der Zertifikatssperrliste bei jedem Fehler fehlerhaft**.
- **Authentifizierungssatz opportunistisch pro Schlüsselerstellungsmodul abgleichen:** Legen Sie die Schlüsselerstellungsmodule darauf fest, den gesamten Authentifizierungssatz zu ignorieren, wenn nicht alle Authentifizierungssuites in diesem Satz unterstützt werden.
- **Paketwarteschlangen:** Legen Sie fest, wie die Skalierung für die Software auf der Empfangsseite für den verschlüsselten Empfang und die Weiterleitung im Klartext für das IPsec-Tunnelgatewayszenario aktiviert wird. Auf diese Weise wird die Paketreihenfolge beibehalten.

### <a name="network-settings"></a>Netzwerkeinstellungen

Diese Einstellungen gelten für bestimmte Netzwerktypen, einschließlich **Domänennetzwerk (Arbeitsplatz)**, **Privates Netzwerk (sichtbar)** und **Öffentliches Netzwerk (nicht sichtbar)**.

#### <a name="general-settings"></a>Allgemeine Einstellungen

- **Windows Defender Firewall:** Aktivieren Sie diese Einstellung, um Netzwerkdatenverkehr zu blockieren.
- **Geschützter Modus:** Legen Sie fest, ob der Betrieb der Firewall im geschützten Modus blockiert werden soll. Wenn Sie dies blockieren, ermöglichen Sie ebenfalls das Blockieren von **durch IPsec gesicherten Paketausnahmen**.
- **Abgeschirmt:** Aktivieren Sie diese Einstellung, damit die Firewall sämtlichen eingehenden Datenverkehr blockiert.
- **Unicastantworten auf Multicastbroadcasts:** Legen Sie fest, ob Unicastantworten auf Multicastbroadcasts blockiert werden sollen. In der Regel sollten keine Unicastantworten auf Multicast- oder Broadcastmeldungen empfangen werden, da solche Antworten auf einen Denial-of-Service-Angriff oder auf einen Angreifer hinweisen können, der versucht, einen bekannten Livecomputer zu durchsuchen.
- **Eingehende Benachrichtigungen:** Legen Sie fest, ob das Anzeigen von Benachrichtigungen für Benutzer blockiert werden soll, wenn eine Anwendung dafür blockiert wird, einen Port zu überwachen.
- **Standardaktion für eingehende Verbindungen:** Legen Sie fest, ob die Standardaktion blockiert werden soll, die die Firewall für eingehende Verbindungen ausführt.

#### <a name="rule-merging"></a>Regelzusammenführung

- **Windows Defender-Firewallregeln für autorisierte Anwendungen aus dem lokalen Speicher:** Legen Sie autorisierte Firewallregeln im lokalen Speicher fest, die erkannt und erzwungen werden sollen.
- **Windows Defender Firewall-Regeln für den globalen Port aus dem lokalen Speicher:** Legen Sie Firewallregeln für den globalen Port im lokalen Speicher fest, die erkannt und erzwungen werden sollen.
- **Windows Defender Firewall-Regeln aus dem lokalen Speicher:** Legen Sie globale Firewallregeln im lokalen Speicher fest, die erkannt und erzwungen werden sollen.
- **IPsec-Regeln aus dem lokalen Speicher:** Legen Sie Regeln für die Verbindungssicherheit aus dem lokalen Speicher fest, die unabhängig vom Schema oder den Versionen der Regeln zur Verbindungssicherheit gelten.

## <a name="windows-defender-smartscreen-settings"></a>Einstellungen für Windows Defender SmartScreen

- **SmartScreen für Apps und Dateien**: Hiermit wird Windows SmartScreen für die Datei- und App-Ausführung aktiviert.
- **Ausführung nicht überprüfter Dateien**: Hiermit wird die Ausführung von Dateien durch den Benutzer gesperrt, die nicht durch Windows SmartScreen überprüft wurden.

## <a name="windows-encryption"></a>Windows-Verschlüsselung

### <a name="windows-settings"></a>Windows-Einstellungen

Diese Einstellungen gelten für alle Versionen von Windows 10.

- **Geräte verschlüsseln**: Wenn diese Einstellung aktiviert ist, werden Benutzer dazu aufgefordert, die Geräteverschlüsselung zu aktivieren. Zusätzlich werden Sie gebeten zu bestätigen, dass keine Verschlüsselung eines anderen Anbieters aktiviert ist. Wenn die Windows-Verschlüsselung eingeschaltet wird, während eine andere Verschlüsselungsmethode aktiv ist, wird das Gerät möglicherweise instabil.
- **Speicherkarte verschlüsseln**: Wenn diese Einstellung aktiviert ist, werden alle vom Gerät verwendeten wechselbaren Speicherkarten verschlüsselt.


### <a name="bitlocker-base-settings"></a>BitLocker-Grundeinstellungen

Bei den Grundeinstellungen handelt es sich um universelle BitLocker-Einstellungen, die für alle Typen von Datenträgern gelten. Durch die BitLocker-Einstellungen für Gruppenrichtlinien wird verwaltet, welche Aufgaben für die Laufwerkverschlüsselung oder Konfigurationsoptionen der Benutzer auf allen Typen von Datenträgern ändern kann.

- **Warnung zu anderer Datenträgerverschlüsselung:** Legen Sie fest, ob das Anzeigen der Warnung für andere Datenträgerverschlüsselungen auf dem Computer des Benutzers deaktiviert werden soll.
- **Verschlüsselungsmethoden konfigurieren**: Wenn diese Einstellung aktiv ist, können Sie Verschlüsselungsalgorithmen für Betriebssystem-, Daten- und Wechseldatenträger konfigurieren.
    - **Verschlüsselung für Betriebssystemlaufwerke**: Wählen Sie die Verschlüsselungsmethode für Betriebssystemlaufwerken. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.
    - **Verschlüsselung für Festplattenlaufwerke**: Wählen Sie die Verschlüsselungsmethode für Festplattenlaufwerke (integriert). Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.
    - **Verschlüsselung für Wechseldatenträger**: Wählen Sie die Verschlüsselungsmethode für Wechseldatenträger. Wenn der Wechseldatenträger mit Geräten verwendet wird, die nicht unter Windows 10 laufen, wird empfohlen, dass Sie den AES-CBC-Algorithmus verwenden.

### <a name="bitlocker-os-drive-settings"></a>Einstellung für BitLocker-OS-Datenträger

Diese Einstellungen gelten speziell für Betriebssystemlaufwerke.

- **Zusätzliche Authentifizierung beim Start:** Konfigurieren Sie die Authentifizierungsanforderungen für den Computerstart, einschließlich der Verwendung von Trusted Platform Module (TPM).
    - **BitLocker mit nicht kompatiblem TPM-Chip**
    - **Systemstart für kompatibles TPM**: Legen Sie fest, ob ein TPM-Chip verwendet werden darf oder muss.
    - **Systemstart-PIN für kompatibles TPM**: Legen Sie fest, ob mit dem TPM-Chip eine Systemstart-PIN verwendet werden darf oder muss.
    - **Systemstartschlüssel für kompatibles TPM**: Legen Sie fest, ob mit dem TPM-Chip ein Systemstartschlüssel verwendet werden darf oder muss.
    - **Systemstartschlüssel und -Systemstart-PIN für kompatibles TPM**: Legen Sie fest, ob mit dem TPM-Chip ein Systemstartschlüssel und eine PIN verwendet werden darf oder muss.
- **PIN-Mindestlänge**: Wenn diese Einstellung aktiv ist, können Sie eine Mindestlänge für den TPM-Systemstart-PIN festlegen.
    - **Mindestanzahl von Zeichen**: Geben Sie die Zahl an Zeichen an, die für den Systemstart-PIN erforderlich sind, zwischen **4**-**20**.
- **Wiederherstellung von Betriebssystemlaufwerken**: Wenn diese Einstellung aktiviert ist, können Sie steuern, wie durch BitLocker geschützte Betriebssystemdatenträger wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht verfügbar sind.
    - **Agent für zertifikatbasierte Datenwiederherstellung**: Wenn diese Einstellung aktiv ist, können Datenwiederherstellungs-Agents mit durch BitLocker geschützten Betriebssystemdatenträgern verwendet werden.
    - **Erstellung des Wiederherstellungskennworts durch den Benutzer**: Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.
    - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**: Legen Sie fest, ob Benutzer ein 256-Bit-Wiederherstellungskennwort generieren dürfen oder müssen.
    - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten**: Wenn Sie diese Einstellung festlegen, können Sie verhindern, dass Benutzer Wiederherstellungsoptionen sehen bzw. ändern können, wenn sie BitLocker aktivieren.
    - **BitLocker-Wiederherstellungsinformationen in AD DS speichern**: Aktiviert das Speichern von BitLocker-Wiederherstellungsinformationen in Active Directory.
    - **In AD DS gespeicherte BitLocker-Wiederherstellungsinformationen**: Legen Sie fest, welche BitLocker-Wiederherstellungsinformationen in Active Directory gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:
        - **Wiederherstellungskennwörter und Schlüsselpakete sichern**
        - **Nur Wiederherstellungskennwörter sichern**
    - **Wiederherstellungsinformationen vor dem Aktivieren von BitLocker in AD DS speichern**: Aktivieren Sie diese Einstellung, um zu verhindern, dass Benutzer BitLocker aktivieren, es sei denn, das Gerät ist mit einer Domäne verbunden und BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Active Directory gespeichert.
- **Pre-Boot-Wiederherstellungsmeldung und -URL**: Legen Sie diese Einstellung fest, um die Meldung und URL zu konfigurieren, die auf dem Bildschirm der Pre-Boot-Schlüsselwiederherstellung angezeigt werden.
    - **Pre-Boot-Wiederherstellungsmeldung**: Legen Sie fest, wie die Pre-Boot-Wiederherstellungsmeldung Benutzern angezeigt wird. Es stehen die folgenden Optionen zur Auswahl:
        - **Standardmäßige Wiederherstellungsmeldung und -URL verwenden**
        - **Leere Wiederherstellungsmeldung und -URL verwenden**
        - **Benutzerdefinierte Wiederherstellungsmeldung**
        - **Benutzerdefinierte Wiederherstellungs-URL**


### <a name="bitlocker-fixed-data-drive-settings"></a>Einstellungen für das BitLocker-Festplattenlaufwerk

- **Schreibzugriff auf nicht durch BitLocker geschützte Festplattenlaufwerke**: Wenn diese Einstellung festgelegt wurde, muss der BitLocker-Schutz auf allen Festplattenlaufwerken und integrierten Laufwerken aktiviert sein, damit in sie geschrieben werden kann.
- **Wiederherstellung von Festplattenlaufwerken**: Wenn diese Einstellung festgelegt wurde, können Sie steuern, wie durch BitLocker geschützte Festplattenlaufwerke wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht vorliegen.
    - **Datenwiederherstellungs-Agent**: Wenn diese Einstellung aktiviert ist, können Datenwiederherstellungs-Agents mit durch BitLocker geschützten Festplattenlaufwerken verwendet werden.
    - **Erstellung des Wiederherstellungskennworts durch den Benutzer**: Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.  
    - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**: Legen Sie fest, ob Benutzer ein 256-Bit-Wiederherstellungskennwort generieren dürfen oder müssen.
    - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten**: Wenn Sie diese Einstellung festlegen, können Sie verhindern, dass Benutzer Wiederherstellungsoptionen sehen bzw. ändern können, wenn sie BitLocker aktivieren.
    - **BitLocker-Wiederherstellungsinformationen in AD DS speichern**: Aktiviert das Speichern von BitLocker-Wiederherstellungsinformationen in Active Directory.
    - **BitLocker-Wiederherstellungsinformationen in AD DS**: Legen Sie fest, welche BitLocker-Wiederherstellungsinformationen in Active Directory gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:
        - **Wiederherstellungskennwörter und Schlüsselpakete sichern**
        - **Nur Wiederherstellungskennwörter sichern**
    - **Wiederherstellungsinformationen vor dem Aktivieren von BitLocker in AD DS speichern**: Aktivieren Sie diese Einstellung, um zu verhindern, dass Benutzer BitLocker aktivieren, es sei denn, das Gerät ist mit einer Domäne verbunden und BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Active Directory gespeichert.

### <a name="bitlocker-removable-data-drive-settings"></a>Einstellungen für den BitLocker-Wechseldatenträger

- **Schreibzugriff auf nicht durch BitLocker geschützte Wechseldatenträger**: Legen Sie fest, ob die BitLocker-Verschlüsselung für Wechseldatenträger erforderlich ist.
  - **Schreibzugriff auf in einer anderen Organisation konfigurierte Geräte**: Legen Sie fest, ob in Wechseldatenträger, die einer anderen Organisation angehören, geschrieben werden darf.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Verwenden Sie [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard), um die Angriffsoberfläche von Apps, die von Ihren Angestellten verwendet werden, zu verwalten und zu reduzieren.

### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche

Wehren Sie [Aktionen und Apps](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) ab, die üblicherweise von Schadsoftware verwendet wird, die nach Sicherheitsproblemen sucht, um Computer zu infizieren.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regeln zum Verhindern von Bedrohungen durch Office-Makros

Blockieren Sie folgende Aktionen, die Office-Apps durchführen können:

- **Einschleusung von Code durch Office-Apps in andere Prozesse (keine Ausnahmen)**
- **Erstellung ausführbarer Inhalte in Office-Apps und -Makros**
- **Starten untergeordneter Prozesse in Office-Apps**
- **Win32-Importe aus Office-Makrocode**

#### <a name="rules-to-prevent-script-threats"></a>Regeln zum Verhindern von Bedrohungen durch Skripts

Blockieren Sie diese Optionen, um Bedrohungen durch Skripts zu verhindern:

- **Verborgener JS-/VBS-/PS-/Makrocode**
- **Ausführung von aus dem Internet heruntergeladener Nutzlast über JS/VBS (keine Ausnahmen)**

#### <a name="rules-to-prevent-email-threats"></a>Regeln zum Verhindern von Bedrohungen durch E-Mails

Blockieren Sie diese Optionen, um Bedrohungen durch E-Mails zu verhindern:

- **Ausführung ausführbarer Inhalte (EXE, DLL, PS, JS, VBS usw.), die per E-Mail (Webmail-/E-Mail-Client) zugestellt werden (keine Ausnahmen)**

#### <a name="attack-surface-reduction-exceptions"></a>Ausnahmen von der Verringerung der Angriffsfläche

- **Von Regeln zur Verringerung der Angriffsfläche auszuschließende Dateien und Ordner:** Importieren bzw. fügen Sie eine Liste von Speicherorten hinzu, die von den konfigurierten Regeln ausgeschlossen werden sollen.

### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff

Schützen Sie wichtige Daten vor schädlichen Apps und Bedrohungen, z.B. vor Ransomware.

- **Ordnerschutz:** Schützen Sie Dateien und Ordner vor unerwünschten Änderungen durch schädliche Apps. Sie können eine **Liste der Apps, die auf geschützte Ordner zugreifen können** importieren oder diese manuell hinzufügen. Sie können ebenfalls eine **Liste zusätzlicher Ordner, die geschützt werden müssen** hochladen, oder diese manuell hinzufügen.

### <a name="network-filtering"></a>Netzwerkfilterung

Blockieren Sie von jeder App ausgehende Verbindungen mit nicht vertrauenswürdigen IP-Adressen/Domänen.

### <a name="exploit-protection"></a>Exploit-Schutz

Blockieren Sie die **Bearbeitung der Exploit-Schutzumgebung durch Benutzer**, indem Sie eine XML-Datei hochladen, die Ihnen das Konfigurieren von Speicher-, Ablaufsteuerungs- und Richtlinieneinschränkungen ermöglichen, mit denen eine Anwendung vor Exploits geschützt werden kann.

Erstellen Sie zum Aktivieren des Exploit-Schutzes eine XML-Datei, die die gewünschten Einstellungen zur Risikominderung für System und Anwendungen darstellt. Hierzu gibt es zwei Möglichkeiten:

 1. PowerShell: Verwenden Sie mindestens eines der PowerShell-Cmdlets „Get-ProcessMitigation“, „Set-ProcessMitigation“ und „ConvertTo-ProcessMitigationPolicy“ zum Konfigurieren von Einstellungen zur Risikominderung, und exportieren Sie eine XML-Darstellung.

 2. Windows Defender Security Center-Benutzeroberfläche: Klicken Sie im Windows Defender Security Center auf „App > Browsersteuerung“, und scrollen Sie zum Ende des entsprechenden Bildschirms, um den Exploit-Schutz zu finden. Verwenden Sie zuerst die Registerkarten „Systemeinstellungen“ und „Programmeinstellungen“, um die Einstellungen für die Risikominderung zu konfigurieren. Suchen Sie anschließend den Link mit den Exporteinstellungen im unteren Bildschirmbereich, um eine XML-Darstellung zu exportieren.

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Verwenden Sie die **Anwendungssteuerungscode-Integritätsrichtlinien**, um zusätzliche Apps auszuwählen, die durch Windows Defender Application Control entweder überwacht werden müssen oder als vertrauenswürdig eingestuft und ausgeführt werden können. Windows-Komponenten und alle Apps aus dem Windows Store werden automatisch als zur Ausführung vertrauenswürdig eingestuft.

Anwendungen werden nicht blockiert, wenn sie im Modus **Nur überwachen** ausgeführt werden. Der Modus **Nur überwachen** protokolliert alle Ereignisse in lokalen Clientprotokollen.

Sobald die Anwendungssteuerung aktiviert ist, kann sie nur noch deaktiviert werden, indem der Modus von **Erzwingen** in **Nur überwachen** geändert wird. Wenn der Modus von **Erzwingen** in **Nicht konfiguriert** geändert wird, wird die Anwendungssteuerung weiterhin auf zugewiesenen Geräten erzwungen.

## <a name="windows-defender-security-center"></a>Windows Defender Security Center

Die Windows Defender Security Center-App fungiert als von den einzelnen Features separate App bzw. separater Prozess und zeigt über das Wartungscenter Benachrichtigungen an. Sie dienst als Collector oder zentraler Ort, um den Status anzuzeigen und Konfigurationen für die verschiedenen Features durchzuführen. Weitere Informationen finden Sie in den Dokumenten zu [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender Security Center-App und -Benachrichtigungen

Blockieren Sie den Benutzerzugriff auf die verschiedenen Bereiche der Windows Defender Security Center-App. Durch das Ausblenden eines Abschnitts werden auch die zugehörigen Benachrichtigungen blockiert.

- **Viren- und Bedrohungsschutz**
- **Geräteleistung und -integrität**
- **Firewall- und Netzwerkschutz**
- **App- und Browsersteuerung**
- **Familienoptionen**
- **Benachrichtigungen aus den angezeigten Bereichen der App:** Legen Sie fest, welche Benachrichtigungen dem Benutzer angezeigt werden sollen. Zu den nicht kritische Benachrichtigungen gehören Zusammenfassungen der Aktivitäten von Windows Defender Antivirus, Benachrichtigungen zum Abschluss von Überprüfungen eingeschlossen. Alle übrigen Benachrichtigungen gelten als kritisch.

#### <a name="it-contact-information"></a>IT-Kontaktinformationen

Stellen Sie IT-Kontaktinformationen bereit, die in der Windows Defender Security Center-App und in den App-Benachrichtigungen angezeigt werden. Sie können **In Apps und Benachrichtigungen anzeigen**, **Nur in App anzeigen**, **Nur in Benachrichtigungen anzeigen** oder **Don‘t display** (Nicht anzeigen) auswählen. Sie müssen den **Namen der IT-Organisation** und mindestens eine der folgenden Kontaktoptionen festlegen:

- **Telefonnummer oder Skype-ID der IT-Abteilung**
- **E-Mail-Adresse der IT-Abteilung**
- **URL der IT-Supportwebsite**

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie fortfahren und dieses Profil Gruppen zuweisen möchten, lesen Sie unter [Zuweisen von Geräteprofilen](device-profile-assign.md) nach.
