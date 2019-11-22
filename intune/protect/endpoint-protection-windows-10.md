---
title: 'Schutzeinstellungen für Windows 10-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Verwenden oder konfigurieren Sie Einstellungen zu Endpoint Protection auf Windows 10-Geräten, um Microsoft Defender-Features zu aktivieren, darunter Application Guard, Firewall, SmartScreen, Verschlüsselung und BitLocker, Exploit Guard, Anwendungssteuerung, Security Center und Sicherheit auf lokalen Geräten in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e2909e7ad1ced9483a6cec58f1f3009f56946f5f
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74058426"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Einstellungen für Windows 10 (und höher), um Geräte zu schützen, die Intune verwenden.

In Microsoft Intune gibt es viele Einstellungen, die dazu dienen, Ihre Geräte zu schützen. In diesem Artikel werden alle Einstellungen erläutert, die Sie auf Geräten mit Windows 10 oder höher aktivieren und konfigurieren können. Diese Einstellungen werden in einem Endpoint Protection-Konfigurationsprofil in Intune erstellt, um die Optionen für Sicherheitsfunktionen festzulegen, einschließlich BitLocker und Microsoft Defender.  

Informationen zum Konfigurieren von Microsoft Defender Antivirus finden Sie unter den [Geräteeinschränkungen für Windows 10](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).  

## <a name="before-you-begin"></a>Vorbereitung  

[Hinzufügen der Endpoint Protection-Einstellungen in Intune](endpoint-protection-configure.md)  

Weitere Informationen zu Konfigurations Dienstanbietern (CSPs) finden Sie unter [Referenz zum Konfigurations Dienstanbieter](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="microsoft-defender-application-guard"></a>Microsoft Defender Application Guard  

Während der Verwendung von Microsoft Edge schützt Microsoft Defender Application Guard Ihre Umgebung vor Websites, die von Ihrer Organisation nicht als vertrauenswürdig definiert wurden. Wenn Benutzer Websites besuchen, die nicht in Ihrer isolierten Netzwerkgrenze aufgelistet sind, werden die Websites in einer virtuellen Hyper-V-Browsersitzung geöffnet. Vertrauenswürdige Websites werden durch eine Netzwerkgrenze definiert, die in der Gerätekonfiguration konfiguriert werden kann.  

Application Guard ist nur für Windows 10-Geräte (64-Bit) verfügbar. Mithilfe dieses Profils wird eine Win32-Komponente zur Aktivierung von Application Guard installiert.  

- **Application Guard**  
  **Standardeinstellung:** Nicht konfiguriert  
   Application Guard CSP: [Settings/allowwindowsdefenderapplicationguard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Aktiviert für Edge**: Aktiviert dieses Feature, das nicht vertrauenswürdige Websites in einem virtualisierten Hyper-V-Browsercontainer öffnet.  
  - **Nicht konfiguriert** : eine beliebige Site (vertrauenswürdig und nicht vertrauenswürdig) kann auf dem Gerät geöffnet werden.  

- **Verhalten der Zwischenablage**  
  **Standardeinstellung:** Nicht konfiguriert  
   Application Guard CSP: [Einstellungen/clipboardsettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  Legen Sie zulässige Aktionen für das Kopieren und Einfügen zwischen dem lokalen Computer und dem virtuellen Browser von Application Guard fest.  
  - **Nicht konfiguriert**  
  - **Kopieren und einfügen nur von PCs zum Browser zulassen**  
  - **Kopieren und einfügen nur aus dem Browser auf den PC zulassen**  
  - **Kopieren und Einfügen zwischen PC und Browser zulassen**  
  - **Kopieren und Einfügen zwischen PC und Browser blockieren**  

- **Inhalt der Zwischenablage**  
  Diese Einstellung ist nur verfügbar, wenn das *Verhalten der Zwischenablage* auf eine der *Zulassungs Einstellungen fest* gelegt ist.  
  **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Settings/clipboardfiletype](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Wählen Sie den zulässigen Inhalt der Zwischenablage aus.  
  - **Nicht konfiguriert**  
  - **Text**  
  - **Bilder**  
  - **Text und Bilder**  

- **Externer Inhalt auf Unternehmenswebsites**  
  **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Einstellungen/blocknonenterprisecontent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **Blockieren**: Verhindert, dass Inhalte von nicht genehmigten Websites geladen werden können.  
  - **Nicht konfiguriert**: Websites, bei denen es sich nicht um Unternehmenswebsites handelt, können auf dem Gerät geöffnet werden.  
 
- **Aus virtuellem Browser drucken**  
  **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Einstellungen/printingsettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Zulassen** : ermöglicht das Drucken ausgewählter Inhalte aus dem virtuellen Browser.  
  - **Nicht konfiguriert** Deaktivieren Sie alle Druck Features.  

  Wenn Sie das Drucken *zulassen* , können Sie die folgende Einstellung konfigurieren:
  - **Drucktyp (e)** Wählen Sie eine oder mehrere der folgenden Optionen aus:  
    - PDF  
    - XPS  
    - Lokale Drucker
    - Netzwerkdrucker  

- **Protokolle sammeln**  
  **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Audit/auditapplicationguard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Zulassen**: Protokolle werden für Ereignisse erfasst, die während einer Browsersitzung von Application Guard auftreten.  
  - **Nicht konfiguriert**: Protokolle werden während einer Browsersitzung nicht erfasst.  

- **Benutzergenerierte Browserdaten beibehalten**  
  **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Einstellungen/allowpersistenz](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Zulassen**: Benutzerdaten (z. B. Kennwörter, Favoriten und Cookies) werden gespeichert, die während einer virtuellen Browsersitzung von Application Guard erstellt werden.  
  - **Nicht konfiguriert**: Vom Benutzer heruntergeladene Dateien und Daten werden gelöscht, wenn das Gerät neu gestartet wird oder ein Benutzer sich abmeldet.  

- **Grafikbeschleunigung**  
 **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Einstellungen/allowvirtualgpu](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **Aktivieren**: Grafisch anspruchsvolle Websites und Videos werden schneller geladen, indem der Zugriff auf einen virtuellen Grafikprozessor gewährt wird.  
  - **Nicht konfiguriert** Verwenden der CPU des Geräts für Grafiken Verwenden Sie die Einheit für die virtuelle Grafik Verarbeitung nicht.  

- **Dateien auf Hostdateisystem herunterladen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Application Guard CSP: [Einstellungen/savefilestohost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Aktivieren**: Benutzer können Dateien aus dem virtualisierten Browser auf das Hostbetriebssystem herunterladen.  
  - **Nicht konfiguriert**: Die Dateien werden lokal auf dem Gerät gespeichert, und es werden keine Dateien auf das Hostdateisystem heruntergeladen.  

## <a name="microsoft-defender-firewall"></a>Microsoft Defender Firewall  
 
### <a name="global-settings"></a>Globale Einstellungen  

Diese Einstellungen können auf alle Netzwerktypen angewendet werden.  

- **Dateiübertragungsprotokoll**  
  **Standardeinstellung:** Nicht konfiguriert  
   Firewall-CSP: [mdmstore/Global/disablestatus efulftp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **Blockieren**: Deaktiviert statusbehaftetes FTP.  
  - **Nicht konfiguriert**: Die Firewall filtert statusbehaftetes FTP, um sekundäre Verbindungen zu ermöglichen.  

- **Leerlaufzeit für Sicherheitszuordnung vor Löschvorgang**  
  **Standard**: *Nicht konfiguriert*  
   Firewall-CSP: [mdmstore/Global/saidletime](https://go.microsoft.com/fwlink/?linkid=872539)  

   Geben Sie eine Leerlaufzeit in Sekunden an, nach der Sicherheits Zuordnungen gelöscht werden.   

- **Codierung vorinstallierter Schlüssel**  
  **Standardeinstellung:** Nicht konfiguriert  
   Firewall-CSP: [mdmstore/Global/presharedkeyencoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Aktivieren** -Codieren von vordefinierten Schlüsseln mithilfe von UTF-8.  
   - **Nicht konfiguriert** : Codieren Sie vorgestellte Schlüssel mit dem Wert des lokalen Stores.  

- **IPsec-Ausnahmen**  
  **Standard**Wert: *0 ausgewählt*  
   Firewall-CSP: [mdmstore/Global/ipsecausgenommen](https://go.microsoft.com/fwlink/?linkid=872547)

   Wählen Sie mindestens einen der folgenden Arten von Datenverkehr aus, der von IPsec ausgenommen werden soll:  
   - **Neighbor Discovery-IPv6-Codes vom Typ ICMP**  
   - **ICMP**  
   - **Router Discovery-IPv6-Codes vom Typ ICMP**  
   - **IPv4- und IPv6-DHCP-Netzwerkdatenverkehr**  

- **Überprüfung der Zertifikatssperrliste**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [mdmstore/Global/crlcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  Wählen Sie aus, wie das Gerät die Zertifikatssperrliste überprüft. Zu den Optionen gehören:  
  - **Überprüfung der CRL deaktivieren**  
  - **CRL-Überprüfung nur bei gesperrtem Zertifikat ausführen**  
  - **Fehler bei der CRL-Überprüfung bei jedem gefundenen Fehler**.  
 

- **Authentifizierungssatz opportunistisch pro Schlüsselerstellungsmodul abgleichen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [mdmstore/Global/opportunisticallymatchauthsetperkm](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Aktivieren**: Schlüsselerstellungsmodule müssen nur die Authentifizierungssätze ignorieren, die sie nicht unterstützen.  
  - **Nicht konfiguriert**: Schlüsselerstellungsmodule müssen den gesamten Authentifizierungssatz ignorieren, wenn sie nicht alle Authentifizierungssuites unterstützen, die im Satz angegeben sind.  


- **Paketwarteschlangen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [mdmstore/Global/enablepacketqueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Legen Sie fest, wie die Skalierung für die Software auf der Empfangsseite für den verschlüsselten Empfang und die Weiterleitung im Klartext für das IPsec-Tunnelgatewayszenario aktiviert wird. Durch diese Einstellung wird die Paketreihenfolge beibehalten. Zu den Optionen gehören:  
  - **Nicht konfiguriert**  
  - **Alle paketqueuingpakete deaktivieren**  
  - **Nur eingehende verschlüsselte Pakete in Warteschlange**  
  - **Pakete nach der Entschlüsselung nur für die Weiterleitung in Warteschlangen**  
  - **Konfigurieren von eingehenden und ausgehenden Paketen**  

### <a name="network-settings"></a>Netzwerkeinstellungen  

Die folgenden Einstellungen sind jeweils in diesem Artikel aufgelistet, gelten jedoch für die drei spezifischen Netzwerktypen:  
- **Domänen Netzwerk (Arbeitsplatz Netzwerk)**  
- **Privates (erkennbares) Netzwerk**  
- **Öffentliches Netzwerk (nicht auffindbar)**  

#### <a name="general-settings"></a>Allgemeine Einstellungen  

- **Microsoft Defender Firewall**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Aktivieren**: Aktivieren Sie die Firewall und die erweiterte Sicherheit. 
  - **Nicht konfiguriert**: Sämtlicher Netzwerkdatenverkehr wird unabhängig von anderen Richtlinieneinstellungen zugelassen.  

- **Geschützter Modus**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [disablestealthmode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **Nicht konfiguriert**  
  - **Block** -Firewall wird für den Betrieb im Stealth-Modus gesperrt. Wenn Sie den geschützten Modus blockieren, ermöglichen Sie ebenfalls das Blockieren von **durch IPsec gesicherten Paketausnahmen**.  
  - **Zulassen** : die Firewall wird im Modus "heimlich" betrieben, um Antworten auf Suchanforderungen zu verhindern.  

- **IPsec-gesicherte Paket Ausnahme im Debugmodus**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [disablestealthmodeipsecsecuredpacketexemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Diese Option wird ignoriert, wenn der *Stealth-Modus* auf *blockieren*festgelegt ist.  

  - **Nicht konfiguriert**  
  - **Block** -IPsec-gesicherte Pakete erhalten keine Ausnahmen.  
  - **Allow** -enable-Ausnahmen. Der heimliche Modus der Firewall darf nicht verhindern, dass der Host Computer auf nicht angeforderten Netzwerk Datenverkehr antwortet, der durch IPSec gesichert wird.  

- **Geschützt**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [abgeschirmt](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **Nicht konfiguriert**  
    - **Blockieren** : Wenn die Microsoft Defender Firewall eingeschaltet ist und diese Einstellung auf *blockieren*festgelegt ist, wird der gesamte eingehende Datenverkehr unabhängig von anderen Richtlinien Einstellungen blockiert. 
    - **Zulassen** : Wenn diese Einstellung auf *zulassen*festgelegt ist, wird diese Einstellung deaktiviert, und eingehender Datenverkehr ist abhängig von anderen Richtlinien Einstellungen zulässig.

- **Unicastantworten auf Multicastbroadcasts**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [disableunicastresponcstomulticastbroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  Sie möchten wohl keine Unicastantworten auf Multicast- oder Broadcastmeldungen empfangen. Diese Antworten können auf einen DoS-Angriff (Denial of Service) hinweisen, oder einen Angreifer, der versucht, einen bekannten aktiven Computer zu testen.  
  - **Nicht konfiguriert**  
  - **Block**: Deaktivieren Sie Unicastantworten auf Multicastbroadcasts.  
  - **Zulassen**: Lassen Sie Unicastantworten auf Multicastbroadcasts zu.  

- **Eingehende Benachrichtigungen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [disableinboundbenachrichtigungen](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **Nicht konfiguriert**  
  - **Blockieren** Sie Benachrichtigungen, die verwendet werden, wenn eine APP für das lauschen an einem Port blockiert ist.  
  - **Zulassen**: Die Einstellung wird aktiviert, und Benutzern werden Benachrichtigungen angezeigt, wenn eine App für das Lauschen auf einen Port blockiert ist.  

- **Standardaktion für ausgehende Verbindungen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [defaultoutboundaction](https://aka.ms/intune-firewall-outboundaction)  
  
  Konfigurieren Sie die Standardaktion, die die Firewall für ausgehende Verbindungen ausführt. Diese Einstellung wird auf Windows-Version 1809 und höher angewendet.  

  - **Nicht konfiguriert**  
  - **Blockieren** : die Standard Firewall-Aktion wird nicht für ausgehenden Datenverkehr ausgeführt, es sei denn, Sie wird explizit angegeben  
  - **Zulassen** : standardmäßige Firewallaktionen werden für ausgehende Verbindungen ausgeführt.  

- **Standardaktion für eingehende Verbindungen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [defaultinboundaction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **Nicht konfiguriert**  
  - **Blockieren**: Die Standardaktion der Firewall wird für eingehende Verbindungen nicht ausgeführt.  
  - **Zulassen** : standardmäßige Firewallaktionen werden für eingehende Verbindungen ausgeführt.  

#### <a name="rule-merging"></a>Regelzusammenführung  

- **Microsoft Defender-Firewallregeln für autorisierte Anwendungen aus dem lokalen Speicher**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [authappsallowuserpräfemerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **Nicht konfiguriert**  
  - **Blockieren**: Die Firewallregeln für autorisierte Anwendungen im lokalen Speicher werden ignoriert und nicht erzwungen.  
  - **Zulassen**: -
   Wählen Sie **Aktivieren** aus, um Firewallregeln auf dem lokalen Speicher anzuwenden, sodass sie erkannt und erzwungen werden.  

- **Microsoft Defender Firewall-Regeln für den globalen Port aus dem lokalen Speicher**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [globalportsallowuserpräfemerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **Nicht konfiguriert**  
  - **Blockieren** : die Firewallregeln für den globalen Port im lokalen Speicher werden ignoriert und nicht erzwungen.  
  - **Aktivieren**: Wenden Sie Firewallregeln für den globalen Port auf dem lokalen Speicher an, sodass sie erkannt und erzwungen werden.  

- **Microsoft Defender Firewall-Regeln aus dem lokalen Speicher**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [allowlocalpolicymerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **Nicht konfiguriert**  
  - **Block** -Firewall-Regeln aus dem lokalen Speicher werden ignoriert und nicht erzwungen.
  - **Aktivieren**: Wenden Sie Firewallregeln auf dem lokalen Speicher an, sodass sie erkannt und erzwungen werden.  

- **IPsec-Regeln aus dem lokalen Speicher**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [allowlocalipsecpolicymerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **Nicht konfiguriert**  
  - **Blockieren**: Die Verbindungssicherheitsregeln im lokalen Speicher werden unabhängig von der Schemaversion und der Version der Verbindungssicherheitsregeln ignoriert und nicht erzwungen.  
  - **Zulassen**: Wenden Sie Verbindungssicherheitsregeln aus dem lokalen Speicher an, die unabhängig vom Schema oder den Versionen der Verbindungssicherheitsregeln gelten.  

### <a name="firewall-rules"></a>Firewallregeln  

Sie können eine oder mehrere benutzerdefinierte Firewallregeln **Hinzufügen** . Weitere Informationen finden Sie unter [Hinzufügen von benutzerdefinierten Firewallregeln für Windows 10-Geräte](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

Benutzerdefinierte Firewallregeln unterstützen die folgenden Optionen:  

#### <a name="general-settings"></a>Allgemeine Einstellungen:  

- **Name**  
  **Standard**Wert: *kein Name*  

  Geben Sie einen anzeigen Amen für die Regel an. Dieser Name wird in der Liste der Regeln angezeigt, die Ihnen bei der Identifizierung helfen.  

- **Beschreibung**  
  **Standard**Wert: *keine Beschreibung*  

  Geben Sie eine Beschreibung der Regel an.  

- **Richtung**   
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [firewallrules/*firewallrulename*/Direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Geben Sie an, ob diese Regel für **Eingeh**enden oder **Ausgeh** enden Datenverkehr gilt. Wenn diese Einstellung als **nicht konfiguriert**festgelegt ist, gilt die Regel automatisch für ausgehenden Datenverkehr.  

- **Aktion**  
  **Standardeinstellung:** Nicht konfiguriert  
  Firewall-CSP: [firewallrules/*firewallrulename*/Action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)und [firewallrules/*firewallrulename*/Action/Type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Wählen Sie aus **zulassen** oder **blockieren**aus. Wenn die Einstellung als **nicht konfiguriert**festgelegt ist, wird der Datenverkehr standardmäßig zugelassen.  

- **Netzwerktyp**  
  **Standard**Wert: 0 ausgewählt  
  Firewall-CSP: [firewallrules/*firewallrulename*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Wählen Sie bis zu drei Typen von Netzwerktypen aus, zu denen diese Regel gehört. Zu den Optionen gehören **Domäne**, **Privat**und **öffentlich**.  Wenn keine Netzwerktypen ausgewählt sind, gilt die Regel für alle drei Netzwerktypen.  

#### <a name="application-settings"></a>Anwendungseinstellungen  

- **Anwendung (en)**  
  **Standard**: Alle  

  Steuern von Verbindungen für eine APP oder ein Programm. Wählen Sie eine der folgenden Optionen aus, und führen Sie dann die zusätzliche Konfiguration aus:  
  - **Paket Familienname** – geben Sie einen Paket Familiennamen an. Verwenden Sie den PowerShell **-Befehl Get-appxpackage**, um den Paket Familiennamen zu ermitteln.   
    Firewall-CSP: [firewallrules/*firewallrulename*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **Dateipfad** – Sie müssen einen Dateipfad zu einer APP auf dem Client Gerät angeben. dabei kann es sich um einen absoluten Pfad oder um einen relativen Pfad handeln. Beispiel: c:\windows\system\notepad.exe oder%windir%\notepad.exe.  
    Firewall-CSP: [firewallrules/*firewallrulename*/App/filePath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Windows-Dienst** – geben Sie den Kurznamen für den Windows-Dienst an, wenn es sich um einen Dienst handelt, nicht um eine Anwendung, die Datenverkehr sendet Verwenden Sie den PowerShell-Befehl **Get-Service**, um den Dienst Kurznamen zu ermitteln.  
    Firewall-CSP: [firewallrules/*firewallrulename*/App/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Alle**– *es ist keine weitere Konfiguration verfügbar*.  

#### <a name="ip-address-settings"></a>IP-Adress Einstellungen  

Geben Sie die lokalen und Remote Adressen an, für die diese Regel gilt.  

- **Lokale Adressen**    
  **Standard**: beliebige Adresse  
  Firewall-CSP: [firewallrules/*firewallrulename*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Wählen Sie **eine beliebige Adresse oder eine** **angegebene Adresse**aus.  

  Wenn Sie die *angegebene Adresse*verwenden, fügen Sie eine oder mehrere Adressen als durch Trennzeichen getrennte Liste von lokalen Adressen hinzu, die von der Regel abgedeckt werden. Gültige Token sind:  
  - Verwenden Sie für eine *beliebige* lokale Adresse ein Sternchen (*). Wenn Sie ein Sternchen verwenden, darf dies das einzige Token sein, das Sie verwenden.  
  - Verwenden Sie zum Angeben eines Subnetzes entweder die Subnetzmaske oder die Netzwerk Präfix Notation. Wenn weder eine Subnetzmaske noch ein Netzwerk Präfix angegeben ist, wird die Subnetzmaske standardmäßig auf 255.255.255.255 festgelegt.  
  - Eine gültige IPv6-Adresse  
  - Ein IPv4-Adressbereich im Format "Start address-End Address" ohne Leerzeichen.  
  - Ein IPv6-Adressbereich im Format "Start address-End Address" ohne Leerzeichen.  

- **Remote Adressen**  
  **Standard**: beliebige Adresse  
  Firewall-CSP: [firewallrules/*firewallrulename*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Wählen Sie **eine beliebige Adresse oder eine** **angegebene Adresse**aus.  

  Wenn Sie die *angegebene Adresse*verwenden, fügen Sie eine oder mehrere Adressen als durch Trennzeichen getrennte Liste von Remote Adressen hinzu, die von der Regel abgedeckt werden. Die Groß-/Kleinschreibung wird nicht beachtet. Gültige Token sind:  
  - Verwenden Sie für *jede* Remote Adresse ein Sternchen "*". Wenn Sie ein Sternchen verwenden, darf dies das einzige Token sein, das Sie verwenden.  
  - "DefaultGateway"  
  - „DHCP“  
  - „DNS“  
  - „WINS“  
  - "Intranet" (wird unter Windows, Version 1809 und höher) unterstützt.  
  - "Rmtintranet" (unter Windows-Versionen 1809 und höher unterstützt)  
  - "Internet" (wird unter Windows, Version 1809 und höher) unterstützt.  
  - "Ply2Renders" (wird unter Windows, Version 1809 und höher) unterstützt.  
  - "LocalSubnet" gibt eine beliebige lokale Adresse im lokalen Subnetz an.  
  - Verwenden Sie zum Angeben eines Subnetzes entweder die Subnetzmaske oder die Netzwerk Präfix Notation. Wenn weder eine Subnetzmaske noch ein Netzwerk Präfix angegeben ist, wird die Subnetzmaske standardmäßig auf 255.255.255.255 festgelegt.  
  - Eine gültige IPv6-Adresse  
  - Ein IPv4-Adressbereich im Format "Start address-End Address" ohne Leerzeichen.  
  - Ein IPv6-Adressbereich im Format "Start address-End Address" ohne Leerzeichen.  

#### <a name="port-and-protocol-settings"></a>Port-und Protokoll Einstellungen  
Geben Sie die lokalen und Remoteports an, für die diese Regel gilt.  

- **Protokoll**  
  **Standard**Wert: beliebig  
  Firewall-CSP: [firewallrules/*firewallrulename*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Wählen Sie eine der folgenden Optionen aus, und führen Sie alle erforderlichen Konfigurationen aus:  
  - **Alle** – es ist keine weitere Konfiguration verfügbar.  
  - **TCP** – lokale Ports und Remoteports konfigurieren. Beide Optionen unterstützen alle Ports oder die angegebenen Ports. Geben Sie mithilfe einer durch Trennzeichen getrennten Liste angegebene Ports ein.  
    - **Lokale Ports** -Firewall-CSP: [firewallrules/*firewallrulename*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Remoteports** -Firewall-CSP: [firewallrules/*firewallrulename*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** – lokale Ports und Remoteports konfigurieren. Beide Optionen unterstützen alle Ports oder die angegebenen Ports. Geben Sie mithilfe einer durch Trennzeichen getrennten Liste angegebene Ports ein.  
    - **Lokale Ports** -Firewall-CSP: [firewallrules/*firewallrulename*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Remoteports** -Firewall-CSP: [firewallrules/*firewallrulename*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Benutzer** definiert – geben Sie eine benutzerdefinierte **Protokoll** Nummer zwischen 0 und 255 an.  

#### <a name="advanced-configuration"></a>Erweiterte Konfiguration  
- **Schnittstellentypen**  
  **Standard**Wert: 0 ausgewählt  
  Firewall-CSP: [firewallrules/*firewallrulename*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Wählen Sie eine der folgenden Optionen aus:  
  - **Remotezugriff**  
  - **Drahtlos**  
  - **Lokales Netzwerk**  

- **Nur Verbindungen von diesen Benutzern zulassen**  
  **Standard**: alle Benutzer *(standardmäßig alle Verwendungen, wenn keine Liste angegeben ist)*  
  Firewall-CSP: [firewallrules/*firewallrulename*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  Geben Sie eine Liste der autorisierten lokalen Benutzer für diese Regel an. Eine Liste der autorisierten Benutzer kann nicht angegeben werden, wenn diese Regel für einen Windows-Dienst gilt.  


## <a name="microsoft-defender-smartscreen-settings"></a>Einstellungen für Microsoft Defender SmartScreen  
 
Microsoft Edge muss auf dem Gerät installiert sein.  

- **SmartScreen für Apps und Dateien**  
  **Standardeinstellung:** Nicht konfiguriert  
   SmartScreen-CSP: [SmartScreen/enablesmartscreeninshell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **Nicht konfiguriert** : deaktiviert die Verwendung von SmartScreen.  
  - **Aktivieren**: Aktivieren Sie Windows SmartScreen für die Datei- und App-Ausführung. SmartScreen ist eine cloudbasierte Komponente gegen Phishing- und Schadsoftware.  

- **Ausführung nicht überprüfter Dateien**  
  **Standardeinstellung:** Nicht konfiguriert  
   SmartScreen-CSP: [SmartScreen/preventoverrideforfilesinshell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Nicht konfiguriert**: Deaktiviert dieses Feature, sodass Endbenutzer keine Dateien ausführen können, die nicht überprüft wurden.  
  - **Blockieren**: Sperren Sie die Ausführung von Dateien durch den Benutzer, die nicht durch Windows SmartScreen überprüft wurden.  

## <a name="windows-encryption"></a>Windows-Verschlüsselung  
 
### <a name="windows-settings"></a>Windows-Einstellungen  

- **Geräte verschlüsseln**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: Requirements [deviceencryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Anfordern**: Fordern Sie Benutzer dazu auf, die Geräteverschlüsselung zu aktivieren. Je nach Windows-Edition und Systemkonfiguration können Benutzer zu Folgendem aufgefordert werden:  
    - Zur Bestätigung, dass keine Verschlüsselung eines anderen Anbieters aktiviert ist  
    - Zum Deaktivieren der BitLocker-Laufwerksverschlüsselung und zum anschließenden Aktivieren von BitLocker  
  - **Nicht konfiguriert**  
  
  Wenn die Windows-Verschlüsselung eingeschaltet wird, während eine andere Verschlüsselungsmethode aktiv ist, wird das Gerät möglicherweise instabil.  

- **Speicherkarte verschlüsseln (nur Mobilgeräte)**  
  *Diese Einstellung gilt nur für Windows 10 Mobile.*  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: Requirements [storagecardencryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - Legen Sie diese Einstellung auf **Anfordern** fest, um alle vom Gerät verwendeten wechselbaren Speicherkarten zu verschlüsseln.  
  - **Nicht konfiguriert**: Es ist keine Speicherkartenverschlüsselung erforderlich, und der Benutzer wird nicht dazu aufgefordert, diese zu aktivieren.  

### <a name="bitlocker-base-settings"></a>BitLocker-Grundeinstellungen  

Bei den Grundeinstellungen handelt es sich um universelle BitLocker-Einstellungen, die für alle Typen von Datenträgern gelten. Durch diese Einstellungen wird verwaltet, welche Aufgaben für die Laufwerkverschlüsselung oder Konfigurationsoptionen der Benutzer auf allen Typen von Laufwerken ändern kann.  

- **Warnung zu anderer Datenträgerverschlüsselung**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker-CSP: [allowwarningforotherdiskencryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Blockieren**: Deaktivieren Sie die Warnung, die angezeigt wird, wenn ein anderer Dienst zur Datenträgerverschlüsselung auf dem Gerät vorhanden ist.  
  - **Nicht konfiguriert** : erlauben Sie, dass die Warnung für die andere Datenträger Verschlüsselung angezeigt wird.  

  Wenn Sie auf *blockieren*festgelegt ist, können Sie die folgende Einstellung konfigurieren:  

  - **Standardbenutzern erlauben, die Verschlüsselung während Azure AD Join zu aktivieren**  
    *Diese Einstellung gilt nur für Azure Active Directory verbundene Geräte (Azure adj) und hängt von der vorherigen Einstellung `Warning for other disk encryption`ab.*  
    **Standardeinstellung:** Nicht konfiguriert  
    BitLocker-CSP: [allowstandarduserencryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Allow** -Standard Benutzer (nicht-Administratoren) können die BitLocker-Verschlüsselung aktivieren, wenn Sie angemeldet sind.  
     - **Nicht konfiguriert**: Nur Administratoren können die BitLocker-Verschlüsselung auf dem Gerät aktivieren.  

- **Verschlüsselungsmethoden konfigurieren**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: [verschlüsselungsmethodbydrivetype](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Aktivieren**: Konfigurieren Sie Verschlüsselungsalgorithmen für Betriebssystem- und Datenlaufwerke sowie für Wechseldatenträger.  
  - **Nicht konfiguriert**: BitLocker verwendet XTS-AES 128-Bit als Standardverschlüsselungsmethode oder die Verschlüsselungsmethode, die von einem Setupskript festgelegt wird.  

  Bei der Einstellung *Aktivieren* können Sie folgende Einstellungen konfigurieren:  

  - **Verschlüsselung für Betriebssystemlaufwerke**  
    **Standard**: XTS-AES 128-Bit  
   
    Wählen Sie die Verschlüsselungsmethode für Betriebssystemlaufwerke aus. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.  
    - **AES-CBC, 128 Bit**  
    - **AES-CBC, 256 Bit**  
    - **XTS-AES 128-Bit**  
    - **XTS-AES 256-Bit**  

  - **Verschlüsselung für Festplattenlaufwerke**  
    **Standard**: AES-CBC 128-Bit  
   
    Wählen Sie die Verschlüsselungsmethode für Festplattenlaufwerke (integriert) aus. Es wird empfohlen, dass Sie den XTS-AES-Algorithmus verwenden.  
    - **AES-CBC, 128 Bit**  
    - **AES-CBC, 256 Bit**  
    - **XTS-AES 128-Bit**  
    - **XTS-AES 256-Bit**  

  - **Verschlüsselung für Wechseldatenträger**  
    **Standard**: AES-CBC 128-Bit  

    Wählen Sie die Verschlüsselungsmethode für Wechseldatenträger aus. Wenn der Wechseldatenträger mit Geräten verwendet wird, auf denen nicht Windows 10 ausgeführt wird, wird empfohlen, den AES-CBC-Algorithmus zu verwenden.  
    - **AES-CBC, 128 Bit**  
    - **AES-CBC, 256 Bit**  
    - **XTS-AES 128-Bit**  
    - **XTS-AES 256-Bit**  

### <a name="bitlocker-os-drive-settings"></a>Einstellung für BitLocker-OS-Datenträger  

Diese Einstellungen gelten speziell für Betriebssystemlaufwerke.  

- **Zusätzliche Authentifizierung beim Start**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: [systemdrivesrequirements startupauthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Anfordern**: Konfigurieren Sie die Authentifizierungsanforderungen für den Computerstart, einschließlich der Verwendung von Trusted Platform Module (TPM).  
  - **Nicht konfiguriert** : Konfigurieren Sie nur die grundlegenden Optionen auf Geräten mit einem TPM.  

  Bei der Einstellung *Anfordern* können Sie folgende Einstellungen konfigurieren:  

  - **BitLocker mit nicht kompatiblem TPM-Chip**  
    **Standardeinstellung:** Nicht konfiguriert  

    - **Blockieren**: Deaktivieren Sie die Verwendung von BitLocker, wenn ein Gerät nicht über einen kompatiblen TPM-Chip verfügt.  
    - **Nicht konfiguriert**: Benutzer können BitLocker ohne einen kompatiblen TPM-Chip verwenden. BitLocker kann ein Kennwort oder einen Systemstartschlüssel erfordern.  

  - **Systemstart für kompatibles TPM**  
    **Standardeinstellung**: TPM zulassen  

    Hiermit wird konfiguriert, ob TPM zulässig, erforderlich oder nicht zulässig ist.  

    - **TPM zulassen**  
    - **TPM nicht zulassen**  
    - **TPM erforderlich**  

  - **Systemstart-PIN für kompatibles TPM**  
    **Standard**: Start-PIN mit TPM zulassen  

    Legen Sie fest, ob mit dem TPM-Chip eine Systemstart-PIN zugelassen, nicht zugelassen oder erforderlich ist. Für das Aktivieren einer Systemstart-PIN ist ein Eingreifen des Endbenutzers erforderlich.  

    - **Systemstart-PIN mit TPM zulassen**  
    - **Systemstart-PIN mit TPM nicht zulassen**  
    - **Systemstart-PIN mit TPM erforderlich**

  - **Systemstartschlüssel für kompatibles TPM**  
    **Standard**: Systemstart Schlüssel mit TPM zulassen  

    Legen Sie fest, ob die Verwendung eines Systemstartschlüssels mit dem TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist. Für das Aktivieren eines Systemstartschlüssels ist ein Eingreifen des Endbenutzers erforderlich.  

    - **Systemstart Schlüssel mit TPM zulassen**  
    - **Systemstart Schlüssel mit TPM nicht zulassen**  
    - **Systemstart Schlüssel mit TPM erforderlich**  

  - **Systemstartschlüssel und -PIN für kompatibles TPM**  
    **Standard**: Systemstart Schlüssel und-PIN mit TPM zulassen  

    Legen Sie fest, ob die Verwendung eines Systemstartschlüssels und einer PIN mit dem TPM-Chip zugelassen, nicht zugelassen oder erforderlich ist. Für das Aktivieren eines Systemstartschlüssels und einer Systemstart-PIN ist ein Eingreifen des Endbenutzers erforderlich.  
    - **Systemstart Schlüssel und-PIN mit TPM zulassen**  
    - **Systemstart Schlüssel und-PIN mit TPM nicht zulassen**  
    - **Systemstart Schlüssel und-PIN mit TPM erforderlich**   

- **PIN-Mindestlänge**  
    **Standardeinstellung:** Nicht konfiguriert  
    BitLocker CSP: [systemdrivesminimumpinlength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Aktivieren** von Konfigurieren Sie eine Mindestlänge für das TPM-Systemstart-PIN.  
    - **Nicht konfiguriert**: Benutzer können eine Systemstart-PIN zwischen 6 und 20 Ziffern konfigurieren.  

  Wenn *Aktivieren* festgelegt ist, können Sie die folgende Einstellung konfigurieren:  

  - **Mindestanzahl von Zeichen**  
    **Standard**: *nicht konfiguriert* BitLocker CSP: [systemdrivesminimumpinlength](https://go.microsoft.com/fwlink/?linkid=872528)  

    Geben Sie die Zahl an Zeichen (**4**-**20**) an, die für die Systemstart-PIN erforderlich sind.  

- **Wiederherstellung von Betriebssystemlaufwerken**  
  **Standardeinstellung:** Nicht konfiguriert   
  BitLocker CSP: [systemdriveswiederherstellungsanoptionen](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Aktivieren**: Sie können festlegen, wie durch BitLocker geschützte Betriebssystemdatenträger wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht verfügbar sind.  
  - **Nicht konfiguriert**: Die Standardwiederherstellungsoptionen werden für die BitLocker-Wiederherstellung unterstützt. Standardmäßig ist DRA zulässig, die Wiederherstellungsoptionen (einschließlich Wiederherstellungskennwort und -schlüssel) werden vom Benutzer angegeben, und Wiederherstellungsinformationen werden nicht in AD DS gesichert.  

  Bei der Einstellung *Aktivieren* können Sie folgende Einstellungen konfigurieren:  

  - **Zertifikatbasierter Datenwiederherstellungs-Agent**  
    **Standardeinstellung:** Nicht konfiguriert  
     
    - **Blockieren** : verhindert die Verwendung des Datenwiederherstellungs-Agents mit durch BitLocker geschützten Betriebssystem Laufwerken.  
    - **Nicht konfiguriert** : erlauben Sie die Verwendung von Datenwiederherstellungs-Agents mit durch BitLocker geschützten Betriebssystem Laufwerken.  

  - **Erstellung des Wiederherstellungskennworts durch den Benutzer**  
    **Standard**: 48-stelliges Wiederherstellungs Kennwort zulassen  

    Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.  
    - **48-stelliges Wiederherstellungs Kennwort zulassen**  
    - **48-stelliges Wiederherstellungs Kennwort nicht zulassen**  
    - **48-stelliges Wiederherstellungs Kennwort erforderlich**  

  - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**  
    **Standard**: 256-Bit-Wiederherstellungs Schlüssel zulassen  

    Legen Sie fest, ob Benutzer einen 256-Bit-Wiederherstellungsschlüssel generieren dürfen oder müssen.  
    - **256-Bit-Wiederherstellungs Schlüssel zulassen**  
    - **256-Bit-Wiederherstellungs Schlüssel nicht zulassen**  
    - **256-Bit-Wiederherstellungs Schlüssel erforderlich**  

  - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten**  
    **Standardeinstellung:** Nicht konfiguriert  

    - **Blockieren**: Benutzer können Wiederherstellungsoptionen nicht anzeigen oder ändern. Wenn festgelegt auf 
    - **Nicht konfiguriert**: Benutzer können die Wiederherstellungsoptionen anzeigen und ändern, wenn sie BitLocker aktivieren. 
 
  - **BitLocker-Wiederherstellungs Informationen in Azure Active Directory speichern**  
    **Standardeinstellung:** Nicht konfiguriert  

    - **Aktivieren**: Speichern Sie die BitLocker-Wiederherstellungsinformationen in Azure Active Directory (AAD).  
    - **Nicht konfiguriert** : die BitLocker-Wiederherstellungs Informationen werden nicht in Aad gespeichert.  

  - **In Azure Active Directory gespeicherte BitLocker-Wiederherstellungs Informationen**  
    **Standardeinstellung**: Wiederherstellungskennwörter und Schlüsselpakete sichern  

    Konfigurieren Sie, welche BitLocker-Wiederherstellungsinformationen in Azure AD gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:  
    - **Wiederherstellungskennwörter und Schlüsselpakete sichern**  
    - **Nur Wiederherstellungskennwörter sichern**  

  - **Client gesteuerte Wiederherstellungs Kennwort-Rotation**  
    **Standard**: die Schlüssel Rotation ist für Azure AD Geräte aktiviert.  
    BitLocker CSP: [configurerecoverypasswordrotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Diese Einstellung initiiert eine Client gesteuerte Wiederherstellungs Kennwort-Rotation nach einer Wiederherstellung des Betriebssystem Laufwerks (entweder mithilfe von Bootmgr oder WinRE).  

    - Nicht konfiguriert  
    - Schlüssel Rotation deaktiviert  
    - Schlüssel Rotation für Azure AD verbundenen Geräten aktiviert  
    - Die Schlüssel Rotation ist für Azure AD und in Hybrid eingebundenen Geräten aktiviert.  

  - **Speichern von Wiederherstellungs Informationen in Azure Active Directory vor dem Aktivieren von BitLocker**  
    **Standardeinstellung:** Nicht konfiguriert  
 
     Hiermit wird verhindert, dass Benutzer BitLocker aktivieren, es sei denn, der Computer sichert die BitLocker-Wiederherstellungs Informationen erfolgreich in Azure Active Directory.  

    - **Anfordern**: Verhindern Sie, dass Benutzer BitLocker aktivieren, es sei denn, die BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Azure AD gespeichert.  
    - **Nicht konfiguriert**: Benutzer können BitLocker aktivieren, auch wenn die Wiederherstellungsinformationen nicht erfolgreich in Azure AD gespeichert wurden.  

- **Pre-Boot-Wiederherstellungsmeldung und -URL**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker-CSP: [systemdriveswiederherstellungsanage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Aktivieren** : Konfigurieren Sie die Nachricht und die URL, die auf dem Bildschirm für die vorab Start Schlüsselwiederherstellung angezeigt werden.  
  - **Nicht konfiguriert**: Deaktivieren Sie dieses Feature.  
  
  Wenn *Aktivieren* festgelegt ist, können Sie die folgende Einstellung konfigurieren:  
  - **Pre-Boot-Wiederherstellungsmeldung**  
    **Standardeinstellung**: Verwenden Sie die standardmäßige Wiederherstellungsmeldung und -URL.   
 
    Legen Sie fest, wie die Pre-Boot-Wiederherstellungsmeldung Benutzern angezeigt wird. Es stehen die folgenden Optionen zur Auswahl:  
    - **Standardmäßige Wiederherstellungsmeldung und -URL verwenden**  
    - **Leere Wiederherstellungsmeldung und -URL verwenden**  
    - **Benutzerdefinierte Wiederherstellungsmeldung**  
    - **Benutzerdefinierte Wiederherstellungs-URL**  

### <a name="bitlocker-fixed-data-drive-settings"></a>Einstellungen für das BitLocker-Festplattenlaufwerk  

Diese Einstellungen gelten speziell für Festplattenlaufwerke.  

- **Schreibzugriff auf nicht durch BitLocker geschützte Festplattenlaufwerke**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: [fixeddrivesrequirements Encryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Blockieren**: Gewähren Sie nur Lesezugriff auf nicht durch BitLocker geschützte Datenträger.  
  - **Nicht konfiguriert** : standardmäßig Lese-und Schreibzugriff auf Daten Laufwerke, die nicht verschlüsselt sind.  

- **Wiederherstellung von Festplattenlaufwerken**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: [fixeddrivesherstellyoptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Aktivieren**: Steuern Sie, wie durch BitLocker geschützte Festplattenlaufwerke wiederhergestellt werden, wenn die erforderlichen Systemstartinformationen nicht vorliegen.  
  - **Nicht konfiguriert**: Deaktivieren Sie dieses Feature.  

  Bei der Einstellung *Aktivieren* können Sie folgende Einstellungen konfigurieren:  

  - **Datenwiederherstellungs-Agent**  
    **Standardeinstellung:** Nicht konfiguriert  
 
    - **Blockieren**: Blockieren Sie die Verwendung des Datenwiederherstellungs-Agents mit dem Richtlinien-Editor für durch BitLocker geschützte Festplattenlaufwerke. 
    - **Nicht konfiguriert**: Ermöglicht die Verwendung von Datenwiederherstellungs-Agents auf durch BitLocker geschützten Festplattenlaufwerken.  

  - **Erstellung des Wiederherstellungskennworts durch den Benutzer**  
    **Standard**: 48-stelliges Wiederherstellungs Kennwort zulassen  

    Legen Sie fest, ob Benutzer ein 48-stelliges Wiederherstellungskennwort generieren dürfen oder müssen.  
    - **48-stelliges Wiederherstellungs Kennwort zulassen**  
    - **48-stelliges Wiederherstellungs Kennwort nicht zulassen**  
    - **48-stelliges Wiederherstellungs Kennwort erforderlich**  

  - **Erstellung des Wiederherstellungsschlüssels durch den Benutzer**  
    **Standard**: 256-Bit-Wiederherstellungs Schlüssel zulassen

    Legen Sie fest, ob Benutzer einen 256-Bit-Wiederherstellungsschlüssel generieren dürfen oder müssen.
    - **256-Bit-Wiederherstellungs Schlüssel zulassen**  
    - **256-Bit-Wiederherstellungs Schlüssel nicht zulassen**  
    - **256-Bit-Wiederherstellungs Schlüssel erforderlich**  

  - **Wiederherstellungsoptionen im BitLocker-Setup-Assistenten**  
    **Standardeinstellung:** Nicht konfiguriert  

    - **Blockieren**: Benutzer können Wiederherstellungsoptionen nicht anzeigen oder ändern. Wenn festgelegt auf 
    - **Nicht konfiguriert**: Benutzer können die Wiederherstellungsoptionen anzeigen und ändern, wenn sie BitLocker aktivieren.
 
  - **BitLocker-Wiederherstellungs Informationen in Azure Active Directory speichern**  
    **Standardeinstellung:** Nicht konfiguriert  

    - **Aktivieren**: Speichern Sie die BitLocker-Wiederherstellungsinformationen in Azure Active Directory (AAD).  
    - **Nicht konfiguriert** : die BitLocker-Wiederherstellungs Informationen werden nicht in Aad gespeichert.

  - **In Azure Active Directory gespeicherte BitLocker-Wiederherstellungs Informationen**  
    **Standardeinstellung**: Wiederherstellungskennwörter und Schlüsselpakete sichern  

    Konfigurieren Sie, welche BitLocker-Wiederherstellungsinformationen in Azure AD gespeichert werden. Es stehen die folgenden Optionen zur Auswahl:  
    - **Wiederherstellungskennwörter und Schlüsselpakete sichern**  
    - **Nur Wiederherstellungskennwörter sichern**  

  - **Client gesteuerte Wiederherstellungs Kennwort-Rotation**  
    **Standard**: die Schlüssel Rotation ist für Azure AD Geräte aktiviert.  
    BitLocker CSP: [configurerecoverypasswordrotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Diese Einstellung initiiert eine Client gesteuerte Wiederherstellungs Kennwort-Rotation nach einer Wiederherstellung des Betriebssystem Laufwerks (entweder mithilfe von Bootmgr oder WinRE).  

    - Nicht konfiguriert  
    - Schlüssel Rotation deaktiviert  
    - Schlüssel Rotation für Azure AD verbundenen Geräten aktiviert  
    - Die Schlüssel Rotation ist für Azure AD und in Hybrid eingebundenen Geräten aktiviert.  

  - **Speichern von Wiederherstellungs Informationen in Azure Active Directory vor dem Aktivieren von BitLocker**  
    **Standardeinstellung:** Nicht konfiguriert  
 
    Hiermit wird verhindert, dass Benutzer BitLocker aktivieren, es sei denn, der Computer sichert die BitLocker-Wiederherstellungs Informationen erfolgreich in Azure Active Directory.  

    - **Anfordern**: Verhindern Sie, dass Benutzer BitLocker aktivieren, es sei denn, die BitLocker-Wiederherstellungsinformationen wurden erfolgreich in Azure AD gespeichert.  
    - **Nicht konfiguriert**: Benutzer können BitLocker aktivieren, auch wenn die Wiederherstellungsinformationen nicht erfolgreich in Azure AD gespeichert wurden.  

### <a name="bitlocker-removable-data-drive-settings"></a>Einstellungen für den BitLocker-Wechseldatenträger  

Diese Einstellungen gelten speziell für Wechsel Datenträger.  

- **Schreibzugriff auf nicht durch BitLocker geschützte Wechseldatenträger**  
  **Standardeinstellung:** Nicht konfiguriert  
  BitLocker CSP: [removabledrivesrequirements Encryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Blockieren**: Gewähren Sie nur Lesezugriff auf nicht durch BitLocker geschützte Datenträger.  
  - **Nicht konfiguriert** : standardmäßig Lese-und Schreibzugriff auf Daten Laufwerke, die nicht verschlüsselt sind.  

  Wenn *Aktivieren* festgelegt ist, können Sie die folgende Einstellung konfigurieren:  

  - **Schreibzugriff auf in einer anderen Organisation konfigurierte Geräte**  
    **Standardeinstellung:** Nicht konfiguriert  

    - **Blockieren**: Blockieren Sie den Schreibzugriff auf in einer anderen Organisation konfigurierte Geräte.  
    - **Nicht konfiguriert** : Schreibzugriff verweigern.  
 
## <a name="microsoft-defender-exploit-guard"></a>Microsoft Defender Exploit Guard  

Verwenden Sie [Exploit Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) zum Verwalten und reduzieren der Angriffsfläche von apps, die von ihren Mitarbeitern verwendet werden.  

### <a name="attack-surface-reduction"></a>Verringerung der Angriffsfläche  

Regeln zur Verringerung der Angriffsfläche helfen dabei, Verhaltens Schadsoftware zu verhindern, mit der häufig von Schadsoftware infiziert wird  

#### <a name="attack-surface-reduction-rules"></a>Regeln zur Verringerung der Angriffsfläche  

- **Abgreifen von Anmeldeinformationen über das Subsystem der lokalen Sicherheitsautorität von Windows kennzeichnen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Diebstahl von Anmeldeinformationen aus dem Subsystem für die lokale Sicherheitsautorität (lsass.exe) von Windows blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  Wehren Sie Aktionen und Apps ab, die üblicherweise von Schadsoftware verwendet wird, die nach Sicherheitsproblemen sucht, um Computer zu infizieren.  

  - **Nicht konfiguriert**  
  - **Aktivieren**: Kennzeichnen Sie das Abgreifen von Anmeldeinformationen über das Subsystem zur lokalen Sicherheitsautorität von Windows (lsass.exe).  
  - **Nur überwachen**  

- **Prozesserstellung aus Adobe Reader (Beta)**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Blockieren der Erstellung untergeordneter Prozesse durch Adobe Reader](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **Nicht konfiguriert**  
  - **Aktivieren** : untergeordnete Prozesse blockieren, die aus dem Adobe Reader erstellt werden.  
  - **Nur überwachen**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Regeln zum Verhindern von Bedrohungen durch Office-Makros  

Blockieren Sie folgende Aktionen, die Office-Apps durchführen können:  

- **Einschleusung von Code durch Office-Apps in andere Prozesse (keine Ausnahmen)**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Einschleusung von Code durch Office-Anwendungen in andere Prozesse blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **Nicht konfiguriert**  
  - **Blockieren** Sie das Einfügen von Office-Apps in andere Prozesse.  
  - **Nur überwachen**  

- **Erstellung ausführbarer Inhalte in Office-Apps und -Makros**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Erstellung ausführbarer Inhalte durch Office-Anwendungen blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **Nicht konfiguriert**  
  - **Blockieren** Sie die Erstellung ausführbarer Inhalte durch Office-Apps und-Makros.  
  - **Nur überwachen**  

- **Starten untergeordneter Prozesse in Office-Apps**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Alle Office-Anwendungen am Erstellen von untergeordneten Prozessen hindern](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **Nicht konfiguriert**  
  - **Blockieren** Sie das Starten untergeordneter Prozesse durch Office-Apps.  
  - **Nur überwachen**  
  
- **Win32-Importe aus Office-Makrocode**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Win32-API-Aufrufe über Office-Makros blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **Nicht konfiguriert**  
  - **Blockieren** Sie Win32-Importe aus Makro Code in Office.  
  - **Nur überwachen**  
  
- **Prozesserstellung über Office-Kommunikationsprodukte**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: die [Einrichtung von untergeordneten Prozessen durch die Office-Kommunikationsanwendung blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **Nicht konfiguriert**  
  - **Aktivieren** : untergeordnete Prozesserstellung aus Office Communications apps blockieren.  
  - **Nur überwachen**  

#### <a name="rules-to-prevent-script-threats"></a>Regeln zum Verhindern von Bedrohungen durch Skripts  

Blockieren Sie diese Optionen, um Bedrohungen durch Skripts zu verhindern:  

- **Verborgener JS-/VBS-/PS-/Makrocode**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Ausführung möglicherweise verschleierter Skripts blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **Nicht konfiguriert**  
  - **Blockieren** Sie alle verborgenen js/VBS/PS/Makro-Code.  
  - **Nur überwachen**  

- **Ausführung von aus dem Internet heruntergeladener Nutzlast über JS/VBS (keine Ausnahmen)**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Starten heruntergeladener ausführbarer Inhalte durch JavaScript oder VBScript blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **Nicht konfiguriert**  
  - **Blockieren** Sie die Ausführung von Nutzlast, die aus dem Internet heruntergeladen wurde, von JS/VBS  
  - **Nur überwachen**  

- **Prozesserstellung über die Befehle „PSExec“ und „WMI“**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Blockiert Prozesserstellungen über die Befehle „PSExec“ und „WMI“](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **Nicht konfiguriert**  
  - **Blockieren**: Blockiert Prozesserstellungen über die Befehle „PSExec“ und „WMI“.  
  
  - **Nur überwachen**  

- **Nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Nicht vertrauenswürde und nicht signierte Prozess, die von USB ausgeführt werden, blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **Nicht konfiguriert**  
  - **Blockieren**: Blockiert nicht vertrauenswürdige und nicht signierte Prozesse, die über USB ausgeführt werden.  
  - **Nur überwachen**  
  
- **Ausführbare Dateien, die keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Ausführbare Dateien an der Ausführung hindern, außer sie erfüllen Kriterium zur Verbreitung, zum Alter oder zu vertrauenswürdigen Listen](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **Nicht konfiguriert**  
  - **Blockieren**: Blockiert das Ausführen ausführbarer Dateien, wenn sie keinem Listenkriterium zur Verbreitung, zum Alter oder zur Vertrauenswürdigkeit entsprechen.  
  - **Nur überwachen**  

#### <a name="rules-to-prevent-email-threats"></a>Regeln zum Verhindern von Bedrohungen durch E-Mails  

Blockieren Sie diese Optionen, um Bedrohungen durch E-Mails zu verhindern:  

- **Ausführung ausführbarer Inhalte (EXE, DLL, PS, JS, VBS usw.), die per E-Mail (Webmail-/E-Mail-Client) zugestellt werden (keine Ausnahmen)**  
  **Standardeinstellung:** Nicht konfiguriert  
  Regel: [Ausführbare Inhalte von E-Mail-Clients und Webmail blockieren](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **Nicht konfiguriert**  
  - **Blockieren**: Blockiert die Ausführung ausführbarer Inhalte (EXE, DLL, PS, JS, VBS usw.), die per E-Mail (Webmail-/E-Mail-Client) zugestellt werden.  
  - **Nur überwachen**  

#### <a name="rules-to-protect-against-ransomware"></a>Regeln zum Schutz vor Ransomware  

- **Erweiterter Schutz vor Ransomware**  
  Standard: Nicht konfiguriert  
  Regel: [Erweiterten Schutz vor Ransomware verwenden](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - **Nicht konfiguriert**  
  - **Aktivieren**: Verwenden Sie einen offensiven Schutz vor Ransomware.  
  - **Nur überwachen**  

#### <a name="attack-surface-reduction-exceptions"></a>Ausnahmen von der Verringerung der Angriffsfläche

- **Von Regeln zur Verringerung der Angriffsfläche auszuschließende Dateien und Ordner**  
  Defender CSP: [angreisurfakereductiononlyausschlüsse](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importieren** Sie eine CSV-Datei, die Dateien und Ordner enthält, die von den Regeln zur Verringerung der Angriffsfläche ausgeschlossen werden.  
  - Manuelles **Hinzufügen** von lokalen Dateien oder Ordnern.  

> [!IMPORTANT]  
> Durch die entsprechenden Antischadsoftwareeinstellungen sollte die Überprüfung der folgenden Verzeichnisse ausgeschlossen werden, damit Win32-Branchenanwendungen ordnungsgemäß installiert und ausgeführt werden können:  
> **Auf X64-Clientcomputern:**  
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **Auf X86-Clientcomputern:**  
> *C:\Program Files\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Überwachter Ordnerzugriff  

[Schützen Sie wichtige Daten](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) vor schädlichen Apps und Bedrohungen, z. B. vor Ransomware.  

- **Ordnerschutz**  
  **Standardeinstellung:** Nicht konfiguriert  
  Defender CSP: [enablecontrolledfolderaccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Hiermit schützen Sie Dateien und Ordner vor unbefugten Änderungen durch bösartige Apps.  

  - **Nicht konfiguriert**  
  - **Aktivieren**  
  - **Nur überwachen**  
  - **Nur die Änderung des Datenträgers blockieren**  
  - **Änderung des Datenträgers überprüfen**  

  Wenn Sie eine andere Konfiguration als *nicht konfiguriert*auswählen, können Sie Folgendes konfigurieren:  
  - **Liste von apps, die Zugriff auf geschützte Ordner haben**  
    Defender CSP: [controlledfolderaccesszuweisung](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importieren** Sie eine CSV-Datei, die eine APP-Liste enthält.  
    - **Fügen Sie** dieser Liste manuell apps hinzu.  

  - **Liste der zusätzlichen Ordner, die geschützt werden müssen**  
    Defender CSP: [controlledfolderaccessprotectedfolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importieren** Sie eine CSV-Datei, die eine Ordnerliste enthält.  
    - **Fügen Sie** dieser Liste manuell Ordner hinzu.  

### <a name="network-filtering"></a>Netzwerkfilterung  

Blockieren Sie ausgehende Verbindungen von jeder APP an IP-Adressen oder Domänen mit geringem Ruf. Die Netzwerk Filterung wird sowohl im Überwachungs-als auch im Block Modus unterstützt.  

- **Netzwerkschutz**  
  **Standardeinstellung:** Nicht konfiguriert  
  Defender CSP: [enablenetworkprotection](https://go.microsoft.com/fwlink/?linkid=872618)  

  Die Absicht dieser Einstellung besteht darin, Endbenutzer vor Apps mit Zugriff auf Phishing-Scams, Exploit-Hosting-Websites und böswillige Inhalte im Internet zu schützen. Außerdem wird verhindert, dass Browser von Drittanbietern Verbindungen mit gefährlichen Websites herstellen.  

  - **Nicht konfiguriert**: Deaktivieren Sie dieses Feature. Die Verbindung von Benutzern und Apps mit gefährlichen Domänen wird nicht blockiert. Administratoren wird diese Aktivität im Microsoft Defender Security Center nicht angezeigt.  
  - **Aktivieren: Aktivieren** Sie den Netzwerk Schutz, und blockieren Sie die Verbindung von Benutzern und Apps mit gefährlichen Domänen. Administratoren wird diese Aktivität im Microsoft Defender Security Center angezeigt.  
  - **Nur**überwachen:-Benutzer und apps werden nicht für das Herstellen einer Verbindung mit gefährlichen Domänen gesperrt. Administratoren wird diese Aktivität im Microsoft Defender Security Center angezeigt.  

### <a name="exploit-protection"></a>Exploit-Schutz  

- **XML hochladen**  
  **Standard**: *Nicht konfiguriert*  

  Erstellen Sie eine XML-Datei, die die gewünschten Einstellungen für System-und Anwendungs Entschärfung enthält, um den Schutz [von Geräten vor Exploits mithilfe von](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)Exploit Protection zu schützen. Es gibt zwei Methoden zum Erstellen der XML-Datei:  

  - *PowerShell*: Verwenden Sie mindestens eines der PowerShell-Cmdlets *Get-ProcessMitigation*, *Set-ProcessMitigation* und *ConvertTo-ProcessMitigationPolicy*. Die Cmdlets konfigurieren Einstellungen zur Risikominderung und exportieren eine XML-Darstellung von ihnen.  

  - *Benutzeroberfläche von Microsoft Defender Security Center*: Klicken Sie im Microsoft Defender Security Center auf „App- und Browsersteuerung“, und scrollen Sie zum unteren Ende des entsprechenden Bildschirms, um den Exploit-Schutz zu finden. Verwenden Sie zuerst die Registerkarten „Systemeinstellungen“ und „Programmeinstellungen“, um die Einstellungen für die Risikominderung zu konfigurieren. Suchen Sie anschließend den Link mit den Exporteinstellungen im unteren Bildschirmbereich, um eine XML-Darstellung zu exportieren.  

- **Benutzer Bearbeitung der Exploit-Schutz Schnittstelle**  
  **Standardeinstellung:** Nicht konfiguriert  
  Exploitguard-CSP: [exploitschutzsettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Blockieren** : Laden Sie eine XML-Datei hoch, die es Ihnen ermöglicht, Arbeitsspeicher-, Ablauf Steuerungs-und Richtlinien Einschränkungen zu konfigurieren. Die Einstellungen in der XML-Datei können eine Anwendung vor Exploits schützen.  
  - **Nicht konfiguriert** : Es wird keine benutzerdefinierte Konfiguration verwendet.  

## <a name="microsoft-defender-application-control"></a>Microsoft Defender-Anwendungssteuerung  

Wählen Sie zusätzliche Apps aus, die entweder von überwacht werden müssen oder die von Microsoft Defender Application Control als vertrauenswürdig eingestuft werden. Windows-Komponenten und alle Apps aus dem Windows Store werden automatisch als zur Ausführung vertrauenswürdig eingestuft.  


- **Anwendungs Steuerungs Code-Integritäts Richtlinien**  
  **Standardeinstellung:** Nicht konfiguriert  
   CSP: [AppLocker CSP](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Erzwingen** : Wählen Sie die Anwendungs Steuerungs Code-Integritäts Richtlinien für die Geräte ihrer Benutzer aus.  
  
    Sobald die Anwendungssteuerung auf einem Gerät aktiviert wurde, kann sie nur noch deaktiviert werden, indem der Modus von *Erzwingen* in *Nur überwachen* geändert wird. Wenn der Modus von *Erzwingen* in *Nicht konfiguriert* geändert wird, wird die Anwendungssteuerung weiterhin auf zugewiesenen Geräten erzwungen.  

  - **Nicht konfiguriert** : die Anwendungssteuerung wurde nicht den Geräten hinzugefügt. Einstellungen, die zuvor hinzugefügt wurden, werden jedoch weiterhin auf zugewiesenen Geräten erzwungen. 
 
  - **Nur** überwachen: Anwendungen werden nicht blockiert. Alle Ereignisse werden in den Protokollen des lokalen Clients protokolliert.  

## <a name="microsoft-defender-credential-guard"></a>Microsoft Defender Credential Guard  

Microsoft Defender Credential Guard schützt vor Angriffen zum Diebstahl von Anmeldeinformationen. Geheime Schlüssel werden isoliert, damit nur privilegierte Systemsoftware darauf zugreifen kann.  

- **Credential Guard**  
  **Standard**: Deaktivieren  
  [Deviceguard-CSP](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Deaktivieren**: Deaktiviert Credential Guard per Remoteverbindung, wenn das Programm zuvor über die Option **Ohne UEFI-Sperre aktivieren** aktiviert wurde.  

  - **Mit UEFI-Sperre aktivieren**: Credential Guard kann nicht per Remoteverbindung mit einem Registrierungsschlüssel oder über eine Gruppenrichtlinie deaktiviert werden.  

    > [!NOTE]
    > Wenn Sie diese Einstellung verwenden und dann später Credential Guard deaktivieren möchten, müssen Sie die Gruppenrichtlinie auf **Deaktiviert** setzen. Außerdem müssen Sie die UEFI-Konfigurationsinformationen physisch von den einzelnen Computern löschen. Solange die UEFI-Konfiguration bestehen bleibt, ist Credential Guard weiter aktiviert.  

  - **Ohne UEFI-Sperre aktivieren**: Ermöglicht, Credential Guard über eine Remoteverbindung mithilfe einer Gruppenrichtlinie zu deaktivieren. Die Geräte, die diese Einstellung verwenden, müssen Windows 10 (Version 1511) oder höher ausführen.  

  Wenn Sie Credential Guard *aktivieren*, werden auch die folgenden erforderlichen Features aktiviert:  
  
  - **Virtualization-based Security (VBS)** (Virtualisierungsbasierte Sicherheit (VBS))  
    Wird im Rahmen des nächsten Neustarts aktiviert. Virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen.  
  - **Sicherer Start und DMA-Schutz**  
    Aktiviert die VBS mit den Schutzmaßnahmen für sicheren Start und DMA (Direct Memory Access, direkter Speicherzugriff). Für die DMA-Schutzfunktionen ist Hardwaresupport erforderlich. Außerdem werden sie nur auf richtig konfigurierten Geräten aktiviert.  

## <a name="microsoft-defender-security-center"></a>Microsoft Defender Security Center  

Microsoft Defender Security Center fungiert als separate App bzw. separater Prozess der einzelnen Features. Sie zeigt Benachrichtigungen über das Info-Center an. Sie dienst als Collector oder zentraler Ort, um den Status anzuzeigen und Konfigurationen für die verschiedenen Features auszuführen. Weitere Informationen finden Sie in den [Microsoft Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) docs.  

### <a name="microsoft-defender-security-center-app-and-notifications"></a>Microsoft Defender Security Center-App und -Benachrichtigungen  

Blockieren Sie den Benutzerzugriff auf die verschiedenen Bereiche der Microsoft Defender Security Center-App. Durch das Ausblenden eines Abschnitts werden auch die zugehörigen Benachrichtigungen blockiert.  

- **Viren- und Bedrohungsschutz**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disablevirusui](https://go.microsoft.com/fwlink/?linkid=873662)  

  Konfigurieren Sie, ob Endbenutzer den Bereich Viren-und Bedrohungsschutz im Microsoft Defender-Security Center anzeigen können. Durch das Ausblenden dieses Abschnitts werden auch alle Benachrichtigungen im Zusammenhang mit Viren-und Bedrohungsschutz blockiert.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Schutz vor Ransomware**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [hideransomwaredatarecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Hiermit wird konfiguriert, ob Endbenutzer den Schutzbereich für Ransomware im Microsoft Defender-Security Center anzeigen können. Wenn Sie diesen Abschnitt ausblenden, werden auch alle Benachrichtigungen im Zusammenhang mit dem Schutz vor Ransomware blockiert.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Konto Schutz**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disableaccountschutzui](https://go.microsoft.com/fwlink/?linkid=873666)  

  Hiermit wird konfiguriert, ob Endbenutzer den Bereich "Konto Schutz" im Microsoft Defender-Security Center anzeigen können. Wenn Sie diesen Abschnitt ausblenden, werden auch alle Benachrichtigungen im Zusammenhang mit dem Konto Schutz blockiert.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Firewall- und Netzwerkschutz**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disablenetworkui](https://go.microsoft.com/fwlink/?linkid=873668)  

  Hiermit wird konfiguriert, ob Endbenutzer den Bereich Firewall und Netzwerk Schutz im Microsoft Defender Security Center anzeigen können. Wenn Sie diesen Abschnitt ausblenden, werden auch alle Benachrichtigungen im Zusammenhang mit der Firewall und dem Netzwerk Schutz blockiert.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **App- und Browsersteuerung**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disableappbrowserui](https://go.microsoft.com/fwlink/?linkid=873669)  

  Hiermit wird konfiguriert, ob Endbenutzer den App-und Browser-Steuerungs Bereich im Microsoft Defender Security Center anzeigen können. Wenn Sie diesen Abschnitt ausblenden, werden auch alle Benachrichtigungen im Zusammenhang mit der APP-und Browser Steuerung blockiert.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Hardware Schutz**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disabledevicesecurityui](https://go.microsoft.com/fwlink/?linkid=873670)  

  Hiermit wird konfiguriert, ob Endbenutzer den Hardware Schutzbereich im Microsoft Defender-Security Center anzeigen können. Durch das Ausblenden dieses Abschnitts werden auch alle Benachrichtigungen im Zusammenhang mit dem Hardware Schutz blockiert.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Geräteleistung und -integrität**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disablehealthui](https://go.microsoft.com/fwlink/?linkid=873671)  

  Hiermit wird konfiguriert, ob Endbenutzer den Bereich Geräteleistung und-Integrität im Microsoft Defender Security Center anzeigen können. Durch das Ausblenden dieses Abschnitts werden auch alle Benachrichtigungen im Zusammenhang mit der Geräteleistung und-Integrität blockiert.  
  
  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Familienoptionen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disablefamilyui](https://go.microsoft.com/fwlink/?linkid=873673)  

  Konfigurieren Sie, ob Endbenutzer den Bereich Familien Optionen im Microsoft Defender Security Center anzeigen können. Durch das Ausblenden dieses Abschnitts werden auch alle Benachrichtigungen im Zusammenhang mit den Familien Optionen blockiert.  
  
  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Benachrichtigungen aus den angezeigten Bereichen der App**  
  **Standardeinstellung:** Nicht konfiguriert  
  Windowsdefendersecuritycenter CSP: [disableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  Wählen Sie aus, welche Benachrichtigungen Endbenutzern angezeigt werden. Zu den nicht kritischen Benachrichtigungen gehören Zusammenfassungen der Aktivitäten von Microsoft Defender Antivirus, Benachrichtigungen zum Abschluss von Überprüfungen eingeschlossen. Alle übrigen Benachrichtigungen gelten als kritisch.  

  - **Nicht konfiguriert**  
  - **Nicht kritische Benachrichtigungen blockieren**  
  - **Alle Benachrichtigungen blockieren**  

- **Symbol "Windows-Security Center" in der Taskleiste**  
  **Standardeinstellung:** Nicht konfiguriert  

  Konfigurieren Sie die Anzeige des Benachrichtigungs Bereichs-Steuer Elements. Der Benutzer muss sich abmelden und anmelden oder den Computer neu starten, damit diese Einstellung wirksam wird.  
  
  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **TPM-Schaltfläche Löschen**  
  **Standardeinstellung:** Nicht konfiguriert  

  Konfigurieren Sie die Anzeige der Schaltfläche TPM löschen.  
  
  - **Nicht konfiguriert**  
  - **Deaktivieren**  

- **Warnung zur Aktualisierung der TPM-Firmware**  
  **Standardeinstellung:** Nicht konfiguriert  
  
  Konfigurieren Sie die Anzeige der Update-TPM-Firmware, wenn eine anfällige Firmware erkannt wird.  

  - **Nicht konfiguriert**  
  - **Ausblenden**  

- **Schutz manipulieren**  
  **Standardeinstellung:** Nicht konfiguriert

  Aktivieren bzw. deaktivieren Sie den Manipulationsschutz auf Geräten. Um den Manipulationsschutz zu verwenden, müssen Sie [Microsoft Defender Advanced Threat Protection in InTune integrieren](advanced-threat-protection.md)und über [Enterprise Mobility + Security E5-Lizenzen](../fundamentals/licenses.md)verfügen.  
  - **Nicht konfiguriert** : an den Geräteeinstellungen wird keine Änderung vorgenommen.
  - **Aktiviert** : Manipulationsschutz ist aktiviert, und Einschränkungen werden auf Geräten erzwungen.
  - **Deaktiviert** -Manipulationsschutz ist deaktiviert, und Einschränkungen werden nicht erzwungen.

### <a name="it-contact-information"></a>IT-Kontaktinformationen  

Stellen Sie IT-Kontaktinformationen bereit, die in der Microsoft Defender Security Center-App und in den App-Benachrichtigungen angezeigt werden.  

Sie können **In Apps und Benachrichtigungen anzeigen**, **Nur in App anzeigen**, **Nur in Benachrichtigungen anzeigen** oder **Don‘t display** (Nicht anzeigen) auswählen. Geben Sie den **Namen der IT-Organisation** und mindestens eine der folgenden Kontaktoptionen ein:  


- **IT-Kontaktinformationen**  
  **Standard**: nicht anzeigen  
  Windowsdefendersecuritycenter CSP: [enablecustomizeddeasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Legen Sie fest, wo IT-Kontaktinformationen für Endbenutzer angezeigt werden sollen.  
  
  - **In App und in Benachrichtigungen anzeigen**  
  - **Nur in App anzeigen**  
  - **Nur in Benachrichtigungen anzeigen**  
  - **Nicht anzeigen**  

  Wenn die Konfiguration für die Anzeige konfiguriert ist, können Sie die folgenden Einstellungen konfigurieren:  

  - **Name der IT-Organisation**  
    **Standard**: *Nicht konfiguriert*  
    Windowsdefendersecuritycenter CSP: [CompanyName](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **Telefonnummer oder Skype-ID der IT-Abteilung**  
    **Standard**: *Nicht konfiguriert*  
    Windowsdefendersecuritycenter CSP: [Telefon](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **E-Mail-Adresse der IT-Abteilung**  
    **Standard**: *Nicht konfiguriert*  
    Windowsdefendersecuritycenter CSP: [e-Mail](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **URL der IT-Supportwebsite**  
    **Standard**: *Nicht konfiguriert*  
    Windowsdefendersecuritycenter CSP: [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Sicherheitsoptionen für lokale Geräte  

Konfigurieren Sie mit diesen Optionen die lokalen Sicherheitseinstellungen auf Windows 10-Geräten.  

### <a name="accounts"></a>Konten  

- **Neue Microsoft-Konten hinzufügen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Blockieren**: Verhindert, dass Benutzer diesem Gerät neue Microsoft-Konten hinzufügen.  
  - **Nicht konfiguriert** : Benutzer können Microsoft-Konten auf dem Gerät verwenden.  

- **Remoteanmeldung ohne Kennwort**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Blockieren**: Nur lokale Konten ohne Kennwörter können über die Tastatur des Geräts angemeldet werden.  
   - **Nicht konfiguriert**: Lokale Konten ohne Kennwort können sich auch von anderen Standorten als dem physischen Gerät aus anmelden.  

#### <a name="admin"></a>Administrator  

- **Lokales Administratorkonto**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Blockieren** Verhindern der Verwendung eines lokalen Administrator Kontos.  
  - **Nicht konfiguriert**  

- **Administratorkonto umbenennen**  
  **Standard**: *Nicht konfiguriert*  
  Localpoliciessecurityoptions CSP: [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Definieren Sie einen anderen Kontonamen, der der Sicherheits-ID (SID) für das Administratorkonto zugeordnet werden soll.  

 #### <a name="guest"></a>Gast  

- **Gastkonto**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [localpoliciessecurityoptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Blockieren** : verhindern der Verwendung eines Gastkontos.  
  - **Nicht konfiguriert**  

- **Gastkonto umbenennen**  
  **Standard**: *Nicht konfiguriert*  
  Localpoliciessecurityoptions CSP: [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Definieren Sie einen anderen Kontonamen, der der Sicherheits-ID (SID) für das Gastkonto zugeordnet werden soll.  

### <a name="devices"></a>Geräte  

- **Gerät ohne Anmeldung abdocken**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Blockieren**: Benutzer können auf die physische Schaltfläche zum Auswerfen eines angedockten portablen Geräts drücken, um dieses sicher abzudocken.  
  - **Nicht konfiguriert** : ein Benutzer muss sich am Gerät anmelden und die Berechtigung zum Abdocken des Geräts erhalten.  

- **Druckertreiber für freigegebene Drucker installieren**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Aktiviert**: Alle Benutzer können einen Druckertreiber installieren, wenn sie eine Verbindung mit einem freigegebenen Drucker herstellen.  
  - **Nicht konfiguriert**: Nur Administratoren können einen Druckertreiber installieren, wenn sie eine Verbindung mit einem freigegebenen Drucker herstellen.  

- **CD-ROM-Zugriff auf lokale aktive Benutzer beschränken**  
  **Standard**: Nicht konfiguriert  
  CSP: [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Aktiviert**: Nur der interaktiv angemeldete Benutzer kann CD-ROM-Medien verwenden. Wenn diese Richtlinie aktiviert ist und kein Benutzer interaktiv angemeldet ist, wird über das Netzwerk auf die CD-ROM zugegriffen.  
  - **Nicht konfiguriert** : jeder Benutzer hat Zugriff auf die CD-ROM.  

- **Wechselmedien formatieren und auswerfen**  
  **Standard**: Administratoren  
  CSP: [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  Definieren Sie, wer NTFS-Medien formatieren und auswerfen darf:  
  - **Nicht konfiguriert**  
  - **Administratoren**  
  - **Administratoren und Poweruser**  
  - **Administratoren und interaktive Benutzer**  

### <a name="interactive-logon"></a>Interaktive Anmeldung  

- **Minutes of lock screen inactivity until screen saver activates** (Inaktivität in Minuten für Anmeldebildschirm bis zur Aktivierung des Bildschirmschoners)  
  **Standard**: *Nicht konfiguriert*  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  Geben Sie an, wie viele Minuten auf dem Anmeldebildschirm des interaktiven Desktops maximal Inaktivität herrschen darf, bis sich der Bildschirmschoner einschaltet. (**0** - **99999**)  

- **STRG+ALT+ENTF zur Anmeldung erforderlich**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Aktivieren**: Benutzer müssen STRG+ALT+ENTF drücken, um sich anzumelden.  
  - **Nicht konfiguriert**: Benutzer müssen STRG+ALT+ENTF drücken, bevor sie sich bei Windows anmelden.  

- **Smart card removal behavior** (Verhalten beim Entfernen von Smartcards)  
  **Standard**: Arbeitsstation sperren   
  Localpoliciessecurityoptions CSP: [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  Bestimmt, was geschieht, wenn die Smartcard für einen angemeldeten Benutzer aus dem Smartkartenleser entfernt wird. Folgende Optionen sind verfügbar:  

  - **Arbeitsstation sperren**: Die Arbeitsstation wird gesperrt, wenn die Smartcard entfernt wird. Diese Option ermöglicht es dem Benutzer, den Bereich zu verlassen, die Smartcard mitzunehmen und dennoch eine geschützte Sitzung beizubehalten.  
  - **Keine Aktion**  
  - **Abmeldung erzwingen**: Der Benutzer wird automatisch abgemeldet, wenn die Smartcard entfernt wird.  
  - **Bei Remotedesktopdienste-Sitzung trennen**: Das Entfernen der Smartcard beendet die Sitzung, ohne den Benutzer abzumelden. Diese Option ermöglicht es dem Benutzer, die Smartcard einzulegen und die Sitzung später oder auf einem anderen Computer mit Smartcard-Leser fortzusetzen, ohne sich erneut anmelden zu müssen. Wenn die Sitzung lokal stattfindet, funktioniert diese Richtlinie genau wie „Arbeitsstation sperren“.  

#### <a name="display"></a>Anzeige  

- **Benutzerinformationen auf Sperrbildschirm**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  Konfigurieren Sie die Benutzerinformationen, die angezeigt werden, wenn die Sitzung gesperrt ist. Wenn nicht konfiguriert, werden Anzeigename des Benutzers, Domäne und Benutzername angezeigt.  

  - **Nicht konfiguriert**  
  - **Anzeigename des Benutzers, Domäne und Benutzername**  
  - **Nur Anzeigename des Benutzers**  
  - **Benutzerinformationen nicht anzeigen**  

- **Zuletzt angemeldeten Benutzer ausblenden**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Aktivieren** : Blenden Sie den Benutzernamen aus.  
  - **Nicht konfiguriert** : der letzte Benutzername wird angezeigt.  

- **Benutzernamen bei der Anmeldung ausblenden**
  **Standard**: nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Aktivieren** : Blenden Sie den Benutzernamen aus.  
  - **Nicht konfiguriert** : der letzte Benutzername wird angezeigt.  

- **Logon message title** (Titel der Anmeldenachricht)  
  **Standard**: *Nicht konfiguriert*  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  Legen Sie den Nachrichtentitel für Benutzer fest, die sich anmelden.  

- **Logon message text** (Text der Anmeldenachricht)  
  **Standard**: *Nicht konfiguriert*  
  Localpoliciessecurityoptions CSP: [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  Legen Sie den Nachrichtext für Benutzer fest, die sich anmelden.  
  
### <a name="network-access-and-security"></a>Netzwerkzugriff und Sicherheit

- **Anonymer Zugriff auf Named Pipes und Freigaben**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Nicht konfiguriert**: Schränken Sie den anonymen Zugriff auf Freigabe- und Named Pipe-Einstellungen ein. Gilt für die Einstellungen, auf die anonym zugegriffen werden kann.  
  - **Blockieren** : Deaktivieren Sie diese Richtlinie, sodass anonymer Zugriff verfügbar ist.  

- **Anonyme Aufzählung von SAM-Konten**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **Nicht konfiguriert** : anonyme Benutzer können SAM-Konten aufzählen.  
  - **Blockieren**: Verhindern Sie anonyme Enumerationen von SAM-Konten.  

- **Anonyme Aufzählung von SAM-Konten und Freigaben**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Nicht konfiguriert**: Anonyme Benutzer können die Namen der Domänenkonten und Netzwerkfreigaben auflisten.  
  - **Blockieren**: Verhindern Sie die anonyme Aufzählung von SAM-Konten und Freigaben. 

- **LAN-Manager-Hashwert bei Kennwortänderung speichern**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Bestimmen Sie, ob der Hashwert für Kenn Wörter beim nächsten ändern des Kennworts gespeichert wird. 
  - **Nicht konfiguriert** : der Hashwert wird nicht gespeichert.  
  - **Block** : der LAN-Manager (LM) speichert den Hashwert für das neue Kennwort.  

- **PKU2U-Authentifizierungsanforderungen**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **Nicht konfiguriert**: PU2U-Anforderungen zulassen.  
  - **Blockieren** Sie PKU2U-Authentifizierungsanforderungen an das Gerät.  

- **RPC-Remoteverbindungen mit SAM einschränken**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **Nicht konfiguriert** : Verwenden Sie die Standard Sicherheits Beschreibung, die es Benutzern und Gruppen ermöglicht, Remote-RPC-Aufrufe an Sam durchführen.
  - **Zulassen** : Verweigern von Remote-RPC-Aufrufen an den Security Accounts Manager (Sam), der Benutzerkonten und Kenn Wörter speichert. Mit **zulassen** können Sie auch die Standard Zeichenfolge der Sicherheits Deskriptor-Definitions Sprache (SDDL) ändern, um Benutzern und Gruppen das Ausführen dieser Remote Aufrufe explizit zu gestatten oder zu verweigern.  

    - **Sicherheitsbeschreibung**  
      **Standard**: *Nicht konfiguriert*  
    
- **Minimum session security for NTLM SSP based clients** (Minimale Sitzungssicherheit für NTLM-basierte SSP-Clients)  
  **Standard**Wert: keine  
  Localpoliciessecurityoptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Mit dieser Sicherheitseinstellung kann die Aushandlung der 128-Bit-Verschlüsselung und bzw. oder der NTLMv2-Sitzungssicherheit für einen Server als erforderlich festgelegt werden.  

  - **Keine**  
  - **NTLMv2-Sitzungssicherheit erfordern**  
  - **128-Bit-Verschlüsselung erfordern**  
  - **NTLMv2- und 128-Bit-Verschlüsselung erfordern**  
 
- **Minimum session security for NTLM SSP based servers** (Minimale Sitzungssicherheit für NTLM-basierte SSP-Server)  
  **Standard**Wert: keine  
  Localpoliciessecurityoptions CSP: [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Mit dieser Sicherheitseinstellung wird festgelegt, welches Abfrage/Antwort-Authentifizierungsprotokoll für Netzwerkanmeldungen verwendet wird.  

  - **Keine**  
  - **NTLMv2-Sitzungssicherheit erfordern**  
  - **128-Bit-Verschlüsselung erfordern**  
  - **NTLMv2- und 128-Bit-Verschlüsselung erfordern**  

- **LAN-Manager-Authentifizierungs Ebene**  
  **Standard**: LM und NTLM  
  Localpoliciessecurityoptions CSP: [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM und NTLM**  
  - **LM, NTLM und NTLMv2**  
  - **NTLM**  
  - **NTLMv2**  
  - **NTLMv2 und nicht LM**  
  - **NTLMv2, nicht LM oder NTLM**  
  
- **Unsichere Gast Anmeldungen**  
  **Standardeinstellung:** Nicht konfiguriert  
  LanmanWorkstation CSP: [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Wenn Sie diese Einstellung aktivieren, lehnt der SMB-Client unsichere Gast Anmeldungen ab.  

  - **Nicht konfiguriert**  
  - **Blockieren** : der SMB-Client lehnt unsichere Gast Anmeldungen ab.  

### <a name="recovery-console-and-shutdown"></a>Wiederherstellungskonsole und Herunterfahren  

- **Virtuellen Arbeitsspeicher beim Herunterfahren löschen**  
  **Standardeinstellung:** Nicht konfiguriert  
   Localpoliciessecurityoptions CSP: [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Aktivieren**: Der virtuelle Arbeitsspeicher wird beim Herunterfahren des Geräts gelöscht.  
  - **Nicht konfiguriert**: Der virtuelle Arbeitsspeicher wird nicht gelöscht.  

- **Shut down without log on** (Herunterfahren ohne Anmeldung)  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Blockieren**: Auf dem Windows-Anmeldebildschirm wird die Option zum Herunterfahren ausgeblendet. Benutzer müssen sich beim Gerät anmelden und es dann herunterfahren.  
  - **Nicht konfiguriert**: Benutzer können das Gerät über den Windows-Anmeldebildschirm herunterfahren.  

### <a name="user-account-control"></a>Benutzerkontensteuerung  

- **UIA-Integrität ohne sicheren Speicherort**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **Block** -apps, die sich an einem sicheren Ort im Dateisystem befinden, werden nur mit der UIAccess-Integrität ausgeführt.  
  - **Nicht konfiguriert**: Apps können mit UIAccess-Integrität ausgeführt werden, auch wenn sie sich nicht an einem sicheren Ort im Dateisystem befinden.  

- **Fehler bei Schreibvorgängen für Dateien und Registrierung basierend auf Benutzerspeicherorten virtualisieren**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Aktiviert**: Bei Anwendungen, die Daten in geschützte Orte schreiben, treten Fehler auf.  
  - **Nicht konfiguriert**. Anwendungsschreibfehler werden zur Laufzeit sowohl für das Dateisystem als auch für die Registrierung an festgelegte Benutzerstandorte weitergeleitet.  

- **Rechte nur für ausführbare Dateien erhöhen, die signiert und validiert wurden**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Aktiviert**: Erzwingen Sie die PKI-Zertifizierungspfadüberprüfung für eine ausführbare Datei vor ihrer Ausführung.  
  - **Nicht konfiguriert**: Erzwingen Sie keine Überprüfung des PKI-Zertifizierungspfads, bevor eine ausführbare Datei ausgeführt werden kann.  

#### <a name="uia-elevation-prompt-behavior"></a>Verhalten der UIA-Eingabeaufforderung für erhöhte Rechte  

- **Eingabeaufforderung für erhöhte Rechte für Administratoren**  
  **Standard**: Eingabeaufforderung zur Zustimmung für Nicht-Windows-Binärdateien  
  Localpoliciessecurityoptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Definieren Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Administratoren im Administratorgenehmigungsmodus.  

  - **Nicht konfiguriert**  
  - **Rechte ohne Eingabeaufforderung erhöhen**  
  - **Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop**  
  - **Eingabeaufforderung zu Anmeldeinformationen**  
  - **Eingabeaufforderung zur Zustimmung**  
  - **Zustimmungsaufforderung für Nicht-Windows-Binärdateien**  


- **Eingabeaufforderung für erhöhte Rechte für Standardbenutzer**  
  **Standard**: Eingabeaufforderung zu Anmeldeinformationen  
  Localpoliciessecurityoptions CSP: [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  Definieren Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Standardbenutzer.  

  - **Nicht konfiguriert**  
  - **Anforderungen für erhöhte Rechte automatisch ablehnen**  
  - **Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop**  
  - **Eingabeaufforderung zu Anmeldeinformationen**  

- **Eingabeaufforderung für erhöhte Rechte an interaktiven Desktop des Benutzers umleiten**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Aktiviert** : alle Anforderungen für erhöhte Rechte an den Desktop des interaktiven Benutzers anstatt an den sicheren Desktop. Alle Richtlinieneinstellungen für das Verhalten der Eingabeaufforderung für Administratoren und Standardbenutzer werden verwendet.  
  - **Nicht konfiguriert**: Erzwingen Sie, dass alle Anforderungen für erhöhte Rechte an den sicheren Desktop umgeleitet werden, unabhängig von den Richtlinieneinstellungen für das Verhalten der Eingabeaufforderung für Administratoren und Standardbenutzer.

- **Eingabeaufforderung für erhöhte Rechte bei App-Installationen**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Aktiviert**: Anwendungsinstallationspakete werden nicht erkannt, und es wird keine Eingabeaufforderung für erhöhte Rechte angezeigt.
   - **Nicht konfiguriert**: Benutzer werden aufgefordert, den Benutzernamen und das Kennwort eines Administrators einzugeben, wenn ein Anwendungsinstallationspaket erhöhte Rechte erfordert.

- **UIA-Eingabeaufforderung für erhöhte Rechte ohne sicheren Desktop**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Aktivieren**: Erlauben Sie, dass UIAccess-Anwendungen erhöhte Rechte ohne sicheren Desktop anfordern können.  
- **Nicht konfiguriert** : Eingabe Aufforderungen für erhöhte Rechte verwenden einen sicheren Desktop.  

#### <a name="admin-approval-mode"></a>Administratorgenehmigungsmodus  

- **Administratorgenehmigungsmodus für integrierten Administrator**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Aktiviert**: Erlauben Sie, dass das integrierte Administratorkonto den Administratorgenehmigungsmodus verwenden kann. Der Benutzer wird bei jedem Vorgang, der eine Rechteerweiterungen erfordert, zur Genehmigung aufgefordert.  
  - **Nicht konfiguriert**: Alle Apps werden mit vollständigen Administratorrechten ausgeführt.  

- **Alle Administratoren im Administratorgenehmigungsmodus ausführen**  
  **Standard**: Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Aktiviert**: Aktivieren Sie den Administrator Genehmigungs Modus.  
  - **Nicht konfiguriert**: Deaktivieren Sie den Administratorgenehmigungsmodus und alle verwandten UAC-Richtlinieneinstellungen.  

### <a name="microsoft-network-client"></a>Microsoft-Netzwerkclient  

- **Kommunikation digital signieren (wenn Server zustimmt)**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  Diese Einstellung legt fest, ob der SMB-Client die SMB-Paketsignatur aushandelt.  
  - **Blockieren** : der SMB-Client aushandiert nie die SMB-Paket Signatur.
  - **Nicht konfiguriert**: Der Microsoft-Netzwerkclient fordert den Server zur Durchführung der SMB-Paketsignatur beim Setup der Sitzung auf. Wenn die Paketsignatur auf dem Server aktiviert ist, wird die Paketsignatur ausgehandelt.  

- **Unverschlüsseltes Kennwort an SMB-Server von Drittanbietern senden**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Blockieren**: Der SMB-Redirector (Server Message Block) kann Klartextkennwörter an SMB-Server senden, die nicht von Microsoft stammen und keine Kennwortverschlüsselung während der Authentifizierung unterstützen.  
  - **Nicht konfiguriert** : blockiert das Senden von nur-Text-Kenn Wörtern. Die Kenn Wörter werden verschlüsselt.  

- **Kommunikation digital signieren (immer)**  
  **Standardeinstellung:** Nicht konfiguriert  
  Localpoliciessecurityoptions CSP: [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Aktivieren**: Der Microsoft-Netzwerkserver kommuniziert nur dann mit einem Microsoft-Netzwerkclient, wenn dieser der SMB-Paketsignatur zustimmt.  
  - **Nicht konfiguriert** : zwischen Client und Server wird eine SMB-Paket Signierung ausgehandelt.  

### <a name="microsoft-network-server"></a>Microsoft-Netzwerkserver  
  
- **Kommunikation digital signieren (wenn Client zustimmt)**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Aktivieren**: Der Microsoft-Netzwerkserver handelt die SMB-Paketsignatur wie vom Client angefordert aus. Genau gesagt: Wenn die Paketsignatur auf dem Client aktiviert ist, wird die Paketsignatur ausgehandelt.  
  - **Nicht konfiguriert** : der SMB-Client aushandiert nie die SMB-Paket Signatur.  

- **Kommunikation digital signieren (immer)**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Aktivieren**: Der Microsoft-Netzwerkserver kommuniziert nur dann mit einem Microsoft-Netzwerkclient, wenn dieser der SMB-Paketsignatur zustimmt.  
  - **Nicht konfiguriert** : zwischen Client und Server wird eine SMB-Paket Signierung ausgehandelt.  

## <a name="xbox-services"></a>Xbox-Dienste

- **Aufgabe zum Speichern des Xbox-Spiels**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [TaskScheduler/enablexboxgamesavetask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Mit dieser Einstellung wird festgelegt, ob die Aufgabe zum Speichern von Xbox-spielen aktiviert ist.  
  - **Enabled**
  - **Nicht konfiguriert**

- **Xbox-Zubehör-Verwaltungsdienst**  
  **Standard**: manuell  
  CSP: [Systemservices/konfigurierten Konfigurations Dienstanbieter-Konfigurations Modus](https://go.microsoft.com/fwlink/?linkid=875481)  

  Mit dieser Einstellung wird der Starttyp des Zubehör Verwaltungs dienstanders bestimmt.  
  - **Manuell**
  - **Automatisch**
  - **Deaktiviert**

- **Xbox Live auth Manager-Dienst**  
  **Standard**: manuell  
  CSP: [Systemservices/konfigurierten Konfigurations-Manager-Modus](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Mit dieser Einstellung wird der Starttyp für den Live auth Manager-Dienst bestimmt.  
  - **Manuell**
  - **Automatisch**
  - **Deaktiviert**
 
- **Xbox Live-Spiel Speicherdienst**  
  **Standard**: manuell  
  CSP: [Systemservices/konfigurierten Konfigurations-boxlivegamesaveservicestartupmode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Mit dieser Einstellung wird der Starttyp für den Live Spiel Speicherdienst bestimmt.  
  - **Manuell**
  - **Automatisch**
  - **Deaktiviert**

- **Xbox Live-Netzwerkdienst**  
  **Standard**: manuell  
  CSP: [Systemservices/konfigurierten Konfigurations-boxlivenetworkingservicestartupmode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Mit dieser Einstellung wird der Starttyp für den Netzwerkdienst bestimmt.  
  - **Manuell**
  - **Automatisch**
  - **Deaktiviert**

## <a name="user-rights"></a>Benutzerrechte

- **Auf Anmeldeinformations-Manager als vertrauenswürdigem Aufrufer zugreifen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/accesscredentialmanagerastrustedcaller](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accesscredentialmanagerastrustedcaller)

  Dieses Benutzerrecht wird von der Anmelde Informationsverwaltung während Sicherungs-und Wiederherstellungs Vorgängen verwendet. Die gespeicherten Anmelde Informationen der Benutzer können kompromittiert werden, wenn diese Berechtigung anderen Entitäten erteilt wird.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Lokales anmelden zulassen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/allowloczuweisung](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-allowlocallogon)

  Dieses Benutzerrecht bestimmt, welche Benutzer sich am Computer anmelden können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Zugriff über das Netzwerk zulassen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/accessfromnetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-accessfromnetwork)

  Dieses Benutzerrecht bestimmt, welche Benutzer und Gruppen über das Netzwerk eine Verbindung mit dem Computer herstellen dürfen.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Agieren als Teil des Betriebssystems**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/actasparser-Betriebssystem](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-actaspartoftheoperatingsystem)

  Agieren als Teil des Betriebssystems
  - **Nicht konfiguriert**
  - **Zulassen**  

- **Dateien und Verzeichnisse sichern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/backupfilesanddirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-backupfilesanddirectories)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer die Berechtigungen Datei, Verzeichnis, Registrierung und andere persistente Objekte beim Sichern von Dateien und Verzeichnissen umgehen können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Systemzeit ändern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/changesystemtime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-changesystemtime)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer und Gruppen die Uhrzeit und das Datum auf der internen Uhr des Computers ändern können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Globale Objekte erstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/kreateglobalobjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createglobalobjects)

  Diese Sicherheitseinstellung bestimmt, ob Benutzer globale Objekte erstellen können, die für alle Sitzungen verfügbar sind. Benutzer, die globale Objekte erstellen können, können sich auf Prozesse auswirken, die unter den Sitzungen anderer Benutzer ausgeführt werden. Dies kann zu einem Anwendungsfehler oder einer Beschädigung von Daten führen.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Auslagerungs Datei erstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/kreatepagefile](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpagefile)

  Dieses Benutzerrecht bestimmt, welche Benutzer und Gruppen eine interne API zum Erstellen und Ändern der Größe einer Auslagerungs Datei abrufen können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Dauerhaft freigegebene Objekte erstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/kreatepermanentsharedobjects](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createpermanentsharedobjects)

  Dieses Benutzerrecht bestimmt, welche Konten von Prozessen zum Erstellen eines Verzeichnis Objekts mit dem Objekt-Manager verwendet werden können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Symbolische Links erstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/kreatesymboliclinks](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createsymboliclinks)

  Dieses Benutzerrecht bestimmt, ob der Benutzer eine symbolische Verknüpfung von dem Computer aus erstellen kann, auf dem Sie angemeldet sind.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Token erstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/kreatetoken](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-createtoken)

  Dieses Benutzerrecht bestimmt, welche Benutzer/Gruppen von Prozessen verwendet werden können, um ein Token zu erstellen, das dann verwendet werden kann, um Zugriff auf lokale Ressourcen zu erhalten, wenn der Prozess eine interne API verwendet, um ein Zugriffs Token zu erstellen.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Programme debuggen**  
  **Standardeinstellung:** Nicht konfiguriert  
    CSP: [Userrights/debugprograms](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-debugprograms)

  Dieses Benutzerrecht bestimmt, welche Benutzer einen Debugger an einen beliebigen Prozess oder an den Kernel anfügen können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Zugriff über Netzwerk verweigern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/denyaccessfromnetwork](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyaccessfromnetwork)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer daran gehindert werden, über das Netzwerk auf einen Computer zuzugreifen.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Anmelden als Dienst verweigern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/denyloczuzuweisung](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denylocallogon)

  Diese Sicherheitseinstellung bestimmt, welche Dienst Konten verhindert werden, dass ein Prozess als Dienst registriert wird.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Anmelden über Remotedesktopdienste verweigern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/denyremotedesktopserviceslogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-denyremotedesktopserviceslogon)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer und Gruppen sich als Remotedesktopdienste Client nicht anmelden dürfen.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Delegierung aktivieren**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/enabledelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-enabledelegation)

 Mit diesem Benutzerrecht wird festgelegt, welche Benutzer die Einstellung "vertrauenswürdige Delegierung" für ein Benutzer-oder Computer Objekt festlegen können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Sicherheitsüberwachungen generieren**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/generatesecurityüberwachungen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-generatesecurityaudits)

  Dieses Benutzerrecht bestimmt, welche Konten von einem Prozess verwendet werden können, um dem Sicherheitsprotokoll Einträge hinzuzufügen. Das Sicherheitsprotokoll wird verwendet, um den unbefugten System Zugriff zu verfolgen.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Annehmen der Identität eines Clients**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-impersonateclient) Identitätsnachweis

  Durch Zuweisen dieses Benutzer rechts zu einem Benutzer können Programme, die im Auftrag dieses Benutzers ausgeführt werden, die Identität eines Clients annehmen. Wenn dieses Benutzerrecht für diese Art von Identitätswechsel erforderlich ist, verhindert ein nicht autorisierter Benutzer, dass ein Client eine Verbindung mit einem Dienst herstellt, den er erstellt hat, und dann die Identität des Clients annimmt, wodurch die Berechtigungen des nicht autorisierten Benutzers auf Verwaltungs-oder Systemebene.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Zeitplanungspriorität erhöhen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/eweschedulingpriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-increaseschedulingpriority)

  Dieses Benutzerrecht bestimmt, welche Konten einen Prozess mit Schreib Eigenschaften Zugriff auf einen anderen Prozess verwenden können, um die Ausführungs Priorität zu erhöhen, die dem anderen Prozess zugewiesen ist.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Gerätetreiber laden und entladen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/loadunloaddevicedrivers](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-loadunloaddevicedrivers)

  Dieses Benutzerrecht bestimmt, welche Benutzer Gerätetreiber oder anderen Code dynamisch in den Kernel Modus laden und entladen können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Seiten im Speicher sperren**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/lockmemory](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-lockmemory)

  Mit diesem Benutzerrecht wird festgelegt, welche Konten einen Prozess zum Speichern von Daten im physischen Speicher verwenden können, wodurch das systemgesteuerte Auslagern der Daten in den virtuellen Arbeitsspeicher vermieden wird.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Überwachungs- und Sicherheitsprotokolle verwalten**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/manageauditingandsecuritylog](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-manageauditingandsecuritylog)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzeroptionen für die Objekt Zugriffs Überwachung für einzelne Ressourcen, z. b. Dateien, Active Directory Objekte und Registrierungsschlüssel, angeben können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Volumewartungsaufgaben durchführen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/managevolume](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-managevolume)

  Dieses Benutzerrecht bestimmt, welche Benutzer und Gruppen Wartungs Tasks auf einem Volume ausführen können, z. b. Remote Defragmentierung.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Firmwareumgebungsvariablen verändern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/modifyfirmwareenvironment](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyfirmwareenvironment)

  Mit diesem Benutzerrecht wird festgelegt, wer die Werte der Firmware-Umgebung ändern
  - **Nicht konfiguriert**
  - **Zulassen**

- **Objektbezeichnung verändern**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/modifyobjectlabel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-modifyobjectlabel)

  Dieses Benutzerrecht bestimmt, welche Benutzerkonten die Integritäts Bezeichnung von Objekten ändern können, z. b. Dateien, Registrierungsschlüssel oder Prozesse, die sich im Besitz anderer Benutzer befinden.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Profil für einen Einzelprozess erstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/profilesingleprocess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-profilesingleprocess)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer die Leistungs Überwachungstools zum Überwachen der Leistung von System Prozessen verwenden können.
  - **Nicht konfiguriert**
  - **Zulassen**

- **Remote Herunterfahren**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/RemoteShutdown](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-remoteshutdown)

  Dieses Benutzerrecht bestimmt, welche Benutzer einen Computer von einem Remote Standort im Netzwerk Herunterfahren dürfen. Der Missbrauch dieses Benutzer rechts kann zu einem Denial-of-Service-Angriff führen.
  - **Nicht konfiguriert**
  - **Zulassen**
  
- **Dateien und Verzeichnisse wiederherstellen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/restorefilesanddirectories](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-restorefilesanddirectories)
  
  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer die Berechtigungen Datei, Verzeichnis, Registrierung und andere persistente Objekte beim Wiederherstellen von gesicherten Dateien und Verzeichnissen umgehen können, und es wird bestimmt, welche Benutzer einen gültigen Sicherheits Prinzipal als Besitzer eines Objekts festlegen können.
  - **Nicht konfiguriert**
  - **Zulassen**
  
- **Besitz von Dateien oder Objekten übernehmen**  
  **Standardeinstellung:** Nicht konfiguriert  
  CSP: [Userrights/Take Ownership](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-userrights#userrights-takeownership)

  Mit diesem Benutzerrecht wird festgelegt, welche Benutzer den Besitz von Sicherungs fähigen Objekten im System übernehmen können, einschließlich Active Directory Objekten, Dateien und Ordnern, Druckern, Registrierungs Schlüsseln, Prozessen und Threads.
  - **Nicht konfiguriert**
  - **Zulassen**

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../configuration/device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../configuration/device-profile-monitor.md).  

Konfigurieren von Endpoint Protection-Einstellungen auf [macOS](endpoint-protection-macos.md)-Geräten.  
