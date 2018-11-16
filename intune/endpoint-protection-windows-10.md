---
title: Hinzufügen von Endpoint Protection mit Windows 10 in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Verwenden oder konfigurieren Sie Einstellungen zu Endpoint Protection auf Windows 10-Geräten, um das Feature Windows Defender zu aktivieren, das Application Guard, Firewall, SmartScreen, Verschlüsselung und BitLocker, Exploit Guard, Anwendungssteuerung, Security Center und Sicherheit auf lokalen Geräten in Microsoft Intune enthält.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a7c7ebca1c6472b58021a57b1b4a59fc42966b0
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576952"
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Endpoint Protection-Einstellungen für Windows 10 und höher in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Mit dem Endpoint Protection-Profil können Sie Sicherheitsfeatures auf Windows 10-Geräten steuern, z.B. BitLocker und Windows Defender.

Verwenden Sie die Informationen in diesem Artikel, um Endpoint Protection-Profile zu erstellen. Informationen zum Konfigurieren von Windows Defender Antivirus finden Sie unter [Windows 10-Geräteeinschränkungen](device-restrictions-windows-10.md#windows-defender-antivirus). 

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Enterprise 
- Professional

Bei der Verwendung von Microsoft Edge schützt Windows Defender Application Guard Ihre Umgebung vor Websites, die von Ihrer Organisation nicht als vertrauenswürdig definiert wurden. Wenn Benutzer Websites besuchen, die nicht in Ihrer isolierten Netzwerkgrenze aufgelistet sind, werden die Websites in einer virtuellen Hyper-V-Browsersitzung geöffnet. Vertrauenswürdige Websites werden durch eine Netzwerkgrenze definiert, die in der Gerätekonfiguration konfiguriert werden kann.

Application Guard ist nur für Windows 10-Geräte (64-Bit) verfügbar. Mithilfe dieses Profils wird eine Win32-Komponente zur Aktivierung von Application Guard installiert.

- **Application Guard:** Legen Sie diese Einstellung auf **Aktivieren** fest, um dieses Feature zu aktivieren. Dadurch werden nicht genehmigte Websites in einem virtualisierten Hyper-V-Browsercontainer geöffnet. **Nicht konfiguriert** (Standardeinstellung) bedeutet, dass jede Website (genehmigt und nicht genehmigt) auf dem Gerät geöffnet wird.
- **Verhalten der Zwischenablage**: Legen Sie zulässige Aktionen für das Kopieren und Einfügen zwischen dem lokalen Computer und dem virtuellen Browser von Application Guard fest.
- **Externer Inhalt auf Unternehmenswebsites:** Legen Sie diese Einstellung auf **Blockieren** fest, damit keine Inhalte von nicht genehmigten Websites geladen werden. **Nicht konfiguriert** (Standardeinstellung) bedeutet, dass Websites, bei denen es sich nicht um Unternehmenswebsites handelt, auf dem Gerät geöffnet werden können.
- **Aus virtuellem Browser drucken:** Legen Sie diese Einstellung auf **Zulassen** fest, damit PDF-Drucker, XPS-Drucker, lokale Drucker und/oder Netzwerkdrucker Inhalte aus dem virtuellen Browser drucken können. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden alle Druckfunktionen deaktiviert.
- **Protokolle speichern:** Legen Sie diese Einstellung auf **Zulassen** fest, damit Protokolle für Ereignisse gespeichert werden, die während einer Browsersitzung von Application Guard auftreten. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden keine Protokolle während einer Browsersitzung gespeichert.
- **Benutzergenerierte Browserdaten beibehalten:** Legen Sie diese Einstellung auf **Zulassen** fest, damit Benutzerdaten (z.B. Kennwörter, Favoriten und Cookies) gespeichert werden, die während einer virtuellen Browsersitzung von Application Guard erstellt werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden vom Benutzer heruntergeladene Dateien und Daten gelöscht, wenn das Gerät neu gestartet wird oder ein Benutzer sich abmeldet.
- **Grafikbeschleunigung:** Legen Sie diese Einstellung auf **Aktivieren** fest, um grafisch anspruchsvolle Websites und Videos schneller zu laden, indem der Zugriff auf einen virtuellen Grafikprozessor gewährt wird. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird nur die CPU des Geräts (d.h. kein virtueller Grafikprozessor) für Grafiken verwendet.
- **Dateien auf Hostdateisystem herunterladen:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit Benutzer Dateien aus dem virtualisierten Browser auf das Hostbetriebssystem herunterladen können. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Dateien lokal auf dem Gerät gespeichert, und es werden keine Dateien auf das Hostdateisystem heruntergeladen.

## <a name="windows-defender-firewall"></a>Windows Defender Firewall

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:
- Startseite
- Professional
- Business
- Enterprise
- Education
- Handy
- Mobile Enterprise

### <a name="global-settings"></a>Globale Einstellungen

Diese Einstellungen können auf alle Netzwerktypen angewendet werden.

- **File Transfer Protocol:** Legen Sie diese Einstellung auf **Blockieren** fest, um statusbehaftetes FTP zu deaktivieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, filtert die Firewall statusbehaftetes FTP, um sekundäre Verbindungen zu ermöglichen.
- **Leerlaufzeit für Sicherheitszuordnung vor Löschvorgang**: Sicherheitszuordnungen werden gelöscht, wenn für *n* Sekunden kein Netzwerkdatenverkehr erkannt wird. Geben Sie eine Leerlaufzeit in Sekunden an.
- **Codierung vorinstallierter Schlüssel:** Legen Sie diese Einstellung auf **Aktivieren** fest, um die Codierung vorinstallierter Schlüssel mithilfe von UTF-8 zu verwenden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der lokal gespeicherte Wert verwendet.
- **IPsec-Ausnahmen:** Diese Konfiguration legt fest, ob bestimmter Datenverkehr von IPsec ausgenommen werden soll, einschließlich Folgendem:
  - **Neighbor Discovery-IPv6-Codes vom Typ ICMP**
  - **ICMP**
  - **Router Discovery-IPv6-Codes vom Typ ICMP**
  - **IPv4- und IPv6-DHCP-Netzwerkdatenverkehr**
- **Überprüfung der Zertifikatssperrliste:** Bestimmt, wie die Überprüfung der Zertifikatssperrliste erzwungen wird, einschließlich **Überprüfung der Zertifikatssperrliste deaktivieren**, **Überprüfung der Zertifikatssperrliste nur bei gesperrtem Zertifikat fehlerhaft** und **Überprüfung der Zertifikatssperrliste bei jedem Fehler fehlerhaft**.
- **Authentifizierungssatz opportunistisch pro Schlüsselerstellungsmodul abgleichen:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit Schlüsselerstellungsmodule nur die Authentifizierungssuites ignorieren müssen, die sie nicht unterstützen. Mit der Einstellung **Nicht konfiguriert** müssen Schlüsselerstellungsmodule den gesamten Authentifizierungssatz ignorieren, wenn sie nicht alle Authentifizierungssuites unterstützen, die im Satz angegeben sind.
- **Paketwarteschlangen**: Legen Sie fest, wie die Skalierung für die Software auf der Empfangsseite für den verschlüsselten Empfang und die Weiterleitung im Klartext für das IPsec-Tunnelgatewayszenario aktiviert wird. Durch diese Einstellung wird die Paketreihenfolge beibehalten.

### <a name="network-settings"></a>Netzwerkeinstellungen

Diese Einstellungen gelten für bestimmte Netzwerktypen, einschließlich **Domänennetzwerk (Arbeitsplatz)**, **Privates Netzwerk (sichtbar)** und **Öffentliches Netzwerk (nicht sichtbar)**.

#### <a name="general-settings"></a>Allgemeine Einstellungen

- **Windows Defender Firewall:** Legen Sie diese Einstellung auf **Aktivieren** fest, um die Firewall und die erweiterte Sicherheit zu aktivieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird sämtlicher Netzwerkdatenverkehr unabhängig von anderen Richtlinieneinstellungen zugelassen.
- **Geschützter Modus:** Legen Sie diese Einstellung auf **Blockieren** fest, damit die Firewall nicht im geschützten Modus ausgeführt werden kann. Wenn Sie den geschützten Modus blockieren, ermöglichen Sie ebenfalls das Blockieren von **durch IPsec gesicherten Paketausnahmen**. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird die Firewall im geschützten Modus ausgeführt. Dadurch werden Antworten auf Suchanforderungen verhindert.
- **Geschützt:** Legen Sie diese Einstellung auf **Blockieren** fest, um dieses Feature zu deaktivieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird diese Einstellung aktiviert. Wenn diese Einstellung und Windows Defender Firewall aktiviert sind, wird sämtlicher eingehender Datenverkehr unabhängig von anderen Richtlinieneinstellungen blockiert.
- **Unicastantworten auf Multicastbroadcasts:** Wenn diese Einstellung auf **Blockieren** festgelegt ist, werden Unicastantworten auf Multicastbroadcasts deaktiviert. Sie möchten wohl keine Unicastantworten auf Multicast- oder Broadcastmeldungen empfangen. Diese Antworten können auf einen DoS-Angriff (Denial of Service) hinweisen, oder einen Angreifer, der versucht, einen bekanntermaßen aktiven Computer zu testen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird diese Einstellung aktiviert.
- **Eingehende Benachrichtigungen:** Wenn diese Einstellung auf **Blockieren** festgelegt ist, werden Benachrichtigungen für Benutzer ausgeblendet, wenn eine App für das Lauschen auf einen Port blockiert ist. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird die Einstellung aktiviert, und Benutzern werden Benachrichtigungen angezeigt, wenn eine App für das Lauschen auf einen Port blockiert ist.
- **Standardaktion für eingehende Verbindungen:** Wenn diese Einstellung auf **Blockieren** festgelegt ist, wird die Standardaktion der Firewall nicht für eingehende Verbindungen ausgeführt. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird die Standardaktion der Firewall für eingehende Verbindungen ausgeführt.

#### <a name="rule-merging"></a>Regelzusammenführung

- **Windows Defender Firewall-Regeln für autorisierte Anwendungen aus dem lokalen Speicher:** Legen Sie diese Einstellung auf **Aktivieren** fest, wenn die Firewallregeln im lokalen Speicher erkannt und erzwungen werden sollen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Firewallregeln für autorisierte Anwendungen im lokalen Speicher ignoriert und nicht erzwungen.
- **Windows Defender Firewall-Regeln für den globalen Port aus dem lokalen Speicher:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit die Firewallregeln für den globalen Port im lokalen Speicher erkannt und erzwungen werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Firewallregeln für den globalen Port im lokalen Speicher ignoriert und nicht erzwungen.
- **Windows Defender Firewall-Regeln aus dem lokalen Speicher:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit Firewallregeln im lokalen Speicher erkannt und erzwungen werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Firewallregeln im lokalen Speicher ignoriert und nicht erzwungen.
- **IPsec-Regeln aus dem lokalen Speicher:** Legen Sie diese Einstellung auf **Aktivieren** fest, um Verbindungssicherheitsregeln aus dem lokalen Speicher anzuwenden, die unabhängig vom Schema oder den Versionen der Verbindungssicherheitsregeln gelten. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Verbindungssicherheitsregeln im lokalen Speicher unabhängig von der Schemaversion und der Version der Verbindungssicherheitsregeln ignoriert und nicht erzwungen.

## <a name="windows-defender-smartscreen-settings"></a>Einstellungen für Windows Defender SmartScreen

Dieses Feature wird in folgenden Windows 10-Editionen unterstützt, für die Microsoft Edge installiert ist:
- Startseite
- Professional
- Business
- Enterprise
- Education
- Handy
- Mobile Enterprise

**Einstellungen:**

- **SmartScreen für Apps und Dateien:** Legen Sie diese Einstellung auf **Aktivieren** fest, um Windows SmartScreen für die Datei- und App-Ausführung zu aktivieren. SmartScreen ist eine cloudbasierte Komponente gegen Phishing- und Schadsoftware. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird SmartScreen deaktiviert.
- **Ausführung nicht überprüfter Dateien:** Legen Sie diese Einstellung auf **Blockieren** fest, um die Ausführung von Dateien durch den Benutzer zu sperren, die nicht durch Windows SmartScreen überprüft wurden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden diese Features deaktiviert, sodass Endbenutzer keine Dateien ausführen können, die nicht überprüft wurden.

## <a name="windows-encryption"></a>Windows-Verschlüsselung

### <a name="windows-settings"></a>Windows-Einstellungen

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Professional
- Business
- Enterprise
- Education
- Handy
- Mobile Enterprise

**Einstellungen:**

- **Geräte verschlüsseln:** Legen Sie diese Einstellung auf **Erforderlich** fest, um Benutzer dazu aufzufordern, die Geräteverschlüsselung zu aktivieren. Je nach Windows-Edition und Systemkonfiguration können Benutzer zu Folgendem aufgefordert werden:  
  - Zur Bestätigung, dass keine Verschlüsselung eines anderen Anbieters aktiviert ist
  - Zum Deaktivieren der BitLocker-Laufwerksverschlüsselung und zum anschließenden Aktivieren von BitLocker
    
    Wenn die Windows-Verschlüsselung eingeschaltet wird, während eine andere Verschlüsselungsmethode aktiv ist, wird das Gerät möglicherweise instabil. 
- **Speicherkarte verschlüsseln (nur mobil):** Legen Sie diese Einstellung auf **Erforderlich** fest, um alle vom Gerät verwendeten wechselbaren Speicherkarten zu verschlüsseln. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, ist keine Speicherkartenverschlüsselung erforderlich, und der Benutzer wird nicht dazu aufgefordert, diese zu aktivieren. Diese Einstellung gilt nur für Windows 10 Mobile-Geräte.

### <a name="bitlocker-base-settings"></a>BitLocker-Grundeinstellungen

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Enterprise
- Education
- Handy
- Mobile Enterprise

Bei den Grundeinstellungen handelt es sich um universelle BitLocker-Einstellungen, die für alle Typen von Datenträgern gelten. Durch diese Einstellungen wird verwaltet, welche Aufgaben für die Laufwerkverschlüsselung oder Konfigurationsoptionen der Benutzer auf allen Typen von Laufwerken ändern kann.

- **Warnung zu anderer Datenträgerverschlüsselung:** Legen Sie diese Einstellung auf **Blockieren** fest, um die Warnung zu deaktivieren, die angezeigt wird, wenn ein anderer Dienst zur Datenträgerverschlüsselung auf dem Gerät vorhanden ist. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird diese Warnung angezeigt.
- **Verschlüsselungsmethoden konfigurieren:** **Aktivieren** Sie diese Einstellung, um Verschlüsselungsalgorithmen für Betriebssystem-, Daten- und Wechseldatenträger zu konfigurieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, verwendet BitLocker XTS-AES 128-Bit als Standardverschlüsselungsmethode oder die Verschlüsselungsmethode, die von einem Setupskript festgelegt wird.
  - **Verschlüsselung für Betriebssystemlaufwerke**: Wählen Sie die Verschlüsselungsmethode für Betriebssystemlaufwerke aus. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.
  - **Verschlüsselung für Festplattenlaufwerke**: Wählen Sie die Verschlüsselungsmethode für Festplattenlaufwerke (integriert) aus. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.
  - **Verschlüsselung für Wechseldatenträger**: Wählen Sie die Verschlüsselungsmethode für Wechseldatenträger aus. Wenn der Wechseldatenträger mit Geräten verwendet wird, auf denen nicht Windows 10 ausgeführt wird, wird empfohlen, den AES-CBC-Algorithmus zu verwenden.

### <a name="bitlocker-os-drive-settings"></a>Einstellung für BitLocker-OS-Datenträger
Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Enterprise
- Education
- Handy
- Mobile Enterprise

Diese Einstellungen gelten speziell für Betriebssystemlaufwerke.

- **Zusätzliche Authentifizierung beim Start:** Legen Sie diese Einstellung auf **Erforderlich** fest, um die Authentifizierungsanforderungen für den Computerstart zu konfigurieren, einschließlich der Verwendung von Trusted Platform Module (TPM). Legen Sie die Standardeinstellung **Nicht konfiguriert** fest, um nur grundlegende Optionen auf Geräten mit einem TPM zu konfigurieren.
  - **BitLocker mit nicht kompatiblem TPM-Chip:** Legen Sie diese Einstellung auf **Blockieren** (Deaktivieren) fest, um die Verwendung von BitLocker zu blockieren, wenn ein Gerät nicht über einen kompatiblen TPM-Chip verfügt. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer BitLocker ohne kompatiblen TPM-Chip verwenden. BitLocker kann ein Kennwort oder einen Systemstartschlüssel erfordern.
  - **Systemstart für kompatibles TPM**: Legen Sie fest, ob der TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist.
  - **Systemstart-PIN für kompatibles TPM**: Legen Sie fest, ob mit dem TPM-Chip eine Systemstart-PIN zugelassen, nicht zugelassen oder erforderlich ist. Für das Aktivieren einer Systemstart-PIN ist ein Eingreifen des Endbenutzers erforderlich. 
  - **Systemstartschlüssel für kompatibles TPM**: Legen Sie fest, ob die Verwendung eines Systemstartschlüssels mit dem TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist. Für das Aktivieren eines Systemstartschlüssels ist ein Eingreifen des Endbenutzers erforderlich. 
  - **Systemstartschlüssel und Systemstart-PIN für kompatibles TPM**: Legen Sie fest, ob die Verwendung eines Systemstartschlüssels und einer PIN mit dem TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist. Für das Aktivieren eines Systemstartschlüssels und einer Systemstart-PIN ist ein Eingreifen des Endbenutzers erforderlich.
- **PIN-Mindestlänge:** Wenn diese Einstellung **aktiviert** ist, können Sie eine Mindestlänge für die TPM-Systemstart-PIN festlegen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer eine Systemstart-PIN zwischen 6 und 20 Ziffern konfigurieren.
  - **Mindestanzahl von Zeichen**: Geben Sie die Zahl an Zeichen (**4**-**20**) an, die für die Systemstart-PIN erforderlich sind.
- **Wiederherstellung von Betriebssystemlaufwerken:** Wenn diese Einstellung auf **Aktivieren** festgelegt ist, können Sie steuern, wie durch BitLocker geschützte Betriebssystemdatenträger wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht verfügbar sind. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Standardwiederherstellungsoptionen für die BitLocker-Wiederherstellung unterstützt. Standardmäßig ist DRA zulässig, die Wiederherstellungsoptionen (einschließlich Wiederherstellungskennwort und -schlüssel) werden vom Benutzer angegeben, und Wiederherstellungsinformationen werden nicht in AD DS gesichert.
  - **Zertifikatbasierter Datenwiederherstellungs-Agent:** Wenn diese Einstellung auf **Blockieren** festgelegt ist, können Sie keinen Datenwiederherstellungs-Agent auf durch BitLocker geschützten Betriebssystemlaufwerken verwenden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, um diese Einstellung zu aktivieren, können Datenwiederherstellungs-Agents mit durch BitLocker geschützten Betriebssystemlaufwerken verwendet werden.
  - **Erstellung des Wiederherstellungskennworts durch den Benutzer**: Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.
  - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**: Legen Sie fest, ob Benutzer einen 256-Bit-Wiederherstellungsschlüssel generieren dürfen oder müssen.
  - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten:** Legen Sie diese Einstellung auf **Blockieren** fest, damit Benutzer die Wiederherstellungsoptionen nicht anzeigen oder ändern können. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer die Wiederherstellungsoptionen anzeigen und ändern, wenn sie BitLocker aktivieren.
  - **BitLocker-Wiederherstellungsinformationen in AD DS speichern:** Legen Sie diese Einstellung auf **Aktivieren** fest, um die BitLocker-Wiederherstellungsinformationen in Azure Active Directory (AAD) zu speichern. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Wiederherstellungsinformationen nicht in AAD gespeichert.
  - **In AD DS gespeicherte BitLocker-Wiederherstellungsinformationen:** Konfiguriert, welche BitLocker-Wiederherstellungsinformationen in Azure AD gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:
    - **Wiederherstellungskennwörter und Schlüsselpakete sichern**
    - **Nur Wiederherstellungskennwörter sichern**
  - **Wiederherstellungsinformationen vor dem Aktivieren von BitLocker in AD DS speichern:** Legen Sie diese Einstellung auf **Erforderlich** fest, um zu verhindern, dass Benutzer BitLocker aktivieren, es sei denn, das Gerät ist mit einer Domäne verbunden und BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Active Directory gespeichert. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer BitLocker aktivieren, auch wenn die Wiederherstellungsinformationen nicht erfolgreich in Azure Active Directory gespeichert sind.
- **Pre-Boot-Wiederherstellungsmeldung und -URL:** **Aktivieren** Sie diese Einstellung, um die Meldung und URL zu konfigurieren, die auf dem Bildschirm der Pre-Boot-Schlüsselwiederherstellung angezeigt werden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird dieses Feature deaktiviert.
  - **Pre-Boot-Wiederherstellungsmeldung**: Legen Sie fest, wie die Pre-Boot-Wiederherstellungsmeldung Benutzern angezeigt wird. Es stehen die folgenden Optionen zur Auswahl:
    - **Standardmäßige Wiederherstellungsmeldung und -URL verwenden**
    - **Leere Wiederherstellungsmeldung und -URL verwenden**
    - **Benutzerdefinierte Wiederherstellungsmeldung**
    - **Benutzerdefinierte Wiederherstellungs-URL**

### <a name="bitlocker-fixed-data-drive-settings"></a>Einstellungen für das BitLocker-Festplattenlaufwerk

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Enterprise
- Education
- Handy
- Mobile Enterprise

**Einstellungen:**

- **Schreibzugriff auf nicht durch BitLocker geschützte Festplattenlaufwerke:** Legen Sie diese Einstellung auf **Blockieren** fest, um Laufwerken, die nicht durch BitLocker geschützt werden, schreibgeschützten Zugriff zu gewähren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, haben nicht durch BitLocker geschützte Datenträger Lese- und Schreibzugriff.
- **Wiederherstellung von Festplattenlaufwerken:** **Aktivieren** Sie diese Einstellung, um zu steuern, wie durch BitLocker geschützte Festplattenlaufwerke wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht vorliegen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird dieses Feature deaktiviert.
  - **Datenwiederherstellungs-Agent:** Legen Sie diese Einstellung auf **Blockieren** fest, um die Verwendung des Datenwiederherstellungs-Agents auf durch BitLocker geschützten Festplattenlaufwerken zu blockieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Datenwiederherstellungs-Agents auf durch BitLocker geschützten Festplattenlaufwerken verwendet werden.
  - **Erstellung des Wiederherstellungskennworts durch den Benutzer**: Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.  
  - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**: Legen Sie fest, ob Benutzer einen 256-Bit-Wiederherstellungsschlüssel generieren dürfen oder müssen.
  - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten:** Legen Sie diese Einstellung auf **Blockieren** fest, damit Benutzer die Wiederherstellungsoptionen nicht anzeigen oder ändern können. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer die Wiederherstellungsoptionen anzeigen und ändern, wenn sie BitLocker aktivieren.
  - **BitLocker-Wiederherstellungsinformationen in AD DS speichern:** Legen Sie diese Einstellung auf **Aktivieren** fest, um die BitLocker-Wiederherstellungsinformationen in Azure Active Directory (AAD) zu speichern. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Wiederherstellungsinformationen nicht in AAD gespeichert.
  - **BitLocker-Wiederherstellungsinformationen in AD DS:** Konfiguriert, welche BitLocker-Wiederherstellungsinformationen in Azure Active Directory gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:
    - **Wiederherstellungskennwörter und Schlüsselpakete sichern**
    - **Nur Wiederherstellungskennwörter sichern**
  - **Wiederherstellungsinformationen vor dem Aktivieren von BitLocker in AD DS speichern:** Legen Sie diese Einstellung auf **Erforderlich** fest, um zu verhindern, dass Benutzer BitLocker aktivieren, es sei denn, das Gerät ist mit einer Domäne verbunden und BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Active Directory gespeichert. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer BitLocker aktivieren, auch wenn die Wiederherstellungsinformationen nicht erfolgreich in Azure Active Directory gespeichert sind.

### <a name="bitlocker-removable-data-drive-settings"></a>Einstellungen für den BitLocker-Wechseldatenträger

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Enterprise
- Education
- Handy
- Mobile Enterprise

**Einstellungen:**

- **Schreibzugriff auf nicht durch BitLocker geschützte Wechseldatenträger:** Legen Sie diese Einstellung auf **Blockieren** fest, um Datenträgern, die nicht durch BitLocker geschützt werden, schreibgeschützten Zugriff zu gewähren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, haben nicht durch BitLocker geschützte Datenträger Lese- und Schreibzugriff.
  - **Schreibzugriff auf in einer anderen Organisation konfigurierte Geräte:** Legen Sie die Einstellung auf **Blockieren** fest, um in einer anderen Organisation konfigurierten Geräten den Schreibzugriff zu verweigern. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der Schreibzugriff zugelassen.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Startseite
- Professional
- Business
- Enterprise
- Education
- Handy
- Mobile Enterprise

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

Erstellen Sie zum Aktivieren des Exploit-Schutzes eine XML-Datei, die die gewünschten Einstellungen zur Risikominderung für System und Anwendungen enthält. Es gibt zwei Methoden:

 1. PowerShell: Verwenden Sie mindestens eines der PowerShell-Cmdlets Get-ProcessMitigation, Set-ProcessMitigation und ConvertTo-ProcessMitigationPolicy. Die Cmdlets konfigurieren Einstellungen zur Risikominderung und exportieren eine XML-Darstellung von ihnen.

 2. Windows Defender Security Center-Benutzeroberfläche: Klicken Sie im Windows Defender Security Center auf „App > Browsersteuerung“, und scrollen Sie zum Ende des entsprechenden Bildschirms, um den Exploit-Schutz zu finden. Verwenden Sie zuerst die Registerkarten „Systemeinstellungen“ und „Programmeinstellungen“, um die Einstellungen für die Risikominderung zu konfigurieren. Suchen Sie anschließend den Link mit den Exporteinstellungen im unteren Bildschirmbereich, um eine XML-Darstellung zu exportieren.

Blockieren Sie die **Bearbeitung der Exploit-Schutzumgebung durch Benutzer**, indem Sie eine XML-Datei hochladen, die Ihnen das Konfigurieren von Speicher-, Ablaufsteuerungs- und Richtlinieneinschränkungen ermöglicht. Die Einstellungen in der XML-Datei können eine Anwendung vor Exploits schützen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden benutzerdefinierte Konfigurationen nicht blockiert. 

## <a name="windows-defender-application-control"></a>Windows Defender Application Control

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

**Mobile Geräteverwaltung (MDM):** 
- Professional
- Business
- Enterprise
- Education
- Handy
- Mobile Enterprise

**Gruppenrichtlinienverwaltung:** 
- Enterprise

Verwenden Sie die **Anwendungssteuerungscode-Integritätsrichtlinien**, um zusätzliche Apps auszuwählen, die durch Windows Defender Application Control überwacht werden oder als vertrauenswürdig eingestuft und ausgeführt werden. Windows-Komponenten und alle Apps aus dem Windows Store werden automatisch als zur Ausführung vertrauenswürdig eingestuft.

Anwendungen werden nicht blockiert, wenn sie im Modus **Nur überwachen** ausgeführt werden. Der Modus **Nur überwachen** protokolliert alle Ereignisse in lokalen Clientprotokollen.

Sobald die Anwendungssteuerung aktiviert ist, kann sie nur noch deaktiviert werden, indem der Modus von **Erzwingen** in **Nur überwachen** geändert wird. Wenn der Modus von **Erzwingen** in **Nicht konfiguriert** geändert wird, wird die Anwendungssteuerung weiterhin auf zugewiesenen Geräten erzwungen.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Enterprise

Windows Defender Credential Guard schützt vor Angriffen zum Diebstahl von Anmeldeinformationen. Geheime Schlüssel werden isoliert, damit nur privilegierte Systemsoftware darauf zugreifen kann.

Die **Credential Guard** Einstellungen beinhalten:

- **Deaktivieren:** Deaktiviert Credential Guard per Remoteverbindung, wenn das Programm zuvor über die Option **Ohne UEFI-Sperre aktivieren** aktiviert wurde.

- **Mit UEFI-Sperre aktivieren:** Credential Guard kann nicht remote mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden.

    > [!NOTE]
    > Wenn Sie diese Einstellung verwenden und dann später Credential Guard deaktivieren möchten, müssen Sie die Gruppenrichtlinie auf **Deaktiviert** setzen. Außerdem müssen Sie die UEFI-Konfigurationsinformationen physisch von den einzelnen Computern löschen. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.

- **Ohne UEFI-Sperre aktivieren:** Ermöglicht, Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie zu deaktivieren. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.

Wenn Sie Credential Guard aktivieren, werden auch die folgenden erforderlichen Features aktiviert:

- **Virtualisierungsbasierte Sicherheit** (VBS): Wird beim nächsten Neustart aktiviert. Virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen.
- **Sicherer Start mit direktem Speicherzugriff**: Aktiviert VBS mit Schutzmaßnahmen wie sicherem Start und direktem Speicherzugriff (Direct Memory Access, DMA). Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf richtig konfigurierten Geräten aktiviert.

## <a name="windows-defender-security-center"></a>Windows Defender Security Center

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:

- Startseite
- Professional
- Business
- Enterprise
- Education
- Handy
- Mobile Enterprise

Windows Defender Security Center fungiert als von den einzelnen Features separate App bzw. separater Prozess. Sie zeigt Benachrichtigungen über das Info-Center an. Sie dienst als Collector oder zentraler Ort, um den Status anzuzeigen und Konfigurationen für die verschiedenen Features durchzuführen. Weitere Informationen finden Sie in den Dokumenten zu [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Windows Defender Security Center-App und -Benachrichtigungen

Blockieren Sie den Benutzerzugriff auf die verschiedenen Bereiche der Windows Defender Security Center-App. Durch das Ausblenden eines Abschnitts werden auch die zugehörigen Benachrichtigungen blockiert.

- **Viren- und Bedrohungsschutz**
- **Geräteleistung und -integrität**
- **Firewall- und Netzwerkschutz**
- **App- und Browsersteuerung**
- **Familienoptionen**
- **Benachrichtigungen aus den angezeigten Bereichen der App**: Legen Sie fest, welche Benachrichtigungen dem Benutzer angezeigt werden sollen. Zu den nicht kritische Benachrichtigungen gehören Zusammenfassungen der Aktivitäten von Windows Defender Antivirus, Benachrichtigungen zum Abschluss von Überprüfungen eingeschlossen. Alle übrigen Benachrichtigungen gelten als kritisch.

#### <a name="it-contact-information"></a>IT-Kontaktinformationen

Stellen Sie IT-Kontaktinformationen bereit, die in der Windows Defender Security Center-App und in den App-Benachrichtigungen angezeigt werden. Sie können **In Apps und Benachrichtigungen anzeigen**, **Nur in App anzeigen**, **Nur in Benachrichtigungen anzeigen** oder **Don‘t display** (Nicht anzeigen) auswählen. Geben Sie den **Namen der IT-Organisation** und mindestens eine der folgenden Kontaktoptionen ein:

- **Telefonnummer oder Skype-ID der IT-Abteilung**
- **E-Mail-Adresse der IT-Abteilung**
- **URL der IT-Supportwebsite**

## <a name="local-device-security-options"></a>Sicherheitsoptionen für lokale Geräte

Dieses Feature wird auf folgenden Windows 10-Editionen unterstützt:
 
- Startseite
- Professional
- Business
- Enterprise
- Education

Konfigurieren Sie mit diesen Optionen die lokalen Sicherheitseinstellungen auf Windows 10-Geräten.

### <a name="accounts"></a>Konten

- **Neue Microsoft-Konten hinzufügen:** Legen Sie diese Einstellung auf **Blockieren** fest, damit Benutzer diesem Computer keine neuen Microsoft-Konten hinzufügen können. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer Microsoft-Konten auf dem Gerät verwenden.
- **Remoteanmeldung ohne Kennwort:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit lokale Konten ohne Kennwörter über die Tastatur des Geräts angemeldet werden können. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können lokale Konten ohne Kennwort sich auch von anderen Standorten als dem physischen Gerät aus anmelden.

#### <a name="admin"></a>Administrator

- **Lokales Administratorkonto:** Legen Sie diese Einstellung auf **Aktiviert** fest, um das lokale Administratorkonto zuzulassen. Legen Sie die Standardeinstellung **Nicht konfiguriert** fest, um das lokale Administratorkonto zu deaktivieren.
- **Administratorkonto umbenennen**: Definieren Sie einen anderen Kontonamen, der der Sicherheits-ID (SID) für das Administratorkonto zugeordnet werden soll.

#### <a name="guest"></a>Gast

- **Gastkonto:** Legen Sie diese Einstellung auf **Aktiviert** fest, um das lokale Gastkonto zuzulassen. Legen Sie die Standardeinstellung **Nicht konfiguriert** fest, um das lokale Gastkonto zu deaktivieren.
- **Gastkonto umbenennen**: Definieren Sie einen anderen Kontonamen, der der Sicherheits-ID (SID) für das Gastkonto zugeordnet werden soll.

### <a name="devices"></a>Geräte

- **Gerät ohne Anmeldung abdocken:** Legen Sie diese Einstellung auf **Blockieren** fest, damit Benutzer auf die physische Schaltfläche zum Auswerfen eines angedockten portablen Geräts drücken können, um dieses abzudocken. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, muss der Benutzer sich beim Gerät anmelden und die Berechtigung dafür erhalten, das Gerät abzudocken.
- **Druckertreiber für freigegebene Drucker installieren:** Wenn diese Einstellung auf **Aktiviert** festgelegt ist, können alle Benutzer einen Druckertreiber installieren, wenn sie eine Verbindung mit einem freigegebenen Drucker herstellen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können nur Administratoren einen Druckertreiber installieren, wenn sie eine Verbindung mit einem freigegebenen Drucker herstellen.
- **CD-ROM-Zugriff auf lokal aktiven Benutzer beschränken:** Wenn diese Einstellung auf **Aktiviert** festgelegt ist, kann nur der interaktiv angemeldete Benutzer CD-ROM-Medien verwenden. Wenn diese Richtlinie aktiviert ist und kein Benutzer interaktiv angemeldet ist, wird über das Netzwerk auf die CD-ROM zugegriffen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, kann jeder Benutzer auf die CD-ROM zugreifen.
- **Wechselmedien formatieren und auswerfen**: Definieren Sie, wer NTFS-Wechselmedien formatieren und auswerfen darf:
  - **Nicht konfiguriert**
  - **Administratoren**
  - **Administratoren und Poweruser**
  - **Administratoren und interaktive Benutzer**

### <a name="interactive-logon"></a>Interaktive Anmeldung

- **Inaktivität in Minuten für Anmeldebildschirm bis zur Aktivierung des Bildschirmschoners:** Geben Sie die maximale Anzahl von Minuten der Inaktivität auf dem Anmeldebildschirm des interaktiven Desktops ein, bis der Bildschirmschoner ausgeführt wird.
- **STRG+ALT+ENTF zur Anmeldung voraussetzen:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit Benutzer STRG+ALT+ENTF drücken müssen, um sich anzumelden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, müssen Benutzer nicht STRG+ALT+ENTF drücken, bevor sie sich bei Windows anmelden.
- **Verhalten beim Entfernen von Smartcards**: Bestimmt, was geschieht, wenn die Smartcard für einen angemeldeten Benutzer aus den Smartkartenleser entfernt wird. Folgende Optionen sind verfügbar:

  - **Arbeitsstation sperren:** Die Arbeitsstation wird gesperrt, wenn die Smartcard entfernt wird. Diese Option ermöglicht es dem Benutzer, den Bereich zu verlassen, die Smartcard mitzunehmen und dennoch eine geschützte Sitzung beizubehalten.
  - **Abmeldung erzwingen:** Der Benutzer wird automatisch abgemeldet, wenn die Smartcard entfernt wird.
  - **Disconnect if a Remote Desktop Services session** (Verbindung bei einer Remotedesktopdienste-Sitzung trennen): Das Entfernen der Smartcard beendet die Sitzung, ohne den Benutzer abzumelden. Diese Option ermöglicht es dem Benutzer, die Smartcard einzulegen und die Sitzung später oder auf einem anderen Computer mit Smartcard-Leser fortzusetzen, ohne sich erneut anmelden zu müssen. Wenn die Sitzung lokal stattfindet, funktioniert diese Richtlinie genau wie „Arbeitsstation sperren“.

    [LocalPoliciesSecurity-Optionen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) enthalten weitere Details.

#### <a name="display"></a>Anzeige

- **Benutzerinformationen auf Sperrbildschirm**: Konfigurieren Sie die Benutzerinformationen, die angezeigt werden, wenn die Sitzung gesperrt ist. Wenn nicht konfiguriert, werden Anzeigename des Benutzers, Domäne und Benutzername angezeigt.
  - **Nicht konfiguriert**
  - **Anzeigename des Benutzers, Domäne und Benutzername**
  - **Nur Anzeigename des Benutzers**
  - **Benutzerinformationen nicht anzeigen**
- **Zuletzt angemeldeten Benutzer ausblenden:** Legen Sie diese Einstellung auf **Aktiviert** fest, um den Benutzernamen auszublenden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der Benutzername angezeigt.
- **Benutzernamen bei der Anmeldung ausblenden:** Legen Sie diese Einstellung auf **Aktiviert** fest, um den Benutzernamen auszublenden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der Benutzername angezeigt.
- **Anmeldemeldungstitel:** Legen Sie den Meldungstitel für Benutzer fest, die sich anmelden.
- **Anmeldemeldungstext:** Legen Sie den Meldungstext für Benutzer fest, die sich anmelden.

### <a name="network-access-and-security"></a>Netzwerkzugriff und Sicherheit

- **Anonymer Zugriff auf Named Pipes und Freigaben:** **Nicht konfiguriert** (Standard) Schränkt den anonymen Zugriff auf Freigabe- und Named Pipe-Einstellungen ein. Gilt für die Einstellungen, auf die anonym zugegriffen werden kann.
- **Anonyme Auflistung von SAM-Konten:** **Lässt zu**, dass anonyme Benutzer die SAM-Konten auflisten. Windows ermöglicht anonymen Benutzern, die Namen von Domänenkonten und Netzwerkfreigaben aufzuzählen.
- **Anonyme Auflistung von SAM-Konten und -Freigaben:** **Nicht konfiguriert** (Standard) Dies bedeutet, dass anonyme Benutzer die Namen der Domänenkonten und Netzwerkfreigaben auflisten können. Wenn Sie die anonyme Auflistung von SAM-Konten und Freigaben verhindern möchten, legen Sie **Blockieren** fest.
- **LAN-Manager-Hashwert bei Kennwortänderung speichern**: Wählen Sie, ob bei der nächsten Kennwortänderung **zugelassen** wird, dass der LAN-Manager-Hashwert (LM) den Hashwert für das neue Kennwort speichert. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der Hashwert nicht gespeichert.
- **PKU2U-Authentifizierungsanforderungen:** **Blockiert** an das Gerät gerichtete PKU2U-Authentifizierungsanforderungen, damit Onlineidentitäten verwendet werden. Durch **Nicht konfiguriert** (Standard) werden diese Anforderungen zugelassen.
- **RPC-Remoteverbindungen mit SAM einschränken:** **Lassen Sie die Security Descriptor Definition Language-Standardzeichenfolge zu**, um Benutzern und Gruppen Remoteaufrufe an SAM zu gewähren oder zu verweigern. **Nicht konfiguriert** (Standard) Die Security Descriptor Definition Language-Standardzeichenfolge lässt zu, dass Benutzer und Gruppen Remoteaufrufe an SAM durchführen.
  - **Sicherheitsbeschreibung**

### <a name="recovery-console-and-shutdown"></a>Wiederherstellungskonsole und Herunterfahren

- **Virtuellen Arbeitsspeicher beim Herunterfahren löschen:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit die Auslagerungsdatei des virtuellen Arbeitsspeichers beim Herunterfahren des Geräts gelöscht wird. Wenn **Nicht konfiguriert** festgelegt ist, wird der virtuelle Arbeitsspeicher nicht gelöscht.
- **Herunterfahren ohne Anmeldung:** Legen Sie diese Einstellung auf **Blockieren** fest, um die Option zum Herunterfahren auf dem Windows-Anmeldebildschirm auszublenden. Benutzer müssen sich beim Gerät anmelden und es dann herunterfahren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Benutzer das Gerät über den Windows-Anmeldebildschirm herunterfahren.

### <a name="user-account-control"></a>Benutzerkontensteuerung

- **UIA-Integrität ohne sicheren Speicherort:** Legen Sie diese Einstellung auf **Aktivieren** fest, um Apps, die sich an sicheren Speicherorten im Dateisystem befinden, nur mit UIAccess-Integrität auszuführen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, können Apps mit UIAccess-Integrität ausgeführt werden, auch wenn sie sich nicht an einem sicheren Ort im Dateisystem befinden.
- **Datei- und Registrierungsschreibfehler an Einzelbenutzerstandorte virtualisieren:** Wenn diese Einstellung auf **Blockieren** festgelegt ist, werden Schreibfehler der Anwendung zur Laufzeit an definierte Benutzerstandorte für das Dateisystem und die Registrierung umgeleitet. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, schlagen Anwendungen fehl, die Daten an geschützte Speicherorte schreiben.
- **Rechte nur für ausführbare Dateien erhöhen, die signiert und validiert wurden:** Legen Sie diese Einstellung auf **Aktiviert** fest, um die Überprüfung des PKI-Zertifizierungspfads für eine ausführbare Datei zu erzwingen, bevor sie ausgeführt werden kann. Legen Sie die Standardeinstellung **Nicht konfiguriert** fest, um die Überprüfung des PKI-Zertifizierungspfads nicht zu erzwingen, bevor eine ausführbare Datei ausgeführt werden kann.

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
- **Eingabeaufforderung für erhöhte Rechte an interaktiven Desktop des Benutzers umleiten:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit alle Anforderungen für erhöhte Rechte nicht an den sicheren Desktop, sondern an den interaktiven Benutzerdesktop umgeleitet. Alle Richtlinieneinstellungen für das Verhalten der Eingabeaufforderung für Administratoren und Standardbenutzer werden verwendet. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird erzwungen, dass alle Anforderungen für erhöhte Rechte an den sicheren Desktop umgeleitet werden, unabhängig von den Richtlinieneinstellungen für das Verhalten der Eingabeaufforderung für Administratoren und Standardbenutzer.
- **Eingabeaufforderung für erhöhte Rechte bei App-Installationen:** Wenn diese Einstellung auf **Blockieren** festgelegt ist, werden Anwendungsinstallationspakete nicht erkannt, und es wird keine Eingabeaufforderung für erhöhte Rechte angezeigt. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der Benutzer aufgefordert, den Benutzernamen und das Kennwort eines Administrators einzugeben, wenn ein Anwendungsinstallationspaket erhöhte Rechte erfordert.
- **UIA-Eingabeaufforderung für erhöhte Rechte ohne sicheren Desktop:** Legen Sie diese Einstellung auf **Aktivieren** fest, damit UIAccess-Apps eine Eingabeaufforderung für erhöhte Rechte anzeigen können, ohne den sicheren Desktop zu verwenden. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, verwendet die Eingabeaufforderung für erhöhte Rechte einen sicheren Desktop.

#### <a name="admin-approval-mode-settings"></a>Administratorgenehmigungsmodus-Einstellungen

- **Administratorgenehmigungsmodus für integrierten Administrator:** Legen Sie die Einstellung auf **Aktiviert** fest, damit das integrierte Administratorkonto den Administratorgenehmigungsmodus verwenden kann. Der Benutzer wird bei jedem Vorgang, der eine Rechteerweiterungen erfordert, zur Genehmigung aufgefordert. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden alle Apps mit vollständigen Administratorrechten ausgeführt.
- **Alle Administratoren im Administratorgenehmigungsmodus ausführen:** Legen Sie diese Einstellung auf **Blockieren** fest, um den Administratorgenehmigungsmodus und alle zugehörigen UAC-Richtlinieneinstellungen zu deaktivieren. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, wird der Administratorgenehmigungsmodus aktiviert.

### <a name="microsoft-network-client"></a>Microsoft-Netzwerkclient

- **Kommunikation digital signieren (wenn Server zustimmt):** Bestimmt, ob der SMB-Client die SMB-Paketsignatur aushandelt. Wenn diese Einstellung auf **Nicht konfiguriert** oder Aktiviert (Standardeinstellung) ist, weist der Microsoft-Netzwerkclient den Server an, die SMB-Paketsignatur beim Setup der Sitzung auszuführen. Wenn die Paketsignatur auf dem Server aktiviert ist, wird die Paketsignatur ausgehandelt. Wenn diese Einstellung auf **Deaktivieren** festgelegt ist, handelt der SMB-Client die SMB-Paketsignatur nie aus.
- **Unverschlüsseltes Kennwort an SMB-Server von Drittanbietern senden:** Wenn diese Einstellung auf **Aktivieren** festgelegt ist, kann der SMB-Redirector (Server Message Block) Klartextkennwörter an SMB-Server senden, die nicht von Microsoft stammen, und die keine Kennwortverschlüsselung während der Authentifizierung unterstützen. Wenn die Standardeinstellung **Nicht konfiguriert** festgelegt ist, werden die Kennwörter verschlüsselt.

### <a name="microsoft-network-server"></a>Microsoft-Netzwerkserver

- **Kommunikation digital signieren (wenn Client zustimmt)**: Bestimmt, ob der SMB-Server die SMB-Paketsignatur mit Clients verhandelt, die sie anfordern. Wenn diese Einstellung auf **Aktivieren** festgelegt ist, handelt der Microsoft-Netzwerkserver die SMB-Paketsignatur wie vom Client angefordert aus. Genau gesagt: Wenn die Paketsignatur auf dem Client aktiviert ist, wird die Paketsignatur ausgehandelt. Bei **Nicht konfiguriert** oder „Deaktiviert“ (Standard) handelt der SMB-Client die SMB-Paketsignatur nie aus.
- **Kommunikation digital signieren (immer)**: Bestimmt, ob die SMB-Serverkomponente die Paketsignatur erfordert. Wenn diese Einstellung auf **Aktivieren** festgelegt ist, kommuniziert der Microsoft-Netzwerkserver nur dann mit einem Microsoft-Netzwerkclient, wenn dieser der SMB-Paketsignatur zustimmt. Wenn die Einstellung **Nicht konfiguriert** oder Deaktiviert (Standardeinstellung) festgelegt ist, wird die SMB-Paketsignatur zwischen dem Client und dem Server ausgehandelt.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Zuweisen dieses Profils an Gruppen finden Sie unter [Zuweisen von Microsoft Intune-Geräteprofilen](device-profile-assign.md).
