---
title: Hinzufügen von Endpoint Protection mit Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden oder konfigurieren Sie Einstellungen zu Endpoint Protection auf Windows 10-Geräten, um das Feature Windows Defender zu aktivieren, das Application Guard, Firewall, SmartScreen, Verschlüsselung und BitLocker, Exploit Guard, Anwendungssteuerung, Security Center und Sicherheit auf lokalen Geräten in Microsoft Intune enthält.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 069f71d75c0a9c7cec083a929f89a2b39bb4aac5
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Endpoint Protection-Einstellungen für Windows 10 und höher in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit dem Endpoint Protection-Profil können Sie Sicherheitsfeatures auf Windows 10-Geräten steuern, z.B. BitLocker und Windows Defender.

Verwenden Sie die Informationen in diesem Artikel, um Endpoint Protection-Profile zu erstellen. Informationen zum Konfigurieren von Windows Defender Antivirus finden Sie unter [Windows 10-Geräteeinschränkungen](device-restrictions-windows-10.md#windows-defender-antivirus). 

> [!NOTE]
> Diese Einstellungen werden nicht auf der Home Edition und auf der Professional Edition von Windows 10 unterstützt.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Bei der Verwendung von Microsoft Edge schützt Windows Defender Application Guard Ihre Umgebung vor Websites, die von Ihrer Organisation nicht als vertrauenswürdig definiert wurden. Wenn Benutzer Websites besuchen, die nicht in Ihrer isolierten Netzwerkgrenze aufgelistet sind, werden die Websites in einer virtuellen Browsersitzung in Hyper-V geöffnet. Vertrauenswürdige Websites werden durch eine Netzwerkgrenze definiert, die in der Gerätekonfiguration konfiguriert werden kann. 

Application Guard ist nur für Windows 10-Geräte (64-Bit) verfügbar. Mithilfe dieses Profils wird eine Win32-Komponente zur Aktivierung von Application Guard installiert.

- **Application Guard**: Nicht genehmigte Websites werden in einem virtualisierten Hyper-V-Browsercontainer geöffnet.
- **Verhalten der Zwischenablage**: Legen Sie zulässige Aktionen für das Kopieren und Einfügen zwischen dem lokalen Computer und dem virtuellen Browser von Application Guard fest.
- **Externer Inhalt auf Unternehmenswebsites**: Legen Sie fest, ob das Laden von Inhalten blockiert werden soll, die von nicht genehmigten Websites stammen.
- **Aus virtuellem Browser drucken**: Legen Sie fest, ob PDF-Drucker, XPS-Drucker, lokale Drucker und/oder Netzwerkdrucker Inhalte aus dem virtuellen Browser drucken können.
- **Protokolle speichern**: Legen Sie fest, ob Protokolle für Ereignisse gespeichert werden, die während einer Browsersitzung von Application Guard auftreten.
- **Benutzergenerierte Browserdaten beibehalten**: Während einer virtuellen Browsersitzung von Application Guard erstellte Benutzerdaten (z.B. Kennwörter, Favoriten und Cookies) werden gespeichert.
- **Grafikbeschleunigung**: Websites mit vielen Grafiken werden schneller geladen, wenn Sie innerhalb der virtuellen Browsersitzung von Application Guard arbeiten. Websites arbeiten schneller, indem der Zugriff auf einen virtuellen Grafikprozessor aktiviert wird.
- **Dateien herunterladen, um Dateisystem zu hosten**: Benutzer können Dateien aus dem virtualisierten Browser auf das Hostbetriebssystem herunterladen.

## <a name="windows-defender-firewall"></a>Windows Defender Firewall

### <a name="global-settings"></a>Globale Einstellungen

Diese Einstellungen können auf alle Netzwerktypen angewendet werden.

- **File Transfer Protocol**: Legen Sie fest, ob statusbehaftetes FTP blockiert werden soll.
- **Leerlaufzeit für Sicherheitszuordnung vor Löschvorgang**: Sicherheitszuordnungen werden gelöscht, wenn für *n* Sekunden kein Netzwerkdatenverkehr erkannt wird.
- **Codierung vorinstallierter Schlüssel**: Codieren vorinstallierter Schlüssel mithilfe von UTF-8.
- **IPsec-Ausnahmen**: Legen Sie fest, ob bestimmter Datenverkehr von IPsec ausgenommen werden soll, einschließlich **Neighbor Discovery-IPv6-Codes vom Typ ICMP**, **ICMP**, **Router Discovery-IPv6-Codes vom Typ ICMP** und **IPv4- und IPv6-DHCP-Netzwerkdatenverkehr**.
- **Überprüfung der Zertifikatssperrliste**: Legen Sie einen Wert dafür fest, wie die Überprüfung der Zertifikatssperrliste erzwungen wird, einschließlich **Überprüfung der Zertifikatssperrliste deaktivieren**, **Überprüfung der Zertifikatssperrliste nur bei gesperrtem Zertifikat fehlerhaft** und **Überprüfung der Zertifikatssperrliste bei jedem Fehler fehlerhaft**.
- **Authentifizierungssatz opportunistisch pro Schlüsselerstellungsmodul abgleichen**: Legen Sie die Schlüsselerstellungsmodule darauf fest, den gesamten Authentifizierungssatz zu ignorieren, wenn nicht alle Authentifizierungssuites in diesem Satz unterstützt werden.
- **Paketwarteschlangen**: Legen Sie fest, wie die Skalierung für die Software auf der Empfangsseite für den verschlüsselten Empfang und die Weiterleitung im Klartext für das IPsec-Tunnelgatewayszenario aktiviert wird. Durch diese Einstellung wird die Paketreihenfolge beibehalten.

### <a name="network-settings"></a>Netzwerkeinstellungen

Diese Einstellungen gelten für bestimmte Netzwerktypen, einschließlich **Domänennetzwerk (Arbeitsplatz)**, **Privates Netzwerk (sichtbar)** und **Öffentliches Netzwerk (nicht sichtbar)**.

#### <a name="general-settings"></a>Allgemeine Einstellungen

- **Windows Defender Firewall**: Aktivieren Sie diese Einstellung, um Netzwerkdatenverkehr zu blockieren.
- **Geschützter Modus**: Legen Sie fest, ob der Betrieb der Firewall im geschützten Modus blockiert werden soll. Wenn Sie den geschützten Modus blockieren, ermöglichen Sie ebenfalls das Blockieren von **durch IPsec gesicherten Paketausnahmen**.
- **Abgeschirmt**: Aktivieren Sie diese Einstellung, damit die Firewall sämtlichen eingehenden Datenverkehr blockiert.
- **Unicastantworten auf Multicastbroadcasts**: Legen Sie fest, ob Unicastantworten auf Multicastbroadcasts blockiert werden sollen. Sie möchten wohl keine Unicastantworten auf Multicast- oder Broadcastmeldungen empfangen. Diese Antworten können auf einen DoS-Angriff (Denial of Service) hinweisen, oder einen Angreifer, der versucht, einen bekanntermaßen aktiven Computer zu testen.
- **Eingehende Benachrichtigungen**: Legen Sie fest, ob das Anzeigen von Benachrichtigungen für Benutzer blockiert werden soll, wenn eine Anwendung für das Lauschen auf einen Port blockiert ist.
- **Standardaktion für eingehende Verbindungen**: Legen Sie fest, ob die Standardaktion blockiert werden soll, die die Firewall für eingehende Verbindungen ausführt.

#### <a name="rule-merging"></a>Regelzusammenführung

- **Windows Defender-Firewallregeln für autorisierte Anwendungen aus dem lokalen Speicher**: Legen Sie autorisierte Firewallregeln im lokalen Speicher fest, die erkannt und erzwungen werden sollen.
- **Windows Defender Firewall-Regeln für den globalen Port aus dem lokalen Speicher**: Legen Sie Firewallregeln für den globalen Port im lokalen Speicher fest, die erkannt und erzwungen werden sollen.
- **Windows Defender Firewall-Regeln aus dem lokalen Speicher**: Legen Sie globale Firewallregeln im lokalen Speicher fest, die erkannt und erzwungen werden sollen.
- **IPsec-Regeln aus dem lokalen Speicher**: Legen Sie Regeln für die Verbindungssicherheit aus dem lokalen Speicher fest, die unabhängig vom Schema oder den Versionen der Regeln zur Verbindungssicherheit gelten.

## <a name="windows-defender-smartscreen-settings"></a>Einstellungen für Windows Defender SmartScreen

- **SmartScreen für Apps und Dateien**: Hiermit wird Windows SmartScreen für die Datei- und App-Ausführung aktiviert.
- **Ausführung nicht überprüfter Dateien**: Hiermit wird die Ausführung von Dateien durch den Benutzer gesperrt, die nicht durch Windows SmartScreen überprüft wurden.

## <a name="windows-encryption"></a>Windows-Verschlüsselung

### <a name="windows-settings"></a>Windows-Einstellungen

Die folgenden beiden Einstellungen gelten für alle Versionen von Windows 10:

- **Geräte verschlüsseln**: Wenn diese Einstellung aktiviert ist, werden Benutzer dazu aufgefordert, die Geräteverschlüsselung zu aktivieren. Zusätzlich werden Sie gebeten zu bestätigen, dass keine Verschlüsselung eines anderen Anbieters aktiviert ist. Wenn die Windows-Verschlüsselung eingeschaltet wird, während eine andere Verschlüsselungsmethode aktiv ist, wird das Gerät möglicherweise instabil.
- **Speicherkarte verschlüsseln**: Wenn diese Einstellung aktiviert ist, werden alle vom Gerät verwendeten wechselbaren Speicherkarten verschlüsselt.


### <a name="bitlocker-base-settings"></a>BitLocker-Grundeinstellungen

Bei den Grundeinstellungen handelt es sich um universelle BitLocker-Einstellungen, die für alle Typen von Datenträgern gelten. Durch die BitLocker-Einstellungen für Gruppenrichtlinien wird verwaltet, welche Aufgaben für die Laufwerkverschlüsselung oder Konfigurationsoptionen der Benutzer auf allen Typen von Datenträgern ändern kann.

- **Warnung zu anderer Datenträgerverschlüsselung**: Legen Sie fest, ob das Anzeigen der Warnung für andere Datenträgerverschlüsselungen auf dem Computer des Benutzers deaktiviert werden soll.
- **Verschlüsselungsmethoden konfigurieren**: Wenn diese Einstellung aktiv ist, können Sie Verschlüsselungsalgorithmen für Betriebssystem-, Daten- und Wechseldatenträger konfigurieren.
  - **Verschlüsselung für Betriebssystemlaufwerke**: Wählen Sie die Verschlüsselungsmethode für Betriebssystemlaufwerke aus. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.
  - **Verschlüsselung für Festplattenlaufwerke**: Wählen Sie die Verschlüsselungsmethode für Festplattenlaufwerke (integriert) aus. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.
  - **Verschlüsselung für Wechseldatenträger**: Wählen Sie die Verschlüsselungsmethode für Wechseldatenträger aus. Wenn der Wechseldatenträger mit Geräten verwendet wird, die nicht unter Windows 10 laufen, wird empfohlen, dass Sie den AES-CBC-Algorithmus verwenden.

### <a name="bitlocker-os-drive-settings"></a>Einstellung für BitLocker-OS-Datenträger

Diese Einstellungen gelten speziell für Betriebssystemlaufwerke.

- **Zusätzliche Authentifizierung beim Start**: Konfigurieren Sie die Authentifizierungsanforderungen für den Computerstart, einschließlich der Verwendung von Trusted Platform Module (TPM).
  - **BitLocker mit nicht kompatiblem TPM-Chip**
  - **Systemstart für kompatibles TPM**: Legen Sie fest, ob der TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist.
  - **Systemstart-PIN für kompatibles TPM**: Legen Sie fest, ob mit dem TPM-Chip eine Systemstart-PIN zugelassen, nicht zugelassen oder erforderlich ist.
  - **Systemstartschlüssel für kompatibles TPM**: Legen Sie fest, ob die Verwendung eines Systemstartschlüssels mit dem TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist.
  - **Systemstartschlüssel und Systemstart-PIN für kompatibles TPM**: Legen Sie fest, ob die Verwendung eines Systemstartschlüssels und einer PIN mit dem TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist.
- **PIN-Mindestlänge**: Wenn diese Einstellung aktiv ist, können Sie eine Mindestlänge für dle TPM-Systemstart-PIN festlegen.
  - **Mindestanzahl von Zeichen**: Geben Sie die Zahl an Zeichen (**4**-**20**) an, die für die Systemstart-PIN erforderlich sind.
- **Wiederherstellung von Betriebssystemlaufwerken**: Wenn diese Einstellung aktiviert ist, können Sie steuern, wie durch BitLocker geschützte Betriebssystemdatenträger wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht verfügbar sind.
  - **Agent für zertifikatbasierte Datenwiederherstellung**: Wenn diese Einstellung aktiv ist, können Datenwiederherstellungs-Agents mit durch BitLocker geschützten Betriebssystemdatenträgern verwendet werden.
  - **Erstellung des Wiederherstellungskennworts durch den Benutzer**: Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.
  - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**: Legen Sie fest, ob Benutzer einen 256-Bit-Wiederherstellungsschlüssel generieren dürfen oder müssen.
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

- **Schreibzugriff auf nicht durch BitLocker geschützte Festplattenlaufwerke**: Wenn diese Einstellung festgelegt wurde, muss der BitLocker-Schutz auf allen Festplattenlaufwerken und integrierten Laufwerken aktiviert sein, damit sie beschrieben werden können.
- **Wiederherstellung von Festplattenlaufwerken**: Wenn diese Einstellung festgelegt wurde, können Sie steuern, wie durch BitLocker geschützte Festplattenlaufwerke wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht vorliegen.
  - **Datenwiederherstellungs-Agent**: Wenn diese Einstellung aktiviert ist, können Datenwiederherstellungs-Agents mit durch BitLocker geschützten Festplattenlaufwerken verwendet werden.
  - **Erstellung des Wiederherstellungskennworts durch den Benutzer**: Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.  
  - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**: Legen Sie fest, ob Benutzer einen 256-Bit-Wiederherstellungsschlüssel generieren dürfen oder müssen.
  - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten**: Wenn Sie diese Einstellung festlegen, können Sie verhindern, dass Benutzer Wiederherstellungsoptionen sehen bzw. ändern können, wenn sie BitLocker aktivieren.
  - **BitLocker-Wiederherstellungsinformationen in AD DS speichern**: Aktiviert das Speichern von BitLocker-Wiederherstellungsinformationen in Active Directory.
  - **BitLocker-Wiederherstellungsinformationen in AD DS**: Legen Sie fest, welche BitLocker-Wiederherstellungsinformationen in Active Directory gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:
    - **Wiederherstellungskennwörter und Schlüsselpakete sichern**
    - **Nur Wiederherstellungskennwörter sichern**
  - **Wiederherstellungsinformationen vor dem Aktivieren von BitLocker in AD DS speichern**: Aktivieren Sie diese Einstellung, um zu verhindern, dass Benutzer BitLocker aktivieren, es sei denn, das Gerät ist mit einer Domäne verbunden und BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Active Directory gespeichert.

### <a name="bitlocker-removable-data-drive-settings"></a>Einstellungen für den BitLocker-Wechseldatenträger

- **Schreibzugriff auf nicht durch BitLocker geschützte Wechseldatenträger**: Legen Sie fest, ob die BitLocker-Verschlüsselung für Wechseldatenträger erforderlich ist.
  - **Schreibzugriff auf in einer anderen Organisation konfigurierte Geräte**: Legen Sie fest, ob Wechseldatenträger, die einer anderen Organisation angehören, beschrieben werden düren.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Verwenden Sie [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard), um die Angriffsoberfläche von Apps, die von Ihren Angestellten verwendet werden, zu verwalten und zu reduzieren.

### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche

- **Abgreifen von Anmeldeinformationen über das Subsystem der lokalen Sicherheitsautorität von Windows kennzeichnen**

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
- **Prozesserstellung über die Befehle „PSExec“ und „WMI“**
- **Nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden**
- **Ausführbare Dateien, die keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen**

#### <a name="rules-to-prevent-email-threats"></a>Regeln zum Verhindern von Bedrohungen durch E-Mails

Blockieren Sie diese Optionen, um Bedrohungen durch E-Mails zu verhindern:

- **Ausführung ausführbarer Inhalte (EXE, DLL, PS, JS, VBS usw.), die per E-Mail (Webmail-/E-Mail-Client) zugestellt werden (keine Ausnahmen)**

#### <a name="rules-to-protect-against-ransomware"></a>Regeln zum Schutz vor Ransomware
- **Erweiterter Schutz vor Ransomware**

> [!TIP]
> Weitere Informationen über diese Regeln finden Sie unter [Reduce attack surfaces with Windows Defender Exploit Guard (Reduzieren von Attacken auf die Oberflächen mit Windows Defender Exploit Guard)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard).

#### <a name="attack-surface-reduction-exceptions"></a>Ausnahmen von der Verringerung der Angriffsfläche

- **Von Regeln zur Verringerung der Angriffsfläche auszuschließende Dateien und Ordner**: Importieren bzw. fügen Sie eine Liste von Speicherorten hinzu, die von den konfigurierten Regeln ausgeschlossen werden sollen.

### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff

Schützen Sie wichtige Daten vor schädlichen Apps und Bedrohungen, z.B. vor Ransomware.

- **Ordnerschutz**: Schützen Sie Dateien und Ordner vor unerwünschten Änderungen durch schädliche Apps. Sie können eine **Liste der Apps, die auf geschützte Ordner zugreifen können** importieren oder diese manuell hinzufügen. Sie können ebenfalls eine **Liste zusätzlicher Ordner, die geschützt werden müssen** hochladen, oder diese manuell hinzufügen.

### <a name="network-filtering"></a>Netzwerkfilterung

Blockieren Sie von jeder App ausgehende Verbindungen mit nicht vertrauenswürdigen IP-Adressen/Domänen.

### <a name="exploit-protection"></a>Exploit-Schutz

Blockieren Sie die **Bearbeitung der Exploit-Schutzumgebung durch Benutzer**, indem Sie eine XML-Datei hochladen, die Ihnen das Konfigurieren von Speicher-, Ablaufsteuerungs- und Richtlinieneinschränkungen ermöglicht. Die Einstellungen in der XML-Datei können eine Anwendung vor Exploits schützen.

Erstellen Sie zum Aktivieren des Exploit-Schutzes eine XML-Datei, die die gewünschten Einstellungen zur Risikominderung für System und Anwendungen darstellt. Hierzu gibt es zwei Möglichkeiten:

 1. PowerShell: Verwenden Sie mindestens eines der PowerShell-Cmdlets Get-ProcessMitigation, Set-ProcessMitigation und ConvertTo-ProcessMitigationPolicy. Die Cmdlets konfigurieren Einstellungen zur Risikominderung und exportieren eine XML-Darstellung von ihnen.

 2. Windows Defender Security Center-Benutzeroberfläche: Klicken Sie im Windows Defender Security Center auf „App > Browsersteuerung“, und scrollen Sie zum Ende des entsprechenden Bildschirms, um den Exploit-Schutz zu finden. Verwenden Sie zuerst die Registerkarten „Systemeinstellungen“ und „Programmeinstellungen“, um die Einstellungen für die Risikominderung zu konfigurieren. Suchen Sie anschließend den Link mit den Exporteinstellungen im unteren Bildschirmbereich, um eine XML-Darstellung zu exportieren.

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Verwenden Sie die **Anwendungssteuerungscode-Integritätsrichtlinien**, um zusätzliche Apps auszuwählen, die durch Windows Defender Application Control überwacht werden müssen oder als vertrauenswürdig eingestuft und ausgeführt werden können. Windows-Komponenten und alle Apps aus dem Windows Store werden automatisch als zur Ausführung vertrauenswürdig eingestuft.

Anwendungen werden nicht blockiert, wenn sie im Modus **Nur überwachen** ausgeführt werden. Der Modus **Nur überwachen** protokolliert alle Ereignisse in lokalen Clientprotokollen.

Sobald die Anwendungssteuerung aktiviert ist, kann sie nur noch deaktiviert werden, indem der Modus von **Erzwingen** in **Nur überwachen** geändert wird. Wenn der Modus von **Erzwingen** in **Nicht konfiguriert** geändert wird, wird die Anwendungssteuerung weiterhin auf zugewiesenen Geräten erzwungen.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
Windows Defender Credential Guard schützt vor Angriffen zum Diebstahl von Anmeldeinformationen. Geheime Schlüssel werden isoliert, damit nur privilegierte Systemsoftware darauf zugreifen kann.

Die **Credential Guard** Einstellungen beinhalten:

- **Deaktiviert**: Deaktiviert Credential Guard per Remoteverbindung, wenn das Programm zuvor über die Option **Ohne UEFI-Sperre aktivieren** aktiviert wurde.
- **Mit UEFI-Sperre aktivieren**: Gewährleistet, dass Credential Guard nicht mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie remote deaktiviert werden kann.

    > [!NOTE]
    > Wenn Sie diese Einstellung verwenden und dann später Credential Guard deaktivieren möchten, müssen Sie die Gruppenrichtlinie auf **Deaktiviert** setzen. Außerdem müssen Sie die UEFI-Konfigurationsinformationen physisch von den einzelnen Computern löschen. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

- **Ohne UEFI-Sperre aktivieren**: Ermöglicht, Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie zu deaktivieren. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

Wenn Sie Credential Guard aktivieren, werden auch die folgenden erforderlichen Features aktiviert:

- **Virtualisierungsbasierte Sicherheit** (VBS): Wird beim nächsten Neustart aktiviert. Virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen.
- **Sicherer Start mit direktem Speicherzugriff**: Aktiviert VBS mit Schutzmaßnahmen wie sicherem Start und direktem Speicherzugriff (Direct Memory Access, DMA). Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf richtig konfigurierten Geräten aktiviert.

## <a name="windows-defender-security-center"></a>Windows Defender Security Center

Die Windows Defender Security Center-App fungiert als von den einzelnen Features separate App bzw. separater Prozess. Sie zeigt Benachrichtigungen über das Info-Center an. Sie dienst als Collector oder zentraler Ort, um den Status anzuzeigen und Konfigurationen für die verschiedenen Features durchzuführen. Weitere Informationen finden Sie in den Dokumenten zu [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender Security Center-App und -Benachrichtigungen

Blockieren Sie den Benutzerzugriff auf die verschiedenen Bereiche der Windows Defender Security Center-App. Durch das Ausblenden eines Abschnitts werden auch die zugehörigen Benachrichtigungen blockiert.

- **Viren- und Bedrohungsschutz**
- **Geräteleistung und -integrität**
- **Firewall- und Netzwerkschutz**
- **App- und Browsersteuerung**
- **Familienoptionen**
- **Benachrichtigungen aus den angezeigten Bereichen der App**: Legen Sie fest, welche Benachrichtigungen dem Benutzer angezeigt werden sollen. Zu den nicht kritische Benachrichtigungen gehören Zusammenfassungen der Aktivitäten von Windows Defender Antivirus, Benachrichtigungen zum Abschluss von Überprüfungen eingeschlossen. Alle übrigen Benachrichtigungen gelten als kritisch.

#### <a name="it-contact-information"></a>IT-Kontaktinformationen

Stellen Sie IT-Kontaktinformationen bereit, die in der Windows Defender Security Center-App und in den App-Benachrichtigungen angezeigt werden. Sie können **In Apps und Benachrichtigungen anzeigen**, **Nur in App anzeigen**, **Nur in Benachrichtigungen anzeigen** oder **Don‘t display** (Nicht anzeigen) auswählen. Sie müssen den **Namen der IT-Organisation** und mindestens eine der folgenden Kontaktoptionen eingeben:

- **Telefonnummer oder Skype-ID der IT-Abteilung**
- **E-Mail-Adresse der IT-Abteilung**
- **URL der IT-Supportwebsite**

## <a name="local-device-security-options"></a>Sicherheitsoptionen für lokale Geräte

Konfigurieren Sie mit diesen Optionen die lokalen Sicherheitseinstellungen auf Windows 10-Geräten.

### <a name="accounts"></a>Konten

- **Neue Microsoft-Konten hinzufügen**: Verhindert, dass Benutzer diesem Computer neue Microsoft-Konten hinzufügen.
- **Remoteanmeldung ohne Kennwort**: Ermöglichen Sie lokalen Konten, die nicht kennwortgeschützt sind, die Anmeldung von anderen Speicherorten aus als dem physischen Gerät.

#### <a name="admin"></a>Administrator

- **Lokales Administratorkonto**: Legen Sie fest, ob das lokale Administratorkonto aktiviert oder deaktiviert ist.
- **Administratorkonto umbenennen**: Definieren Sie einen anderen Kontonamen, der der Sicherheits-ID (SID) für das Administratorkonto zugeordnet werden soll.

#### <a name="guest"></a>Gast

- **Gastkonto**: Bestimmen Sie, ob das Gastkonto aktiviert oder deaktiviert ist.
- **Gastkonto umbenennen**: Definieren Sie einen anderen Kontonamen, der der Sicherheits-ID (SID) für das Gastkonto zugeordnet werden soll.

### <a name="devices"></a>Geräte

- **Gerät ohne Anmeldung abdocken**: Verhindern Sie, dass ein tragbarer Computer ohne Anmeldung abgedockt werden kann.
- **Druckertreiber für freigegebene Drucker installieren**: Beschränken Sie die Installation von Druckertreibern als Teil des Herstellens einer Verbindung mit einem freigegebenen Drucker auf Administratoren.
- **CD-ROM-Zugriff auf lokale aktive Benutzer beschränken**: Bei Aktivieren dieser Einstellung können nur interaktiv angemeldete Benutzer auf CD-ROM-Medien zugreifen.
- **Wechselmedien formatieren und auswerfen**: Definieren Sie, wer NTFS-Wechselmedien formatieren und auswerfen darf:
  - **Nicht konfiguriert**
  - **Administratoren und Poweruser**
  - **Administratoren und interaktive Benutzer**

### <a name="interactive-logon"></a>Interaktive Anmeldung

- **Inaktivität in Minuten für Anmeldebildschirm bis zur Aktivierung des Bildschirmschoners**: Definieren Sie die maximale Anzahl von Minuten der Inaktivität auf dem Anmeldebildschirm des interaktiven Desktops, bis der Bildschirmschoner ausgeführt wird.
- **STRG+ALT+ENTF zur Anmeldung voraussetzen**: Setzen Sie voraus, dass STRG+ALT+ENTF gedrückt wird, bevor sich ein Benutzer anmelden kann.
- **Verhalten beim Entfernen von Smartcards**: Bestimmt, was geschieht, wenn die Smartcard für einen angemeldeten Benutzer aus den Smartkartenleser entfernt wird.
[LocalPoliciesSecurity-Optionen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) enthalten weitere Details.

#### <a name="display"></a>Anzeige

- **Benutzerinformationen auf Sperrbildschirm**: Konfigurieren Sie die Benutzerinformationen, die angezeigt werden, wenn die Sitzung gesperrt ist. Wenn nicht konfiguriert, werden Anzeigename des Benutzers, Domäne und Benutzername angezeigt.
  - **Nur Anzeigename des Benutzers**
  - **Benutzerinformationen nicht anzeigen**
  - **Nicht konfiguriert**: Anzeigename des Benutzers, Domäne und Benutzername.
- **Zuletzt angemeldeten Benutzer ausblenden**: Der Benutzername der letzten Person, die sich bei diesem Gerät angemeldet hat, wird nicht angezeigt.
- **Benutzernamen bei der Anmeldung ausblenden**: Der Benutzername der Person, die sich nach Eingabe der Anmeldeinformationen und vor Anzeige des Desktops des Geräts bei diesem Gerät angemeldet hat, wird nicht angezeigt.
- **Anmeldungsmeldungstitel**: Legen Sie den Meldungstitel für Benutzer fest, die versuchen, sich anzumelden.
- **Anmeldungsmeldungstextl**: Legen Sie den Meldungstext für Benutzer fest, die versuchen, sich anzumelden.

### <a name="network-access-and-security"></a>Netzwerkzugriff und Sicherheit

- **Anonymer Zugriff auf Named Pipes und Freigaben**: Schränkt den anonymen Zugriff auf Freigabe- und Named Pipe-Einstellungen ein. Gilt für die Einstellungen, auf die anonym zugegriffen werden kann.
- **Anonyme Aufzählung von SAM-Konten**: Ermöglicht anonymen Benutzern, die SAM-Konten aufzuzählen. Windows ermöglicht anonymen Benutzern, die Namen von Domänenkonten und Netzwerkfreigaben aufzuzählen.
- **Anonyme Aufzählung von SAM-Konten und Freigaben**: Kann die anonyme Aufzählung von SAM-Konten und Freigaben blockieren. Windows ermöglicht anonymen Benutzern, die Namen von Domänenkonten und Netzwerkfreigaben aufzuzählen.
- **LAN-Manager-Hashwert bei Kennwortänderung speichern**: Wählen Sie, ob bei der nächsten Kennwortänderung der LAN-Manager-Hashwert (LM) für das neue Kennwort gespeichert wird. Standardmäßig wird er nicht gespeichert.
- **PKU2U-Authentifizierungsanforderungen**: Schränken Sie an dieses Gerät gerichtete PKU2U-Authentifizierungsanforderungen auf die ausschließliche Verwendung von Onlineidentitäten ein.
- **RPC-Remoteverbindungen mit SAM einschränken**: Bearbeiten Sie die Security Descriptor Definition Language-Standardzeichenfolge, um Benutzern und Gruppen Remoteaufrufe an SAM zu gewähren oder zu verweigern.
- **Sicherheitsbeschreibung**

### <a name="recovery-console-and-shutdown"></a>Wiederherstellungskonsole und Herunterfahren

- **Virtuellen Arbeitsspeicher beim Herunterfahren löschen**: Die Auslagerungsdatei des virtuellen Arbeitsspeichers wird beim Herunterfahren des Geräts gelöscht.
- **Herunterfahren ohne Anmeldung**: Blockieren Sie die Option zum Herunterfahren des Computers vom Windows-Anmeldebildschirm aus. In diesem Fall müssen Benutzer sich erfolgreich bei dem Computer anmelden können, bevor sie das System herunterfahren können.

### <a name="user-account-control"></a>Benutzerkontensteuerung

- **UIA-Integrität ohne sicheren Speicherort**: Ermöglichen Sie die Ausführung von Apps von unsicheren Speicherorten im Dateisystem mit UIAccess-Integritätsstufe.
- **Fehler bei Schreibvorgängen für Dateien und Registrierung basierend auf Benutzerspeicherorten virtualisieren**: Bestimmen Sie, ob App-Schreibfehler an definierte Registrierungs- und Dateisystemorte umgeleitet werden. Alternativ können Sie veranlassen, dass die Ausführung der App erfolglos ist.
- **Rechte nur für ausführbare Dateien erhöhen, die signiert und validiert wurden**: Erzwingen Sie die PKI-Zertifizierungspfadüberprüfung für eine angegebene ausführbare Datei, bevor ihre Ausführung gestattet wird.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Einstellungen des Verhaltens der UIA-Eingabeaufforderung für erhöhte Rechte

- **Eingabeaufforderung für erhöhte Rechte für Administratoren**: Definieren Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Administratoren im Administratorbestätigungsmodus:
  - **Rechte ohne Eingabeaufforderung erhöhen**
  - **Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop**
  - **Eingabeaufforderung zur Zustimmung auf dem sicheren Desktop**
  - **Eingabeaufforderung zu Anmeldeinformationen**
  - **Eingabeaufforderung zur Zustimmung**
  - **Nicht konfiguriert**: Eingabeaufforderung zur Zustimmung für Nicht-Windows-Binärdateien
- **Eingabeaufforderung für erhöhte Rechte für Standardbenutzer**: Definieren Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Standardbenutzer:
  - **Anforderungen für erhöhte Rechte automatisch ablehnen**
  - **Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop**
  - **Nicht konfiguriert**: Eingabeaufforderung für Anmeldeinformationen
- **Eingabeaufforderung für erhöhte Rechte an interaktiven Desktop des Benutzers umleiten**: Hiermit werden alle Anforderungen für erhöhte Rechte nicht an den sicheren Desktop, sondern an den interaktiven Benutzerdesktop umgeleitet. Es werden Richtlinieneinstellungen für das Verhalten der Eingabeaufforderung für Administratoren und Standardbenutzer verwendet.
- **Eingabeaufforderung für erhöhte Rechte bei App-Installationen**: App-Installationen, die erhöhte Rechte erfordern, fordern zur Eingabe von Administratoranmeldeinformationen auf.
- **UIA-Eingabeaufforderung für erhöhte Rechte ohne sicheren Desktop**: UIAccess-Apps können erhöhte Rechte ohne sicheren Desktop anfordern.

#### <a name="admin-approval-mode-settings"></a>Administratorgenehmigungsmodus-Einstellungen

- **Administratorgenehmigungsmodus für integrierten Administrator**: Definiert, ob das integrierte Administratorkonto den Administratorgenehmigungsmodus verwendet oder alle Apps mit vollständigen Administratorberechtigungen ausführt.
- **Alle Administratoren im Administratorgenehmigungsmodus ausführen**: Definiert, ob Administratorgenehmigungsmodus und alle UAC-Richtlinieneinstellungen aktiviert sind.

### <a name="microsoft-network-client"></a>Microsoft-Netzwerkclient

- **Kommunikation digital signieren (wenn Server zustimmt)**: Bestimmt, ob der SMB-Client versucht, die SMB-Paketsignatur auszuhandeln. Bei Aktivierung (Standard) fordert der Microsoft-Netzwerkclient den Server zur Durchführung der SMB-Paketsignatur beim Setup der Sitzung auf. Wenn die Paketsignatur auf dem Server aktiviert wurde, wird die Paketsignatur ausgehandelt. Wenn diese Richtlinie deaktiviert ist, handelt der SMB-Client nie die SMB-Paketsignatur aus.
- **Unverschlüsseltes Kennwort an SMB-Server von Drittanbietern senden**: Wenn diese Sicherheitseinstellung aktiviert ist, darf der SMB-Redirector (Server Message Block) Klartextkennwörter an Nicht-Microsoft-SMB-Server senden, die keine Kennwortverschlüsselung während der Authentifizierung unterstützen.

### <a name="microsoft-network-server"></a>Microsoft-Netzwerkserver

- **Kommunikation digital signieren (wenn Client zustimmt)**: Bestimmt, ob der SMB-Server die SMB-Paketsignatur mit Clients verhandelt, die sie anfordern. Wenn aktiviert, handelt der Microsoft-Netzwerkserver die SMB-Paketsignatur wie vom Client angefordert aus. Genau gesagt: Wenn die Paketsignatur auf dem Client aktiviert ist, wird die Paketsignatur ausgehandelt. Wenn sie deaktiviert ist (Standard), handelt der SMB-Client nie die SMB-Paketsignatur aus.
- **Kommunikation digital signieren (immer)**: Bestimmt, ob die SMB-Serverkomponente die Paketsignatur erfordert. Wenn aktiviert, kommuniziert der Microsoft-Netzwerkserver nur dann mit einem Microsoft-Netzwerkclient, wenn dieser der Ausführung der SMB-Paketsignatur zustimmt. Wenn deaktiviert (Standard), wird die SMB-Paketsignatur zwischen Client und Server ausgehandelt.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Zuweisen dieses Profils an Gruppen finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).
