---
title: Archive-of InTune-MDM-Sicherheitsbaselines-Einstellungen für Windows 10
titleSuffix: Microsoft Intune
description: Archivieren der früheren Releaseversionen der MDM-Sicherheitsbaseline-Einstellungen für die Verwaltung von Windows 10 mit Microsoft InTune
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3980720101489d32b27957a2e2d3e0e951e58da6
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509015"
---
<!-- This article contains the exact baseline details for baseline versions that were previously published in security-baseline-settings-mdm.md.  -->

# <a name="archive-of-mdm-security-baseline-settings"></a>Archivieren der MDM-Sicherheitsbaseline-Einstellungen  

Anzeigen von Details zu archivierten Versionen der MDM-Sicherheitsbaseline für InTune.  

Wenn eine neue MDM-Sicherheitsbaseline veröffentlicht wird, wird die vorherige Liste der Einstellungen aus dem Artikel Sicherheitsbaseline-Einstellungen in dieses Archiv verschoben. Diese Versionen werden weiterhin zur Verwendung unterstützt, und dieses Archiv wird bereitgestellt, um das Verständnis der Standardeinstellungen für ältere Baselineversion zu unterstützen.

Wenn eine Baselineversion nicht mehr zur Verwendung unterstützt wird, wird Sie aus diesem Artikel entfernt.

- Zeigen Sie die Einstellungen an, die in [der aktuellen MDM-Sicherheitsbaseline](security-baseline-settings-mdm-all.md?pivots=mdm-may-2019)verfügbar sind.
- Erfahren Sie mehr über [Sicherheitsbaselines](security-baselines.md)und das Upgrade der Baselineversion in ihren Sicherheitsbaseline-Profilen.

## <a name="preview-mdm-security-baseline-for-october-2018"></a>Vorschauversion: MDM-Sicherheitsbaseline für Oktober 2018  

*Diese Baseline wird durch die [MDM-Sicherheitsbaseline für Mai 2019](security-baseline-settings-mdm-all.md?pivots=mdm-may-2019) ersetzt.*

### <a name="above-lock"></a>Sperrbildschirm  

Weitere Informationen finden Sie unter [Policy CSP - AboveLock (Richtlinien-Konfigurationsdienstanbieter: AboveLock)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in Ihrer Windows-Dokumentation.  

- **Anzeige von Popupbenachrichtigungen blockieren**  
  Diese Richtlinieneinstellung ermöglicht Ihnen, zu verhindern, dass App-Benachrichtigungen auf dem Sperrbildschirm angezeigt werden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden keine App-Benachrichtigungen auf dem Sperrbildschirm angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer wählen, welche Apps Benachrichtigungen auf dem Sperrbildschirm anzeigen.
  
  **Standard**: Ja  

### <a name="app-runtime"></a>App-Laufzeit  

Weitere Informationen finden Sie unter [Policy CSP - AppRuntime (Richtlinien-Konfigurationsdienstanbieter: AppRuntime)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in Ihrer Windows-Dokumentation.  

- **Microsoft-Konten optional für Windows Store-Apps**  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob für Windows Store-Apps, die eine Anmeldung mit einem Konto erfordern, Microsoft-Konten optional sind. Diese Richtlinie betrifft nur Windows Store-Apps, die dies unterstützen. Wenn Sie diese Richtlinieneinstellung aktivieren, ermöglichen Windows Store-Apps, die normalerweise die Anmeldung mit einem Microsoft-Konto erfordern, Benutzern stattdessen die Anmeldung mit einem Unternehmenskonto. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, müssen Benutzer sich mit einem Microsoft-Konto anmelden.  
  
  **Standard**: Aktiviert  

### <a name="application-management"></a>Anwendungsverwaltung  

Weitere Informationen finden Sie unter [Policy CSP - ApplicationManagement (Richtlinien-Konfigurationsdienstanbieter: ApplicationManagement)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in Ihrer Windows-Dokumentation.  

- **Game DVR (nur Desktop) blockieren**  
  konfiguriert, ob Aufzeichnen und Übertragen von Spielen zulässig ist.
  
  **Standard**: Ja  

### <a name="auto-play"></a>Automatische Wiedergabe  

Weitere Informationen finden Sie unter [Policy CSP - Autoplay (Richtlinien-Konfigurationsdienstanbieter: Autoplay)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in Ihrer Windows-Dokumentation.  

- **Standardverhalten für automatische Ausführung der automatischen Wiedergabe**  
  Diese Einstellung betrifft das Standardverhalten für AutoRun-Befehle. AutoRun-Befehle werden in autorun.inf-Dateien gespeichert und können Installationsprogramme oder andere Routinen auslösen. Wenn das Standardverhalten für AutoRun-Befehle *Aktiviert* ist, können es Administratoren auf einem Gerät ändern, das Windows Vista oder eine höhere Version ausführt. Für das Verhalten bestehen die folgenden Einstellungsmöglichkeiten: a) AutoRun-Befehle komplett deaktivieren, oder b) Wiederherstellen des Verhaltens vor der Ausführung von Windows Vista, damit AutoRun-Befehle wieder automatisch ausgeführt werden. Wenn *Deaktiviert* oder *Nicht konfiguriert* eingestellt ist, wird der Benutzer von Geräten, auf denen Windows Vista ausgeführt wird, dazu aufgefordert, zu entscheiden, ob ein AutoRun-Befehl ausgeführt werden soll.
  
  **Standard**: Nicht ausführen  
  
- **Modus für automatische Wiedergabe**  
  Diese Richtlinieneinstellung ermöglicht Ihnen, die Funktion für die automatische Wiedergabe zu deaktivieren. Die automatische Wiedergabe startet den Lesevorgang von einem Laufwerk, sobald Sie Medien in das Laufwerk einlegen. Daher wird die Installationsdatei von Programmen sofort gestartet, und Musik auf Audiomedien wird sofort abgespielt. In Versionen vor Windows XP SP2 ist die automatische Wiedergabe standardmäßig auf Wechseldatenträgern wie dem Diskettenlaufwerk (nicht aber auf dem CD-ROM-Laufwerk) und Netzlaufwerken deaktiviert. Ab Windows XP SP2 ist die automatische Wiedergabe auch für Wechseldatenträger, einschließlich Ziplaufwerken und einigen USB-Massenspeichergeräten, aktiviert. Wenn Sie diese Richtlinieneinstellung aktivieren, ist die automatische Wiedergabe auf CD-ROM-Laufwerken und Wechselmedien oder auf allen Laufwerken deaktiviert. Diese Richtlinieneinstellung deaktiviert die automatische Wiedergabe auf weiteren Laufwerktypen. Sie können diese Einstellung nicht dazu verwenden, die automatische Wiedergabe auf Laufwerken zu aktivieren, auf denen sie standardmäßig deaktiviert ist. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, ist die automatische Wiedergabe aktiviert. Hinweis: Diese Richtlinieneinstellung wird sowohl in den Ordnern für die Computerkonfiguration als auch für die Benutzerkonfiguration angezeigt. Wenn die Richtlinieneinstellungen miteinander im Konflikt stehen, hat die Richtlinieneinstellung in der Computerkonfiguration Vorrang gegenüber der Richtlinieneinstellung in der Benutzerkonfiguration.
  
  **Standard**: Deaktiviert

- **Automatische Wiedergabe für Nicht-Volume-Geräte blockieren**  
  Diese Richtlinieneinstellung deaktiviert die automatische Wiedergabe für MTP-Geräte wie Kameras oder Telefone. Wenn Sie diese Richtlinieneinstellung aktivieren, ist die automatische Wiedergabe auf MTP-Geräten wie Kameras oder Telefonen nicht möglich. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, ist die automatische Wiedergabe für Nicht-Volume-Geräte aktiviert.
  
  **Standard**: Aktiviert  

### <a name="bitlocker"></a>BitLocker  

Weitere Informationen finden Sie unter [Policy CSP - BitLocker (Richtlinien-Konfigurationsdienstanbieter: BitLocker)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in Ihrer Windows-Dokumentation.  

- **Richtlinie für BitLocker-Verschlüsselung von Wechseldatenträgern**  
  Diese Richtlinieneinstellung wird verwendet, um die Verschlüsselungsmethode und Verschlüsselungsstärke zu steuern. Die Werte dieser Richtlinie bestimmen die Stärke der Verschlüsselung, die BitLocker für die Verschlüsselung verwendet. Unternehmen sollten die Verschlüsselungsstufe für erhöhte Sicherheit steuern (AES-256 ist sicherer als AES-128). Wenn Sie diese Einstellung aktivieren, können Sie einen Verschlüsselungsalgorithmus konfigurieren und für Festplattenlaufwerke, Betriebssystemlaufwerke und Wechseldatenträger die Verschlüsselungsstärke für Schlüssel individuell konfigurieren. Für Festplatten- und Betriebssystemlaufwerke wird die Verwendung des XTS-AES-Algorithmus empfohlen. Für Wechseldatenträger sollten Sie AES-CBC 128-Bit oder AES-CBC 256-Bit verwenden, wenn es in anderen Geräten verwendet wird, auf denen nicht Windows 10, Version 1511 oder höher ausgeführt wird. Das Ändern der Verschlüsselungsmethode hat keine Auswirkungen, wenn das Laufwerk bereits verschlüsselt ist oder die Verschlüsselung gerade ausgeführt wird. In diesen Fällen wird diese Richtlinieneinstellung ignoriert.

  Konfigurieren Sie bei der Richtlinie für BitLocker-Verschlüsselung von Wechseldatenträgern die folgenden Einstellungen:

  - **Verschlüsselung für Schreibzugriff anfordern**  
    **Standard**: Ja  

  - **Verschlüsselungsmethode**  
    **Standard**: AES-256-Bit (CBC)  

- **Richtlinie für BitLocker-Verschlüsselung von Festplattenlaufwerken**  
  Diese Richtlinieneinstellung wird verwendet, um die Verschlüsselungsmethode und Verschlüsselungsstärke zu steuern. Die Werte dieser Richtlinie bestimmen die Stärke der Verschlüsselung, die BitLocker für die Verschlüsselung verwendet. Unternehmen sollten die Verschlüsselungsstufe für erhöhte Sicherheit steuern (AES-256 ist sicherer als AES-128). Wenn Sie diese Einstellung aktivieren, können Sie einen Verschlüsselungsalgorithmus konfigurieren und für Festplattenlaufwerke, Betriebssystemlaufwerke und Wechseldatenträger die Verschlüsselungsstärke für Schlüssel individuell konfigurieren. Für Festplatten- und Betriebssystemlaufwerke wird die Verwendung des XTS-AES-Algorithmus empfohlen. Für Wechseldatenträger sollten Sie AES-CBC 128-Bit oder AES-CBC 256-Bit verwenden, wenn es in anderen Geräten verwendet wird, auf denen nicht Windows 10, Version 1511 oder höher ausgeführt wird. Das Ändern der Verschlüsselungsmethode hat keine Auswirkungen, wenn das Laufwerk bereits verschlüsselt ist oder die Verschlüsselung gerade ausgeführt wird. In diesen Fällen wird diese Richtlinieneinstellung ignoriert.  
 
  Konfigurieren Sie bei der Richtlinie für BitLocker-Verschlüsselung von Festplattenlaufwerken die folgenden Einstellungen: 
  - **Verschlüsselungsmethode**  
    **Standard**: AES-256-Bit (XTS)  

- **Richtlinie für BitLocker-Verschlüsselung von Systemlaufwerken**  
  Diese Richtlinieneinstellung wird verwendet, um die Verschlüsselungsmethode und Verschlüsselungsstärke zu steuern. Die Werte dieser Richtlinie bestimmen die Stärke der Verschlüsselung, die BitLocker für die Verschlüsselung verwendet. Unternehmen sollten die Verschlüsselungsstufe für erhöhte Sicherheit steuern (AES-256 ist sicherer als AES-128). Wenn Sie diese Einstellung aktivieren, können Sie einen Verschlüsselungsalgorithmus konfigurieren und für Festplattenlaufwerke, Betriebssystemlaufwerke und Wechseldatenträger die Verschlüsselungsstärke für Schlüssel individuell konfigurieren. Für Festplatten- und Betriebssystemlaufwerke wird die Verwendung des XTS-AES-Algorithmus empfohlen. Für Wechseldatenträger sollten Sie AES-CBC 128-Bit oder AES-CBC 256-Bit verwenden, wenn es in anderen Geräten verwendet wird, auf denen nicht Windows 10, Version 1511 oder höher ausgeführt wird. Das Ändern der Verschlüsselungsmethode hat keine Auswirkungen, wenn das Laufwerk bereits verschlüsselt ist oder die Verschlüsselung gerade ausgeführt wird. In diesen Fällen wird diese Richtlinieneinstellung ignoriert.  

  Konfigurieren Sie bei der Richtlinie für BitLocker-Verschlüsselung von Systemlaufwerken die folgenden Einstellungen:
  - **Verschlüsselungsmethode**  
    **Standard**: AES-256-Bit (XTS)  

### <a name="browser"></a>Browser  

Weitere Informationen finden Sie unter [Policy CSP - Browser (Richtlinien-Konfigurationsdienstanbieter - Browser)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in Ihrer Windows-Dokumentation.  

- **SmartScreen für Microsoft Edge anfordern**  

  Microsoft Edge verwendet Windows Defender SmartScreen (aktiviert), um Benutzer standardmäßig vor potenziellen betrügerischen Phishing-Angriffen und Schadsoftware zu schützen. Standardmäßig ist auch eingestellt, dass Benutzer Windows Defender SmartScreen nicht deaktivieren können. Wenn Sie diese Richtlinie aktivieren, wird Windows Defender SmartScreen deaktiviert und kann von Benutzern nicht mehr aktiviert werden. Konfigurieren Sie diese Richtlinie nicht so, dass Benutzer wählen können, ob Windows Defender SmartScreen aktiviert oder deaktiviert wird.  
  
  **Standard**: Ja  
  
- **Zugriff auf schädliche Websites blockieren**  

  Standardmäßig ermöglicht Microsoft Edge Benutzern, die Warnungen von Windows Defender SmartScreen zu potenziell schädlichen Websites zu umgehen (ignorieren) und trotzdem auf die betreffende Website zuzugreifen. Mit dieser Richtlinie können Sie Microsoft Edge jedoch so konfigurieren, dass Benutzer die Warnungen nicht umgehen und nicht auf die Website zugreifen können.
  
  **Standard**: Ja  
  
- **Block unverified file download** (Herunterladen nicht überprüfter Dateien blockieren) Standardmäßig ermöglicht Microsoft Edge Benutzern, die Warnungen von Windows Defender SmartScreen zu potenziell schädlichen Dateien zu umgehen (ignorieren) und die nicht geprüfte(n) Datei(en) trotzdem herunterzuladen. Durch die Aktivierung dieser Richtlinie wird verhindert, dass Benutzer die Warnungen umgehen und die nicht geprüfte(n) Datei(en) herunterladen.
  
  **Standard**: Ja  
  
- **Kennwort-Manager blockieren**  
  Standardmäßig verwendet Microsoft Edge den Kennwort-Manager automatisch, wodurch Benutzern die lokale Verwaltung von Kennwörtern ermöglicht wird. Wenn diese Richtlinie deaktiviert wird, kann Microsoft Edge den Kennwort-Manager nicht nutzen. Konfigurieren Sie diese Richtlinie nicht, wenn Sie Benutzern erlauben möchten, selbst zu entscheiden, ob sie den Kennwort-Manager zum lokalen Speichern und Verwalten von Kennwörtern verwenden möchten.
  
  **Standard**: Ja  
  
- **Prevent certificate error overrides** (Überschreiben von Zertifikatfehlern verhindern)  
  Diese Richtlinieneinstellung verhindert, dass der Benutzer SSL/TLS-Zertifikatfehler (Secure Sockets Layer/Transport Layer Security), die die Navigation in Internet Explorer unterbrechen (z.B. „Abgelaufen“, „Gesperrt“ oder „Name stimmt nicht überein“ ) ignoriert. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer das Browsen nicht mehr fortsetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann der Benutzer entscheiden, ob Zertifikatfehler ignoriert werden sollen und das Browsen fortsetzen.
  
  **Standard**: Ja  

### <a name="connectivity"></a>Verbindung  

Weitere Informationen finden Sie unter [Policy CSP – Connectivity (Richtlinien-Konfigurationsdienstanbieter: Konnektivität)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in der Windows-Dokumentation.  

- **Block Internet download for web publishing and online ordering wizards** (Internet-Download für die Assistenten „Webpublishing“ und „Onlinebestellung von Abzügen“ deaktivieren)  
  Diese Richtlinieneinstellung legt fest, ob Windows eine Liste von Anbietern für den Webpublishing-Assistenten und den Assistenten für Onlinebestellung herunterladen soll. Diese Assistenten ermöglichen Benutzern, aus einer Liste Firmen auszuwählen, die Dienste wie Onlinespeicherung und Fotodruck anbieten. Standardmäßig werden zusätzlich zu den in der Registrierung angegebenen Anbietern auch solche angezeigt, die von einer Windows-Website heruntergeladen wurden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden keine Anbieter heruntergeladen, sondern nur die Dienstanbieter angezeigt, die in der lokalen Registrierung zwischengespeichert sind. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird eine Liste von Anbietern heruntergeladen, wenn der Benutzer den Webpublishing-Assistenten und den Assistenten für Onlinebestellung verwendet. Weitere Informationen über den Webpublishing-Assistenten und den Assistenten für Onlinebestellung finden Sie in der Dokumentation, einschließlich Details über das Angeben von Dienstanbietern in der Registrierung.  
  
  **Standard**: Aktiviert  

- **Block downloading of print drivers over HTTP** (Download von Druckertreibern über HTTP blockieren)  
  Diese Richtlinieneinstellung gibt an, ob dieser Client Druckertreiberpakete über HTTP herunterladen darf. Nicht im Lieferumfang enthaltene Treiber müssen über HTTP heruntergeladen werden, um das HTTP-Drucken einzurichten. Hinweis: Diese Richtlinieneinstellung hindert den Client nicht, auf Druckern im Intranet oder Internet über HTTP zu drucken. Sie verhindert nur das Herunterladen von Treibern, die noch nicht lokal installiert sind. Wenn Sie diese Richtlinieneinstellung aktivieren, können keine Druckertreiber über HTTP heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können die Benutzer Druckertreiber über HTTP herunterladen.
  
  **Standard**: Aktiviert  

### <a name="credentials-delegation"></a>Delegierung von Anmeldeinformationen  

Weitere Informationen finden Sie unter [Policy CSP – CredentialsDelegation (Richtlinien-Konfigurationsdienstanbieter: CredentialsDelegation)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in der Windows-Dokumentation.  

- **Remote host delegation of non-exportable credentials** (Remotehostdelegierung nicht exportierbarer Anmeldeinformationen)  
  Remotehost ermöglicht die Delegierung nicht exportierbarer Anmeldeinformationen. Bei Verwendung der Delegierung von Anmeldeinformationen stellen Geräte eine exportierbare Version der Anmeldeinformationen für den Remotehost bereit. Dadurch laufen Benutzer Gefahr, dass ihre Anmeldeinformationen von Angreifern auf dem Remotehost gestohlen werden. Wenn Sie die Richtlinieneinstellung aktivieren, unterstützt der Host den eingeschränkten Verwaltungsmodus oder Remote Credential Guard-Modus. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden der eingeschränkte Verwaltungsmodus und der Remote Credential Guard-Modus nicht unterstützt, und Benutzer müssen ihre Anmeldeinformationen immer an den Host übergeben.  

  
  **Standard**: Aktiviert  

### <a name="credentials-ui"></a>Benutzeroberfläche für Anmeldeinformationen  

Weitere Informationen finden Sie unter [Policy CSP – Connectivity (Richtlinien-Konfigurationsdienstanbieter: CredentialsUI)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in der Windows-Dokumentation.  

- **Enumerate administrators** (Administratoren auflisten) Diese Richtlinieneinstellung steuert, ob Administratorkonten angezeigt werden, wenn ein Benutzer versucht, eine Anwendung mit erhöhten Rechten auszuführen. Standardmäßig werden Administratorkonten beim Versuch eines Benutzers, eine Anwendung mit erhöhten Rechten auszuführen, nicht angezeigt. Wenn Sie diese Richtlinieneinstellung aktivieren, werden alle lokalen Administratorkonten auf dem Computers angezeigt, damit der Benutzer eines auswählen und das richtige Kennwort eingeben kann. Wenn Sie diese Richtlinieneinstellung deaktivieren, müssen Benutzer jedes Mal einen Benutzernamen und ein Kennwort eingeben, um eine Anwendung mit erhöhten Rechten auszuführen.  

  
  **Standard**: Deaktiviert  

### <a name="data-protection"></a>Schutz von Daten  

Weitere Informationen finden Sie unter [Policy CSP – Defender (Richtlinien-Konfigurationsdienstanbieter: DataProtection)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in der Windows-Dokumentation.  

- **Block direct memory access** (Direkten Speicherzugriff blockieren)  
  Mit dieser Richtlinieneinstellung können Sie den direkten Speicherzugriff (Direct Memory Access, DMA) für alle Hot-Plug-PCI-Downstream-Anschlüsse blockieren, bis sich ein Benutzer bei Windows anmeldet. Sobald sich ein Benutzer anmeldet, werden die mit den Hot-Plug-PCI-Anschlüssen verbundenen PCI-Geräte von Windows aufgezählt. Jedes Mal, wenn der Benutzer den Computer sperrt, wird DMA an Hot-Plug-PCI-Anschlüssen ohne untergeordnete Geräte blockiert, bis sich der Benutzer erneut anmeldet. Geräte, die vor dem Entsperren des Computers bereits aufgezählt wurden, sind weiterhin funktionsfähig, bis sie entfernt werden oder das System neu gestartet bzw. in den Ruhezustand versetzt wird. Die Richtlinieneinstellung wird nur erzwungen, wenn BitLocker oder die Geräteverschlüsselung aktiviert ist.
  
  
  **Standard**: Ja  

### <a name="device-guard"></a>Device Guard  

Weitere Informationen finden Sie unter [Policy CSP – DeviceGuard (Richtlinien-Konfigurationsdienstanbieter: DeviceGuard)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in der Windows-Dokumentation.  

- **Credential Guard**  
  Mit dieser Einstellung können Benutzer Credential Guard mit virtualisierungsbasierter Sicherheit aktivieren, um den Schutz von Anmeldeinformationen beim nächsten Neustart zu unterstützen.
   
  **Standard**: Mit UEFI-Sperre aktivieren 

- **Enable virtualization based security** (Virtualisierungsbasierte Sicherheit aktivieren)  </br>
  Aktiviert die virtualisierungsbasierte Sicherheit (VBS) beim nächsten Neustart. Virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen.
  
  **Standard**: Ja  

- **Launch system guard**   (Systemschutz starten)  
  **Standard**: Aktiviert  

### <a name="device-installation"></a>Geräteinstallation  

Weitere Informationen finden Sie unter [Policy CSP – DeviceInstallation (Richtlinien-Konfigurationsdienstanbieter: DeviceInstallation)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in der Windows-Dokumentation.  

- **Hardware device installation by device identifiers** (Installation von Hardwaregeräten anhand der Geräte-ID)  
  Mit dieser Richtlinieneinstellung können Sie eine Liste von Plug & Play-Hardware-IDs und kompatiblen IDs für Geräte angeben, deren Installation unter Windows verhindert wird. Diese Richtlinieneinstellung hat Vorrang gegenüber jeder anderen Richtlinieneinstellung, die die Installation eines Geräts ermöglicht. Wenn Sie diese Richtlinieneinstellung aktivieren, kann ein Gerät nicht installiert oder aktualisiert werden, wenn die zugehörige Hardware-ID oder kompatible ID in der von Ihnen erstellten Liste enthalten ist. Wenn Sie diese Richtlinieneinstellung auf einem Remotedesktopserver aktivieren, wirkt sich dies auf die Umleitung der angegebenen Geräte von einem Remotedesktopclient an den Remotedesktopserver aus. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Geräte installiert und aktualisiert werden, sofern andere Richtlinieneinstellungen dies zulassen.
  
  **Standard**: Block hardware device installation (Hardwaregeräteinstallation blockieren)  

  Wenn *Block hardware device installation* ausgewählt wurde, stehen die folgenden Einstellungen zur Verfügung.

  - **Remove matching hardware devices**  (Übereinstimmende Hardwaregeräte entfernen)  
  Diese Einstellung ist nur verfügbar, wenn die Option *Hardware device installation by device identifiers* (Installation von Hardwaregeräten anhand der Geräte-ID) auf *Block hardware device installation* (Hardwaregeräteinstallation blockieren) festgelegt ist.
    
    **Standard**: Ja

  - **Hardware device identifiers that are blocked** (Blockierte Bezeichner von Hardwaregeräten)  
      Diese Einstellung ist nur verfügbar, wenn die Option *Hardware device installation by device identifiers* (Installation von Hardwaregeräten anhand der Geräte-ID) auf *Block hardware device installation* (Hardwaregeräteinstallation blockieren) festgelegt ist.
    
    **Standard**: Ja  
  
- **Hardware device installation by device identifiers** (Installation von Hardwaregeräten anhand der Setupklassen)  
  Mit dieser Richtlinieneinstellung können Sie eine Liste von GUIDs für Gerätesetupklassen angeben, die Gerätetreiber beschreiben, die unter Windows nicht installierbar sind. Diese Richtlinieneinstellung hat Vorrang gegenüber jeder anderen Richtlinieneinstellung, die die Installation eines Geräts ermöglicht. Wenn Sie diese Richtlinieneinstellung aktivieren, können Gerätetreiber nicht installiert oder aktualisiert werden, deren GUIDs für Gerätesetupklassen in der von Ihnen erstellten Liste enthalten sind. Wenn Sie diese Richtlinieneinstellung auf einem Remotedesktopserver aktivieren, wirkt sich dies auf die Umleitung der angegebenen Geräte von einem Remotedesktopclient an den Remotedesktopserver aus. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Geräte unter Windows installiert und aktualisiert werden, sofern andere Richtlinieneinstellungen dies zulassen.
  
  **Standard**: Block hardware device installation (Hardwaregeräteinstallation blockieren)  

  Wenn *Block hardware device installation* ausgewählt wurde, stehen die folgenden Einstellungen zur Verfügung.
  - **Remove matching hardware devices**   (Übereinstimmende Hardwaregeräte entfernen)  
  Diese Einstellung ist nur verfügbar, wenn *Hardware device installation by setup classes (Hardwaregeräteinstallation nach Setup-Klasse)* auf *Block hardware device installation (Hardwaregeräteinstallation blockieren)* eingestellt ist.  

    **Standard**: *Keine Standardkonfiguration*  

  - **Hardware device identifiers that are blocked** (Blockierte Bezeichner von Hardwaregeräten)  
    Diese Einstellung ist nur verfügbar, wenn *Hardware device installation by setup classes (Hardwaregeräteinstallation nach Setup-Klasse)* auf *Block hardware device installation (Hardwaregeräteinstallation blockieren)* eingestellt ist.
    
    **Standard**: *Keine Standardkonfiguration*  

### <a name="device-lock"></a>Gerätesperre  

Weitere Informationen finden Sie unter [Policy CSP - DeviceLock (Richtlinien-CSP: DeviceLock)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in Ihrer Windows-Dokumentation.  

- **Verwendung der Kamera verhindern**  
  Deaktiviert das Ein-/Ausschalten der Kamera auf dem Sperrbildschirm in den PC-Einstellungen und verhindert, dass eine Kamera auf dem Sperrbildschirm aufgerufen wird. Standardmäßig können Benutzer das Aufrufen einer verfügbaren Kamera auf dem Sperrbildschirm aktivieren. Wenn Sie diese Einstellung aktivieren, können Benutzer den Kamerazugriff auf den Sperrbildschirm in den PC-Einstellungen nicht mehr aktivieren, und die Kamera kann nicht mehr auf dem Sperrbildschirm aufgerufen werden. 
  
  **Standard**: Aktiviert  

- **Kennwort anfordern**  
  Gibt an, ob eine Gerätesperre aktiviert ist.
  
  **Standard**: Ja  
  
  Wenn *Kennwort anfordern* auf *Ja* festgelegt wurde, stehen die folgenden Einstellungen zur Verfügung.

  - **Mindestanzahl von Zeichensätzen für Kennwörter**  
    Anzahl der komplexen Elementtypen (Groß- und Kleinbuchstaben, Zahlen und Interpunktionszeichen), die für eine sichere PIN oder ein sicheres Kennwort erforderlich sind. Die PIN erzwingt das folgende Verhalten für Desktop- und mobile Geräte: 1 – nur Ziffern; 2 – Ziffern und Kleinbuchstaben sind erforderlich; 3 – Ziffern, Kleinbuchstaben und Großbuchstaben sind erforderlich. Nicht unterstützt in Microsoft- und Domänenkonten für Desktopgeräte. 4: Ziffern, Kleinbuchstaben, Großbuchstaben und Sonderzeichen sind erforderlich. Nicht unterstützt für Desktop-Geräte. Der Standardwert lautet 1. 
    
    **Standard**: 3  
  
  - **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird**  
    Die Anzahl von zulässigen Authentifizierungsfehlern bevor das Gerät zurückgesetzt wird. Der Wert 0 deaktiviert die Rücksetzfunktion eines Geräts.
    
    **Standard**: 10  
  
  - **Kennwortablauf (Tage)**  
    Die Richtlinieneinstellung für das maximale Kennwortalter bestimmt die Zeitspanne (in Tagen), in der ein Kennwort verwendet werden kann, bevor das System den Benutzer zum Ändern des Kennworts auffordert. Sie können einstellen, dass Kennwörter nach einer bestimmten Anzahl von Tagen (zwischen 1 und 999) ablaufen, oder dass Kennwörter nie ablaufen, indem Sie die Anzahl der Tage auf 0 einstellen. Wenn das maximale Kennwortalter zwischen 1 und 999 Tagen liegt, muss das minimale Kennwortalter darunter liegen. Wenn das maximale Kennwortalter auf 0 eingestellt ist, kann das minimale Kennwortalter ein Wert zwischen 0 und 998 Tagen sein.
    
    **Standard**: 60  
  
  - **Erforderlicher Kennworttyp**  
    Bestimmt den Typ der erforderlichen PIN oder des erforderlichen Kennworts.
    
    **Standard**: Alphanumerisch  
  
  - **Minimale Kennwortlänge**  
    Die Richtlinieneinstellung für die minimale Kennwortlänge bestimmt die Mindestanzahl von Zeichen, die ein Kennwort für ein Benutzerkonto besitzen muss. Sie können einen Wert zwischen 1 und 14 Zeichen einstellen, oder Sie können einstellen, dass kein Kennwort erforderlich ist, indem Sie die Zeichenanzahl auf 0 einstellen.
    
    **Standard**: 8  

  - **Einfache Kennwörter blockieren**  
    Gibt an, ob PINs oder Kennwörter wie „1111“ oder „1234“ zulässig sind. Für Desktop-Geräte wird auch die Verwendung von Bildcodes gesteuert.
    
    **Standard**: Ja  
      *Eine Einstellung auf „Ja“ verhindert die Verwendung einfacher Kennwörter.* 

  - **Wiederverwendung vorheriger Kennwörter verhindern**  
    Gibt an, wie viele Kennwörter, die nicht mehr verwendet werden können, im Verlauf gespeichert werden können. Der Wert schließt das aktuelle Kennwert des Benutzers mit ein. So kann der Benutzer beispielsweise bei der Einstellung *1* sein aktuelles Kennwort nicht ändern, wenn er ein neues Kennwort auswählt. Die Einstellung *5* bedeutet, dass ein Benutzer sein neues Kennwort nicht auf sein aktuelles Kennwort oder eines seiner vorherigen vier Kennwörter festlegen kann.
    
    **Standard**: 24  

- **Diashow verhindern**  
  Deaktiviert die Diashow-Einstellungen für den Sperrbildschirm in den PC-Einstellungen und verhindert das Abspielen einer Diashow auf dem Sperrbildschirm. Standardmäßig können Benutzer eine Diashow aktivieren, die nach dem Sperren des Computers abgespielt wird. Wenn Sie diese Einstellung aktivieren, können Benutzer Diashow-Einstellungen in den PC-Einstellungen nicht ändern, und es kann keine Diashow gestartet werden.
  
    **Standard**: Aktiviert  
    *Die Einstellung „Deaktiviert“ verhindert das Abspielen von Diashows.* 

- **Minimales Kennwortalter in Tagen**  
  Die Richtlinieneinstellung für das minimale Kennwortalter bestimmt die Zeitspanne (in Tagen), in der ein Kennwort verwendet werden muss, bevor der Benutzer es ändern kann. Sie können einen Wert zwischen 1 und 998 Tagen festlegen, oder Sie können Kennwortänderungen sofort zulassen, indem Sie die Anzahl der Tage auf 0 setzen. Das minimale Kennwortalter muss unter dem maximalen Kennwortalter liegen, es sei denn, das maximale Kennwortalter ist auf 0 eingestellt, was bedeutet, dass ein Kennwörter nie ablaufen. Wenn das maximale Kennwortalter auf 0 eingestellt ist, kann für das minimale Kennwortalter ein Wert zwischen 0 und 998 eingestellt werden.
  
    **Standard**: 1  

### <a name="event-log-service"></a>Ereignisprotokolldienst  

Weitere Informationen finden Sie unter [Policy CSP - EventLogService (Richtlinien-Konfigurationsdienstanbieter: EventLogService)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in Ihrer Windows-Dokumentation.  

- **Sicherheitsprotokoll: maximale Dateigröße in kB**  
  Diese Richtlinieneinstellung gibt die maximale Größe der Protokolldatei in Kilobyte an. Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie die maximale Protokolldateigröße so konfigurieren, dass sie zwischen 1 Megabyte (1.024 Kilobyte) und 2 Terabyte (2.147.483.647 Kilobyte) in Kilobyte-Schritten liegt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die maximale Größe der Protokolldatei auf den lokal konfigurierten Wert eingestellt. Dieser Wert kann durch den lokalen Administrator über das Dialogfeld „Protokolleigenschaften“ geändert werden und wird standardmäßig auf 20 Megabyte eingestellt.
  
   **Standard**: 196608  

- **Systemprotokoll: maximale Dateigröße in kB**  
  Diese Richtlinieneinstellung gibt die maximale Größe der Protokolldatei in Kilobyte an. Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie die maximale Protokolldateigröße so konfigurieren, dass sie zwischen 1 Megabyte (1.024 Kilobyte) und 2 Terabyte (2.147.483.647 Kilobyte) in Kilobyte-Schritten liegt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die maximale Größe der Protokolldatei auf den lokal konfigurierten Wert eingestellt. Dieser Wert kann durch den lokalen Administrator über das Dialogfeld „Protokolleigenschaften“ geändert werden und wird standardmäßig auf 20 Megabyte eingestellt.
  
  **Standard**: 32768  

- **Anwendungsprotokoll: maximale Dateigröße in kB**  
  Diese Richtlinieneinstellung gibt die maximale Größe der Protokolldatei in Kilobyte an. Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie die maximale Protokolldateigröße so konfigurieren, dass sie zwischen 1 Megabyte (1.024 Kilobyte) und 2 Terabyte (2.147.483.647 Kilobyte) in Kilobyte-Schritten liegt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die maximale Größe der Protokolldatei auf den lokal konfigurierten Wert eingestellt. Dieser Wert kann durch den lokalen Administrator über das Dialogfeld „Protokolleigenschaften“ geändert werden und wird standardmäßig auf 20 Megabyte eingestellt.
  
  **Standard**: 32768  

### <a name="experience"></a>Erfahrung  

Weitere Informationen finden Sie unter [Policy CSP - Experience (Richtlinien-Konfigurationsdienstanbieter: Experience)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in Ihrer Windows-Dokumentation.  

- **Windows-Blickpunkt blockieren**  
  Ermöglicht IT-Administratoren, alle Features von Windows-Blickpunkt zu deaktivieren – Windows-Blickpunkt auf dem Sperrbildschirm, Windows-Tipps, Microsoft-Features für Endbenutzer und weitere ähnliche Features.
  
  **Standard**: Ja  

  Wenn *Windows-Blickpunkt blockieren* auf *Ja* festgelegt wurde, stehen die folgenden Einstellungen zur Verfügung.
  
  - **Drittanbietervorschläge in Windows-Blickpunkt blockieren**  
    Gibt an, ob App- und Inhaltsvorschläge durch Herausgeber von Drittanbieter-Software in Features von Windows-Blickpunkt (z.B. Windows-Blickpunkt auf dem Sperrbildschirm, vorgeschlagene Apps im Startmenü oder Windows-Tipps) zulässig sind. Benutzer sehen möglicherweise trotzdem Vorschläge für Microsoft-Features, -Apps und -Dienste.
      
    **Standard**: Ja  
  - **Bestimmte Funktionen für Endbenutzer blockieren**  
    Ermöglicht IT-Administratoren das Aktivieren von Funktionen, die normalerweise nur für Endbenutzer bestimmt sind, beispielsweise Startvorschläge, Mitgliedschaftsbenachrichtigungen, App-Installation nach Anzeige der Windows-Willkommensseite und Kachelumleitungen.
    
    **Standard**: Ja  


### <a name="exploit-guard"></a>Exploit Guard  

Weitere Informationen finden Sie unter [Policy CSP - ExploitGuard (Richtlinien-Konfigurationsdienstanbieter: ExploitGuard)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in Ihrer Windows-Dokumentation.  

- **Exploit-Schutz-XML**  
  Ermöglicht dem IT-Administrator, eine Konfiguration vorzunehmen, die für alle Geräte in der Organisation die gewünschten Optionen zur Risikominderung für System und Anwendungen abbildet. Die Konfiguration wird in einer XML-Datei vorgenommen. Durch den Exploit-Schutz können Geräte vor Schadsoftware geschützt werden, die Exploits für die Verbreitung und den Befall von Systemen verwendet. Sie können die App „Windows-Sicherheit“ oder PowerShell verwenden, um Lösungen zur Entschärfung (Konfigurationen) zu erstellen. Diese Konfiguration können Sie anschließend als XML-Datei exportieren und für die Computer in Ihrem Netzwerk freigeben, sodass diese über dieselben Einstellungen zur Entschärfung verfügen. Sie können außerdem eine vorhandene XML-Konfigurationsdatei aus EMET in eine XML-Konfigurationsdatei für den Exploit-Schutz konvertieren und importieren.
  
  **Standard:** *Sample xml is provided* (XML-Beispieldatei wird bereitgestellt) 
 
### <a name="file-explorer"></a>Datei-Explorer  

Weitere Informationen finden Sie unter [Policy CSP - FileExplorer (Richtlinien-CSP: FileExplorer)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in der Windows-Dokumentation.  

- **Block data execution prevention** (Schutz vor Ausführung von Daten blockieren)  
  Wenn Sie den Schutz vor der Ausführung von Daten deaktivieren, können bestimmte veraltete Plug-In-Anwendungen erfolgreich ausgeführt werden, ohne dass der Explorer geschlossen wird.
  
  **Standard**: Deaktiviert  
   
- **Block heap termination on corruption** (Beenden von Heaps bei Beschädigung blockieren)  
  Wenn Sie das Beenden von Heaps bei Beschädigung deaktivieren, können bestimmte veraltete Plug-In-Anwendungen erfolgreich ausgeführt werden, ohne dass der Explorer sofort geschlossen wird. Der Explorer wird jedoch möglicherweise zu einem späteren Zeitpunkt unerwartet beendet.
  
  **Standard**: Deaktiviert  
    

### <a name="internet-explorer"></a>Internet Explorer  

Weitere Informationen finden Sie unter [Policy CSP - Internet Explorer (Richtlinien-CSP: Internet Explorer)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in der Windows-Dokumentation.  

- **Internet Explorer internet zone access to data sources** (Zugriff auf Datenquellen in Internetzonen in Internet Explorer)  
  Durch diese Richtlinieneinstellung können Sie festlegen, ob Internet Explorer mithilfe von Microsoft XML Parser (MSXML) oder ActiveX Data Objects (ADO) auf Daten aus anderen Sicherheitszonen zugreifen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer eine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie im Dropdownfeld „Prompt“ (Bestätigen) auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob eine Seite in der Zone geladen werden soll, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone drag content from different domains within windows** (Ziehen von Inhalten aus verschiedenen Domänen in Fenstern in einer eingeschränkten Zone in Internet Explorer)  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel im selben Fenster befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ nicht ändern.
  
  **Standard**: Deaktiviert
  
- **Internet Explorer certificate address mismatch warning** (Warnung für Zertifikatadressenkonflikte in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Sicherheitswarnung für Zertifikatadressenkonflikte aktivieren. Wenn diese Richtlinieneinstellung aktiviert ist, wird der Benutzer gewarnt, wenn eine sichere HTTP-Website (HTTPS) Zertifikate enthält, die für eine andere Adresse ausgestellt wurden. Durch diese Warnung können Spoofingangriffe verhindert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die Warnung für Zertifikatadressenkonflikte immer angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann der Benutzer über die Seite „Erweitert“ in der Internetsystemsteuerung festlegen, ob die Warnung für Zertifikatadressenkonflikte angezeigt wird.
  
  **Standard**: Aktiviert 
  
- **Internet Explorer restricted zone less privileged sites** (Websites mit geringeren Berechtigung in der eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Websites aus Zonen mit geringeren Berechtigungen, z.B. aus der Internetzone, zu dieser Zone navigieren können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Websites aus Zonen mit geringeren Berechtigungen neue Fenster in dieser Zone öffnen oder zu dieser Zone navigieren. Die Sicherheitszone wird ohne den zusätzlichen Schutz durch das Sicherheitsfeature „Schutz vor Zonenanhebung“ ausgeführt. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer gewarnt, dass er dabei ist, in einen möglicherweise gefährlichen Bereich zu navigieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden potentiell gefährliche Navigationsvorgänge verhindert. Wie von „Schutz vor Zonenanhebung“ festgelegt, ist das Internet Explorer-Sicherheitsfeature ist in dieser Zone aktiviert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden potentiell gefährliche Navigationsvorgänge verhindert. Wie von „Schutz vor Zonenanhebung“ festgelegt, ist das Internet Explorer-Sicherheitsfeature ist in dieser Zone aktiviert.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone automatic prompt for file downloads** (Automatische Eingabeaufforderung für Dateidownloads in der eingeschränkten Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob eine Eingabeaufforderung bei Dateidownloads angezeigt wird, die nicht vom Benutzer gestartet werden. Downloaddialogfelder werden unabhängig von dieser Einstellung für vom Benutzer gestartete Downloadvorgänge angezeigt. Wenn Sie diese Einstellung aktivieren, werden den Benutzern Downloaddialogfelder für automatische Downloadversuche angezeigt. Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, werden Dateidownloads, die nicht von Benutzern gestartet werden, blockiert, und Benutzern wird die Benachrichtigungsleiste anstelle des Downloaddialogfelds angezeigt. Die Benutzer können dann auf die Benachrichtigungsleiste klicken, um den Dateidownload zu genehmigen.
  
  **Standard**: Deaktiviert
  
- **Internet Explorer internet zone .NET Framework reliant components** (.NET Framework-Komponenten in Internetzonen von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die nicht mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer nicht signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob nicht signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer nicht signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer nicht signierte verwaltete Komponenten aus.
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer internet zone allow only approved domains to use tdc Active X controls** (Nur genehmigte Domänen können das TDC-ActiveX-Steuerelement in Internetzonen in Internet Explorer verwenden)  
  Diese Richtlinieneinstellung steuert, ob der Benutzer das TDC-ActiveX-Steuerelement auf Websites ausführen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird das TDC-ActiveX-Steuerelement nicht von Websites in dieser Zone ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird das TDC-ActiveX-Steuerelement von allen Websites in dieser Zone ausgeführt.
  
  **Standard**: Aktiviert 
  
- **Internet Explorer restricted zone script initiated windows** (Durch Skripts geöffnete Fenster für die eingeschränkte Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Einschränkungen zu durch Skripts geöffneten Popupfenstern und Fenstern mit Titel und Leisten verwalten. Wenn Sie diese Richtlinieneinstellung aktivieren, gilt das Sicherheitsfeature für Fenstereinschränkungen in dieser Zone nicht. Die Sicherheitszone wird also ohne die Sicherheitsebene ausgeführt, die von diesem Feature bereitgestellt wird. Wenn Sie diese Richtlinieneinstellung deaktivieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist.
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer internet zone include local path when uploading files to server** (Informationen zu lokalen Pfaden beim Hochladen von Dateien auf Server einfügen – Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, ob Informationen zu lokalen Pfaden beim Hochladen einer Datei über ein HTML-Formular übermittelt werden. Wenn die Informationen zu lokalen Pfaden übermittelt werden, kann es vorkommen, dass einige davon versehentlich für den Server offengelegt werden. Dabei kann es sich beispielsweise um Dateien vom Desktop des Benutzers handeln, die den Benutzernamen im Pfad enthalten. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular entfernt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt werden sollen. Die Pfadinformationen werden standardmäßig gesendet.
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer disable processes in enhanced protected mode** (Deaktivieren von Prozessen im erweiterten geschützten Modus in Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob 64-Bit-Prozesse (höhere Sicherheit) oder 32-Bit-Prozesse (bessere Kompatibilität) von Internet Explorer 11 verwendet werden, wenn unter 64-Bit-Versionen von Windows der erweiterte geschützte Modus aktiv ist. Wichtig: Einige ActiveX-Steuerelemente und Symbolleisten sind möglicherweise nicht verfügbar, wenn 64-Bit-Prozesse verwendet werden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden 64-Bit-Registerkartenprozesse von Internet Explorer 11 verwendet, sofern der erweiterte geschützte Modus unter 64-Bit-Versionen von Windows aktiv ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden 32-Bit-Registerkartenprozesse von Internet Explorer 11 verwendet, sofern der erweiterte geschützte Modus unter 64-Bit-Versionen von Windows aktiv ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer dieses Feature über die Internet Explorer-Einstellungen ein- oder ausschalten. Dieses Feature ist standardmäßig deaktiviert.
  
  **Standard**: Aktiviert 
  
- **Internet Explorer ignore certificate errors** (Zertifikatfehler in Internet Explorer ignorieren)  
  Diese Richtlinieneinstellung verhindert, dass der Benutzer SSL/TLS-Zertifikatfehler (Secure Sockets Layer/Transport Layer Security), die die Navigation in Internet Explorer unterbrechen (z.B. „Abgelaufen“, „Gesperrt“ oder „Name stimmt nicht überein“ ) ignoriert. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer das Browsen nicht mehr fortsetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann der Benutzer entscheiden, ob Zertifikatfehler ignoriert werden sollen und das Browsen fortsetzen.
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer internet zone loading of XAML files** (Laden von XAML-Dateien in der Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie das Laden von XAML-Dateien (Extensible Application Markup Language) verwalten. XAML ist eine deklarative Markupsprache auf XML-Grundlage, die normalerweise zum Erstellen intelligenter Benutzeroberflächen und Grafiken verwendet wird, die Windows Presentation Foundation nutzen. Wenn Sie diese Richtlinieneinstellung aktivieren und im Dropdownfeld „Aktivieren“ festgelegt ist, werden die XAML-Dateien automatisch in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer zum Laden von XAML-Dateien aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden XAML-Dateien nicht in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer entscheiden, ob XAML-Dateien in Internet Explorer geladen werden sollen.
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer internet zone automatic prompt for file downloads** (Automatische Eingabeaufforderung für Dateidownloads in der Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob eine Eingabeaufforderung bei Dateidownloads angezeigt wird, die nicht vom Benutzer gestartet werden. Downloaddialogfelder werden unabhängig von dieser Einstellung für vom Benutzer gestartete Downloadvorgänge angezeigt. Wenn Sie diese Einstellung aktivieren, werden den Benutzern Downloaddialogfelder für automatische Downloadversuche angezeigt. Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, werden Dateidownloads, die nicht von Benutzern gestartet werden, blockiert, und Benutzern wird die Benachrichtigungsleiste anstelle des Downloaddialogfelds angezeigt. Die Benutzer können dann auf die Benachrichtigungsleiste klicken, um den Dateidownload zu genehmigen.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files** (Sicherheitswarnung für potenziell unsichere Dateien in der eingeschränkten Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob die Nachricht „Datei öffnen – Sicherheitswarnung“ angezeigt wird, wenn der Benutzer versucht, ausführbare Dateien oder andere potenziell unsichere Dateien (z.B. aus einer Dateifreigabe im Intranet über den Datei-Explorer) zu öffnen. Wenn Sie diese Richtlinieneinstellung aktivieren und „Aktivieren“ im Dropdownfeld auswählen, werden diese Dateien ohne Sicherheitswarnung geöffnet. Wenn Sie das Dropdownfeld auf „Bestätigen“ einstellen, wird eine Sicherheitswarnung angezeigt, bevor die Dateien geöffnet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden diese Dateien nicht geöffnet. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer konfigurieren, wie der Computer diese Dateien behandeln soll. Standardmäßig werden diese Dateien in der eingeschränkten Zone blockiert, in der Intranetzone sowie in Zonen für lokale Computer aktiviert und in Internetzonen und vertrauenswürdigen Zonen auf „Bestätigen“ festgelegt.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone cross site scripting filter** (Cross-Site Scripting-Filter in der Internetzone von Internet Explorer)  
  Mit dieser Richtlinie können Sie steuern, ob websiteübergreifende Skripteinschleusungen in Websites in dieser Zone vom XSS-Filter (Cross-Site Scripting) erkannt und verhindert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der XSS-Filter für Websites in dieser Zone aktiviert, um Versuche einer websiteübergreifenden Skripteinschleusung zu blockieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der XSS-Filter für Websites in dieser Zone deaktiviert, und Internet Explorer lässt die websiteübergreifende Skripteinschleusung zu.
  
  **Standard**: Aktiviert 
  
- **Internet Explorer fallback to SSL3** (Fallback auf SSL3 in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie unsichere Fallbacks auf SSL 3.0 blockieren. Wenn die Richtlinie aktiviert ist und TLS 1.0 oder höher einen Fehler verursacht, versucht Internet Explorer, über SSL 3.0 oder eine niedrigere Version eine Verbindung mit Websites herzustellen. Es wird empfohlen, unsichere Fallbacks nicht zuzulassen, um Man-in-the-Middle-Angriffe zu vermeiden. Die Richtlinie wirkt sich nicht darauf aus, welche Sicherheitsprotokolle aktiviert sind. Wenn Sie diese Richtlinie deaktivieren, werden die Standardeinstellungen des Systems verwendet.
  
  **Standard**: Keine Standorte 
  
- **Internet Explorer locked down internet zone java permissions** (SmartScreen-Filter für gesperrte Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.
  
  **Standard**: Aktiviert 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame** (Anwendungen und Dateien in einem iFrame in einer eingeschränkten Zone in Internet Explorer starten)  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob Anwendungen ausgeführt und Dateien aus einem iFrame-Verweis im HTML-Code der Seiten in dieser Zone heruntergeladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Anwendungen ausführen und Dateien aus iFrames auf den Seiten in dieser Zone ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ aus dem Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob Anwendungen ausgeführt und Daten aus iFrames auf den Seiten in dieser Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Anwendungen ausführen und keine Daten aus iFrames auf den Seiten in dieser Zone herunterladen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer keine Anwendungen ausführen und keine Daten aus iFrames auf den Seiten in dieser Zone herunterladen.
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer bypass smart screen warnings about uncommon files** (SmartScreen-Warnungen zu ungewöhnlichen Dateien in Internet Explorer umgehen)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer Warnungen des SmartScreen-Filters umgehen können. Der SmartScreen-Filter warnt Benutzer vor ausführbaren Dateien im Internet, die selten von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung aktivieren, hindern die Warnungen des SmartScreen-Filters Benutzer am Herunterladen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Warnungen des SmartScreen-Filters umgehen.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone protected mode** (Popupblocker für die Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob unerwünschte Popupfenster angezeigt werden. Popupfenster, die geöffnet werden, wenn der Endbenutzer auf einen Link klickt, werden nicht blockiert. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die meisten unerwünschten Popupfenster nicht angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Popupfenster angezeigt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die meisten unerwünschten Popupfenster nicht angezeigt.
  
  **Standard**: Aktivieren  
  
- **Internet Explorer processes consistent MIME handling** (Prozesse für die konsistente MIME-Verarbeitung in Internet Explorer)  
  Internet Explorer enthält dynamische Binärverhalten: Komponenten, die spezifische Funktionalität für die HTML-Elemente einkapseln, an die sie angefügt sind. Mit dieser Richtlinieneinstellung wird gesteuert, ob Binärverhalten durch die Sicherheitseinschränkungen verhindert oder zugelassen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Binärverhalten für alle Datei-Explorer- und Internet Explorer-Prozesse verhindert. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Binärverhalten für alle Datei-Explorer- und Internet Explorer-Prozesse zugelassen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Binärverhalten für alle Datei-Explorer- und Internet Explorer-Prozesse verhindert.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone java permissions (Java-Berechtigungen für eingeschränkte Zonen in Internet Explorer)**  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.
  
  **Standard**: Java deaktivieren  
    
  
- **Internet Explorer Active X controls in protected mode** (ActiveX-Steuerelemente im geschützten Modus in Internet Explorer)  
  Diese Richtlinieneinstellung verhindert, dass ActiveX-Kontrollen im geschützten Modus ausgeführt werden, wenn der erweiterte geschützte Modus aktiviert ist. Hat ein Benutzer eine ActiveX-Kontrolle installiert, die nicht mit dem erweiterten geschützten Modus kompatibel ist, und versucht eine Website, diese Kontrolle zu laden, zeigt Internet Explorer dem Benutzer eine entsprechende Benachrichtigung an und bietet die Option an, die Website im regulären geschützten Modus auszuführen. Diese Richtlinieneinstellung deaktiviert diese Benachrichtigung und erzwingt die Ausführung aller Websites im erweiterten geschützten Modus. Der erweiterte geschützte Modus bietet einen zusätzlichen Schutz gegen Websites mit Schadsoftware, indem er bei 64-Bit-Versionen von Windows 64-Bit-Prozesse verwendet. Bei Computern mit Windows 8 oder höher beschränkt der erweiterte geschützte Modus außerdem die Speicherorte von Internet Explorer in der Registrierung und im Dateisystem. Wenn ein Benutzer bei aktiviertem erweiterten geschützten Modus eine Website aufruft, die versucht, eine ActiveX-Kontrolle zu laden, die nicht mit dem erweiterten geschützten Modus kompatibel ist, zeigt Internet Explorer dem Benutzer eine entsprechende Benachrichtigung an und bietet die Option an, die Website im regulären geschützten Modus auszuführen. Wenn Sie diese Richtlinieneinstellung deaktivieren, zeigt der Internet Explorer dem Benutzer die Option, den erweiterten geschützten Modus zu deaktivieren, nicht an. Alle Websites, die im geschützten Modus ausgeführt werden sollten, werden im erweiterten geschützten Modus ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, zeigt Internet Explorer dem Benutzer eine Benachrichtigung an, in der er ihm die Option bietet, Websites mit nicht kompatiblen ActiveX-Kontrollen im regulären geschützten Modus auszuführen.  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone loading of XAML files** (Laden von XAML-Dateien in eingeschränkten Zonen in Internet Explorer zulassen)  
  Mit dieser Richtlinieneinstellung können Sie das Laden von XAML-Dateien (Extensible Application Markup Language) verwalten. XAML ist eine deklarative Markupsprache auf XML-Grundlage, die normalerweise zum Erstellen intelligenter Benutzeroberflächen und Grafiken verwendet wird, die Windows Presentation Foundation nutzen. Wenn Sie diese Richtlinieneinstellung aktivieren und im Dropdownfeld „Aktivieren“ festgelegt ist, werden die XAML-Dateien automatisch in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer zum Laden von XAML-Dateien aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden XAML-Dateien nicht in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer entscheiden, ob XAML-Dateien in Internet Explorer geladen werden sollen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer processes MK protocol security restriction** (Internet Explorer-Prozesse, Sicherheitseinschränkung für Skriptfenster)  
  Internet Explorer lässt zu, das Skripts programmgesteuert Fenster verschiedener Typen öffnen und in Größe und Position anpassen können. Die Sicherheitsfunktion für Fenstereinschränkungen schränkt Popupfenster ein und verhindert, dass Skripts Fenster anzeigen, in denen Titel- und Statusleiste für den Benutzer nicht sichtbar sind oder die die Sichtbarkeit der Titel- und Statusleiste anderer Fenster behindern. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Skriptfenster für alle Prozesse eingeschränkt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden Skriptfenster nicht eingeschränkt.
  
  **Standard**: Aktiviert   
  
- **Internet Explorer restricted zone download signed Active X controls** (Signierte ActiveX-Steuerelemente und -Plug-Ins in eingeschränkten Zonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob ActiveX-Steuerelemente und Plug-Ins über die festgelegte Zone auf Seiten in Internet Explorer ausgeführt werden kann. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Steuerelemente und Plug-Ins ohne Benutzereingriff ausgeführt. Wenn Sie die Option „Bestätigen“ im Dropdownfeld ausgewählt haben, werden Benutzer dazu aufgefordert, auszuwählen, ob Steuerelemente oder Plug-Ins ausgeführt werden dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Steuerelemente und Plug-Ins nicht ausgeführt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Steuerelemente und Plug-Ins nicht ausgeführt.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting** (ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer ausführen, die für die Skripterstellung als sicher gekennzeichnet wurden)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob ein ActiveX-Steuerelement, das für die Skripterstellung als sicher gekennzeichnet wurde, mit einem Skript interagieren darf. Wenn Sie diese Richtlinie aktivieren, kann mit Skripts automatisch ohne Benutzereingriff interagiert werden. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob sie die Skriptinteraktion erlauben möchten. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist keine Skriptinteraktion erlaubt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, ist keine Skriptinteraktion erlaubt.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone logon options** (Anmeldeoptionen für eingeschränkte Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Einstellungen für Anmeldeoptionen verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie eine der folgenden Anmeldeoptionen auswählen. 
  - *Anonym*: Verwenden Sie die anonyme Anmeldung, um die HTTP-Authentifizierung zu deaktivieren. Das Gastkonto kann nur für das CIFS-Protokoll (Common Internet File System) verwendet werden. 
  - *Nach Benutzername und Kennwort fragen*: Verwenden Sie „Nach Benutzername und Kennwort fragen“, um die Benutzer-IDs und Kennwörter von Benutzern abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. 
  - *Automatisches Anmelden nur in der Intranetzone* – Verwenden Sie diese Option, um Benutzer-IDs und Kennwörter von Benutzern in anderen Zonen abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. 
  - *Automatische Anmeldung mit aktuellem Benutzernamen und Kennwort* – Verwenden Sie diese Option, um die Anmeldung mithilfe der NTLM-Authentifizierung (auch bekannt als „integrierte Windows-Authentifizierung“ oder „Windows NT Challenge Response“) durchzuführen. Wenn der Server die NTLM-Authentifizierung unterstützt, wird der Netzwerkbenutzername und das Kennwort des Benutzers für die Anmeldung verwendet. Wenn die NTLM-Authentifizierung vom Server nicht unterstützt wird, wird der Benutzer dazu aufgefordert, seinen Benutzernamen und sein Kennwort einzugeben. 

  Wenn Sie diese Richtlinieneinstellung deaktivieren, wird die *automatische Anmeldung nur in der Intranetzone zugelassen*. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird *Nach Benutzername und Kennwort fragen* für die Anmeldung festgelegt.
  
  **Standard**: Anonym  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe** (ActiveX-Steuerelementen in vertrauenswürdigen Zonen in Internet Explorer initialisieren und skripten, die als unsicher gekennzeichnet sind)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer check server certificate revocation** (Serverzertifikatwiderrufstatus in Internet Explorer prüfen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Internet Explorer den Widerrufstatus der Serverzertifikat prüft. Zertifikate werden widerrufen, wenn sie kompromittiert wurden oder nicht mehr gültig sind. Durch diese Option wird verhindert, dass Benutzer vertrauliche Daten an eine Website übermitteln, die unter Betrugsverdacht steht oder nicht sicher ist. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer, ob Serverzertifikate widerrufen wurden. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer nicht, ob Serverzertifikate widerrufen wurden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer nicht, ob Serverzertifikate widerrufen wurden.
  
  **Standard**: Aktiviert 
  
- **Internet Explorer internet zone less privileged sites** (Websites mit geringeren Berechtigung in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Websites aus Zonen mit geringeren Berechtigungen, z.B. eingeschränkte Websites, zu dieser Zone navigieren können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Websites aus Zonen mit geringeren Berechtigungen neue Fenster in dieser Zone öffnen oder zu dieser Zone navigieren. Die Sicherheitszone wird ohne den zusätzlichen Schutz durch das Sicherheitsfeature „Schutz vor Zonenanhebung“ ausgeführt. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer gewarnt, dass er dabei ist, in einen möglicherweise gefährlichen Bereich zu navigieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden potentiell gefährliche Navigationsvorgänge verhindert. Wie von „Schutz vor Zonenanhebung“ festgelegt, ist das Internet Explorer-Sicherheitsfeature ist in dieser Zone aktiviert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Websites aus Zonen mit geringeren Berechtigungen neue Fenster in dieser Zone öffnen oder zu dieser Zone navigieren.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone file downloads** (Dateidownloads in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Dateidownloads aus dieser Zone zulässig sind. Diese Option hängt von der Zone der Webseite ab, die den Downloadlink enthält, und nicht von der Zone, in die heruntergeladen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, können Dateien aus der Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können keine Dateien aus der Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können keine Dateien aus der Zone heruntergeladen werden.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with authenticode** (Mit Authenticode signierte .NET Framework-Komponenten in Internetzonen von Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer prevent per user installation of Active X controls** (Installation von ActiveX-Steuerelementen pro Benutzer in Internet Explorer verhindern)  
  Mit dieser Richtlinieneinstellung können Sie die Installation von ActiveX-Steuerelement pro Benutzer verhindern. Wenn Sie diese Richtlinieneinstellung aktivieren, können keine ActiveX-Steuerelemente pro Benutzer installiert werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können ActiveX-Steuerelemente pro Benutzer installiert werden.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer prevent managing smart screen filter** (Verwalten des SmartScreen Filters in Internet Explorer verhindern)  
  Diese Richtlinieneinstellung verhindert, dass der Benutzer den SmartScreen Filter verwalten kann, der den Benutzer warnt, wenn er eine Website besucht, die in der Vergangenheit durch Phishing persönliche Informationen gesammelt hat, oder wenn bekannt ist, dass die Website Schadsoftware hostet. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der Benutzer nicht aufgefordert, den SmartScreen-Filter zu aktivieren. Alle Websiteadressen, die sich nicht auf der Zulassungsliste des Filters befinden, werden automatisch an Microsoft gesendet, ohne dass der Benutzer dies bestätigen muss. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird der Benutzer bei der ersten Ausführung aufgefordert, den SmartScreen Filter zu aktivieren oder zu deaktivieren.
  
  **Standard**: Aktivieren  
  
- **Internet Explorer processes MIME sniffing safety feature** (Internet Explorer-Prozesse, Sicherheitsfunktion für MIME-Ermittlung)  
  Diese Richtlinieneinstellung bestimmt, ob die MIME-Ermittlung von Internet Explorer die Höherstufung einer Datei eines bestimmten Typs auf einen gefährlicheren Dateitypen verhindert. Wenn Sie diese Einstellung aktivieren, stuft die MIME-Ermittlung eine Datei eines bestimmten Typs nie auf einen gefährlicheren Dateityp hoch. Wenn Sie diese Richtlinieneinstellung deaktivieren, lassen Internet Explorer-Prozesse die Höherstufung eines Dateityps auf einen gefährlicheren Dateityp durch die MIME-Ermittlung zu. Wenn Sie diese Einstellung nicht konfigurieren, stuft die MIME-Ermittlung eine Datei eines bestimmten Typs nie auf einen gefährlicheren Dateityp hoch.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone download signed Active X controls** (Signierte ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer herunterladen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer signierte ActiveX-Steuerelemente auf einer Seite in der Zone herunterladen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer signierte Steuerelemente ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ in der Dropdownliste auswählen, werden Benutzer zur Bestätigung aufgefordert, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können signierte Steuerelemente nicht heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die Benutzer gefragt, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer auto complete** (AutoVervollständigen in Internet Explorer)  
  Die Funktion AutoVervollständigen kann Benutzernamen und Kennwörter speichern und beim Ausfüllen von Formularen vorschlagen. Wenn Sie diese Einstellung aktivieren, können die Benutzer die Einstellungen „Benutzernamen und Kennwörter für Formulare“ und „Nachfragen, ob Kennwörter gespeichert werden sollen“ anpassen. Die Funktion AutoVervollständigen wird für Benutzernamen und Kennwörter in Formularen aktiviert. Sie müssen sich entscheiden, ob Sie „Nachfragen, ob Kennwörter gespeichert werden sollen“ aktivieren möchten. Wenn Sie diese Einstellung deaktivieren, können die Benutzer die Einstellungen „Benutzernamen und Kennwörter für Formulare“ und „Nachfragen, ob Kennwörter gespeichert werden sollen“ nicht anpassen. Die Funktion AutoVervollständigen wird für Benutzernamen und Kennwörter in Formularen deaktiviert. Der Benutzer kann auch nicht selbst festlegen, dass er zur Bestätigung aufgefordert wird, ob das Kennwort gespeichert werden soll. Wenn Sie diese Einstellung nicht konfigurieren, kann der Benutzer AutoVervollständigen für „Benutzernamen und Kennwörter für Formulare“ und „Nachfragen, ob Kennwörter gespeichert werden sollen“ selbst aktivieren. Benutzer müssen zu „Internetoptionen“ navigieren und dann auf die Registerkarte „Inhalte“ und auf „Einstellungen“ klicken, um diese Option anzuzeigen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone allow vbscript to run** (Zulassen der Ausführung des VBScript in einer Internet Explorer-Zone)  
  Diese Einstellung bestimmt, ob das VBScript auf Seiten in bestimmten Internet Explorer-Zonen ausgeführt werden kann. Zu den Optionen gehören: 
  - *Aktivieren*: Das VBScript wird auf Seiten in bestimmten Zonen ohne Interaktionen ausgeführt. 
  - *Bestätigung*: Mitarbeiter werden aufgefordert festzulegen, ob das VBScript in der Zone ausgeführt werden soll. 
  - *Deaktivieren*: Das VBScript wird in der Zone nicht ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird das VBScript ohne Interaktionen in der angegebenen Zone ausgeführt. 
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls** (Nur genehmigte Domänen können das TDC-ActiveX-Steuerelement in eingeschränkten Zonen in Internet Explorer verwenden)  
  Diese Richtlinieneinstellung steuert, ob der Benutzer das TDC-ActiveX-Steuerelement auf Websites ausführen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird das TDC-ActiveX-Steuerelement nicht von Websites in dieser Zone ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird das TDC-ActiveX-Steuerelement von allen Websites in dieser Zone ausgeführt.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in vertrauenswürdigen Zonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer local machine zone java permissions** (Java-Berechtigungen für Zonen mit lokalen Computern in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Mittlere Sicherheit“ festgelegt.
  
  **Standard**: Java deaktivieren 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in Intranetzonen in Internet Explorer ausführen) Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausführen soll, um zu überprüfen, ob sie auf Seiten sicher geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.
  
  **Standard**: Deaktiviert  

- **Internet Explorer restricted zone smart screen** (Scriptlets in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer Skriptlets ausführen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Skriptlets ausführen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Skriptlets nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Skriptlets aktivieren oder deaktivieren.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer processes notification bar** (Internet Explorer-Prozesse, Benachrichtigungsleiste)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob die Benachrichtigungsleiste für Internet Explorer-Prozesse angezeigt wird, wenn Datei- oder Codeinstallationen eingeschränkt sind. Die Benachrichtigungsleiste wird standardmäßig für Internet Explorer-Prozesse angezeigt. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die Benachrichtigungsleiste für Internet Explorer-Prozesse angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird die Benachrichtigungsleiste nicht für Internet Explorer-Prozesse angezeigt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Benachrichtigungsleiste für Internet Explorer-Prozesse angezeigt.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer internet zone download signed Active X controls** (Herunterladen signierter ActiveX-Steuerelemente in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer signierte ActiveX-Steuerelemente auf einer Seite in der Zone herunterladen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer signierte Steuerelemente ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ in der Dropdownliste auswählen, werden Benutzer zur Bestätigung aufgefordert, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können signierte Steuerelemente nicht heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die Benutzer gefragt, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone smart screen** (SmartScreen Filter in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.
  
  **Standard**: Aktiviert  
  
- **Schaltfläche „Run this time“ (Dieses Mal ausführen) für veraltete ActiveX-Steuerelemente in Internet Explorer entfernen**  
  Mit dieser Richtlinieneinstellung können Sie verhindern, dass Benutzer die Schaltfläche „Run this time“ (Dieses Mal ausführen) sehen und bestimmte veraltete ActiveX-Steuerelemente in Internet Explorer ausführen. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Schaltfläche „Run this time“ (Dieses Mal ausführen) in der Warnmeldung nicht sehen, die angezeigt wird, wenn Internet Explorer ein veraltetes ActiveX-Steuerelement blockiert. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Schaltfläche „Run this time“ in der Warnung sehen, die angezeigt wird, wenn Internet Explorer ein veraltetes ActiveX-Steuerelement in Internet Explorer blockiert. Durch Klicken auf diese Schaltfläche kann der Benutzer das veraltete ActiveX-Steuerelement einmal ausführen. Weitere Informationen finden Sie unter „Outdated ActiveX Controls“ (Veraltete ActiveX-Steuerelemente) in der TechNet-Bibliothek in Internet Explorer.
  
  **Standard**: Aktiviert 
  
- **Anwendungen und Dateien in einem iFrame starten für die Internetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob Anwendungen ausgeführt und Dateien aus einem iFrame-Verweis im HTML-Code der Seiten in dieser Zone heruntergeladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Anwendungen ausführen und Dateien aus iFrames auf den Seiten in dieser Zone ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ aus dem Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob Anwendungen ausgeführt und Daten aus iFrames auf den Seiten in dieser Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Anwendungen ausführen und keine Daten aus iFrames auf den Seiten in dieser Zone herunterladen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Benutzer dazu aufgefordert, zu entscheiden, ob Anwendungen ausgeführt und Daten aus iFrames auf den Seiten in dieser Zone heruntergeladen werden.
  
  **Standard**: Deaktivieren 
  
- **Fenster und Frames zwischen verschiedenen Domänen navigieren für die eingeschränkte Zone von Internet Explorer**  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern.
  
  **Standard**: Deaktivieren  
  
- **SmartScreen für die Internetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.
  
  **Standard**: Aktiviert  
  
- **Java-Berechtigungen für die gesperrte vertrauenswürdige Zone in Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.
  
  **Standard**: Java deaktivieren 
  
- **Signaturen von heruntergeladenen Programmen in Internet Explorer überprüfen**  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob Internet Explorer auf Computern von Benutzern ausführbare Programme auf digitale Signaturen überprüft (was den Herausgeber von signierter Software identifiziert und verifiziert, dass diese nicht verändert oder manipuliert wurde), bevor diese heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft Internet Explorer die digitalen Signaturen von ausführbaren Programmen und zeigt ihre Identitäten an, bevor sie auf Computer von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, überprüft Internet Explorer die digitalen Signaturen von ausführbaren Programmen nicht oder zeigt ihre Identitäten nicht an, bevor sie auf Computer von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinie nicht konfigurieren, überprüft Internet Explorer die digitalen Signaturen von ausführbaren Programmen nicht oder zeigt ihre Identitäten nicht an, bevor sie auf Computer von Benutzern heruntergeladen werden.
  
  **Standard**: Aktiviert  
  
- **Scripting von WebBrowser-Steuerelementen in der eingeschränkten Zone von Internet Explorer**  
  Diese Richtlinieneinstellung bestimmt, ob eine Seite eingebettete WebBrowser-Steuerelemente per Skript steuern kann. Wenn Sie diese Richtlinieneinstellung aktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement möglich. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement nicht möglich. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer den Skriptzugriff auf das WebBrowser-Steuerelement aktivieren oder deaktivieren. Standardmäßig ist der Skriptzugriff auf das WebBrowser-Steuerelement nur auf dem lokalen Computer und in Intranetzonen möglich.
  
  **Standard**: Deaktiviert  
  
- **Cross-Site Scripting-Filter in der eingeschränkten Zone von Internet Explorer**  
  Mit dieser Richtlinie können Sie steuern, ob websiteübergreifende Skripteinschleusungen in Websites in dieser Zone vom XSS-Filter (Cross-Site Scripting) erkannt und verhindert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der XSS-Filter für Websites in dieser Zone aktiviert, um Versuche einer websiteübergreifenden Skripteinschleusung zu blockieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der XSS-Filter für Websites in dieser Zone deaktiviert, und Internet Explorer lässt die websiteübergreifende Skripteinschleusung zu.
  
  **Standard**: Aktiviert  
  
- **Dynamische Binär- und Skriptverhalten in der eingeschränkten Zone von Internet Explorer**  
  Diese Richtlinieneinstellung ermöglicht Ihnen, dynamische Binär- und Skriptverhalten zu verwalten: Komponenten, die spezifische Funktionalität für die HTML-Elemente einkapseln, an die sie angefügt wurden. Wenn Sie diese Richtlinieneinstellung aktivieren, stehen Binär- und Skriptverhalten zur Verfügung. Wenn Sie „Vom Administrator genehmigt“ in der Dropdownliste auswählen, sind nur Verhalten verfügbar, die in der Liste „Vom Administrator zugelassenes Verhalten“ der Richtlinie „ Sicherheitseinschränkung für Binärverhalten“ aufgeführt sind. Wenn Sie diese Richtlinieneinstellung deaktivieren, stehen Binär- und Skriptverhalten nicht zur Verfügung, es sei denn, Anwendungen haben einen benutzerdefinierten Sicherheits-Manager implementiert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, stehen Binär- und Skriptverhalten nicht zur Verfügung, es sei denn, Anwendungen haben einen benutzerdefinierten Sicherheits-Manager implementiert.
  
  **Standard**: Deaktivieren  
  
- **Überprüfung der Sicherheitseinstellungen von Internet Explorer**  
  Mit dieser Richtlinieneinstellung wird die Funktion zur Überprüfung der Sicherheitseinstellungen deaktiviert, die die Sicherheitseinstellungen von Internet Explorer überprüft, um zu bestimmen, wann die Einstellungen für Internet Explorer ein potenzielles Risiko darstellen. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die Funktion deaktiviert. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die Funktion aktiviert.
  
  **Standard**: Aktiviert  
  
- **Sicherheitswarnung für potenziell unsichere Dateien in der Internetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob die Nachricht „Datei öffnen – Sicherheitswarnung“ angezeigt wird, wenn der Benutzer versucht, ausführbare Dateien oder andere potenziell unsichere Dateien (z.B. aus einer Dateifreigabe im Intranet über den Datei-Explorer) zu öffnen. Wenn Sie diese Richtlinieneinstellung aktivieren und „Aktivieren“ im Dropdownfeld auswählen, werden diese Dateien ohne Sicherheitswarnung geöffnet. Wenn Sie das Dropdownfeld auf „Bestätigen“ einstellen, wird eine Sicherheitswarnung angezeigt, bevor die Dateien geöffnet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden diese Dateien nicht geöffnet. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer konfigurieren, wie der Computer diese Dateien behandeln soll. Standardmäßig werden diese Dateien in der eingeschränkten Zone blockiert, in der Intranetzone sowie in Zonen für lokale Computer aktiviert und in Internetzonen und vertrauenswürdigen Zonen auf „Bestätigen“ festgelegt.
  
  **Standard**: Eingabeaufforderung  
  
- **Java-Berechtigungen in der Intranetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Mittlere Sicherheit“ festgelegt.
  
  **Standard**: Hohe Sicherheit 
  
- **Veraltete ActiveX-Steuerelementen in Internet Explorer blockieren**  </br>
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Internet Explorer bestimmte veraltete ActiveX-Steuerelemente blockiert. Veraltete ActiveX-Steuerelemente werden in der Intranetzone nie blockiert. Wenn Sie diese Richtlinieneinstellung aktivieren, blockiert Internet Explorer veraltete ActiveX-Steuerelemente nicht mehr. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, blockiert Internet Explorer weiterhin bestimmte veraltete ActiveX-Steuerelemente. Weitere Informationen finden Sie unter „Outdated ActiveX Controls“ (Veraltete ActiveX-Steuerelemente) in der TechNet-Bibliothek in Internet Explorer.
  
  **Standard**: Aktiviert  
  
- **Popupblocker in der eingeschränkten Zone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob unerwünschte Popupfenster angezeigt werden. Popupfenster, die geöffnet werden, wenn der Endbenutzer auf einen Link klickt, werden nicht blockiert. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die meisten unerwünschten Popupfenster nicht angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Popupfenster angezeigt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die meisten unerwünschten Popupfenster nicht angezeigt.
  
  **Standard**: Aktivieren  
  
- **Internet Explorer processes MK protocol security restriction** (Internet Explorer-Prozesse, Sicherheitseinschränkung für MK-Protokoll)  
  Die Richtlinieneinstellung „Sicherheitseinschränkung für MK-Protokoll“ verringert die Angriffsfläche durch Blockieren des MK-Protokolls. Bei Ressourcen, die im MK-Prokoll gehostet werden, treten Fehler auf. Wenn Sie diese Richtlinieneinstellung aktivieren, wird das MK-Protokoll für den Datei-Explorer und Internet Explorer blockiert. Bei Ressourcen, die im MK-Protokoll gehostet werden, treten Fehler auf. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Anwendungen die MK-Protokoll-API verwenden. Ressourcen, die im MK-Protokoll gehostet werden, können für den Datei-Explorer und für Internet Explorer-Prozesse verwendet werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird das MK-Protokoll für den Datei-Explorer und Internet Explorer blockiert. Bei Ressourcen, die im MK-Protokoll gehostet werden, treten Fehler auf.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer trusted zone java permissions** (Java-Berechtigungen für vertrauenswürdige Zonen in Internet Explorer)  </br>
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Niedrige Sicherheit“ festgelegt.
  
  **Standard**: Hohe Sicherheit  
  
- **Internet Explorer restricted zone scripting of java applets** (Skripting von Java-Applets in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Applets in dieser Zone für Skripts verfügbar gemacht werden. Wenn Sie diese Richtlinie aktivieren, können Skripts automatisch und ohne Benutzereingriff auf Applets zugreifen. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob ein Skript auf Applets zugreifen darf. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Skripts nicht auf Applets zugreifen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Skripts nicht auf Applets zugreifen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer locked down restricted zone java permissions** (Java-Berechtigungen für gesperrte eingeschränkte Zonen in Internet Explorer)  </br>
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.
  
  **Standard**: Java deaktivieren 
  
- **Internet Explorer internet zone allow only approved domains to use Active X controls** (Nur genehmigte Domänen können das ActiveX-Steuerelement in Internetzonen in Internet Explorer verwenden)  </br>
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer dazu aufgefordert werden, zuzulassen, dass ActiveX-Steuerelemente auf Websites ausgeführt werden, die nicht die Website sind, auf der das ActiveX-Steuerelement installiert wurde. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Benutzer zur Bestätigung aufgefordert, bevor die ActiveX-Steuerelemente von Websites in dieser Zone ausgeführt werden können. Der Benutzer kann die Ausführung des Steuerelements wahlweise für die aktuelle Website oder für alle Websites zulassen. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Benutzer nicht pro Website zum Zulassen von ActiveX aufgefordert, und ActiveX-Steuerelemente dürfen für alle Websites in dieser Zone ausgeführt werden.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer include all network paths** (Alle Netzwerkpfade in Internet Explorer einbeziehen)  
  Alle Netzwerkpfade in Internet Explorer einbeziehen
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer internet zone protected mode** (Geschützter Modus in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie den geschützten Modus aktivieren. Im geschützten Modus wird Internet Explorer vor der Ausnutzung von Schwachstellen geschützt. Hierbei wird die Anzahl der Speicherorte in der Registrierung und im Dateisystem verringert, in die Internet Explorer schreiben kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der geschützte Modus aktiviert. Benutzer können den geschützten Modus nicht deaktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der geschützte Modus deaktiviert. Benutzer können den geschützten Modus nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer den geschützten Modus aktivieren oder deaktivieren.
  
  **Standard**: Aktivieren 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe** (ActiveX-Steuerelemente in Internetzonen in Internet Explorer initialisieren und skripten, die als unsicher gekennzeichnet sind)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt.
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer locked down restricted zone java permissions** (SmartScreen Filter für gesperrte eingeschränkte Zonen in Internet Explorer)  </br>
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer crash detection** (Absturzermittlung in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Absturzermittlungsfunktion der Add-On-Verwaltung verwalten. Wenn Sie diese Richtlinieneinstellung aktivieren, wird durch einen Absturz von Internet Explorer die Windows-Fehlerberichterstattung eingeleitet. Dieses Verhalten gibt es im Windows XP Professional Service Pack 1 und früher. Alle Richtlinieneinstellung für die Windows-Fehlerberichterstattung bleiben bestehen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, bleibt die Absturzermittlungsfunktion für die Add-On-Verwaltung aktiviert.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone java permissions** (Java-Berechtigungen in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Hohe Sicherheit“ festgelegt.
  
  **Standard**: Java deaktivieren  
  
- **Internet Explorer restricted zone active scripting** (Active Scripting in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Skriptcode auf Seiten in der Zone ausgeführt werden darf. Wenn Sie diese Richtlinieneinstellung aktivieren, wird Skriptcode automatisch auf Seiten in der Zone ausgeführt. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob Skriptcode auf Seiten in der Zone ausgeführt werden darf. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird kein Skriptcode auf Seiten in der Zone ausgeführt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird kein Skriptcode auf Seiten in der Zone ausgeführt.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone logon options** (Anmeldeoptionen für die Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Einstellungen für Anmeldeoptionen verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie eine der folgenden Anmeldeoptionen auswählen. Die Anmeldung kann anonym durchgeführt werden, um die HTTP-Authentifizierung zu deaktivieren, und das Gastkonto kann nur für das CIFS-Protokoll (Common Internet File System) verwendet werden. Sie können die Eingabe eines Benutzernamens und eines Kennworts anfordern, um die Benutzer-ID und Kennwörter von Benutzern abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. Sie können die automatische Anmeldung nur in der Intranetzone zulassen, um Benutzer-IDs und Kennwörter von Benutzern in anderen Zonen abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. Sie können die automatische Anmeldung mit dem aktuellen Benutzernamen und Kennwort durchführen, um die Anmeldung mithilfe der NTLM-Authentifizierung (auch bekannt als Windows NT Challenge Response) durchzuführen. Wenn der Server die NTLM-Authentifizierung unterstützt, werden der Netzwerkbenutzername und das Kennwort für die Anmeldung verwendet. Wenn die NTLM-Authentifizierung vom Server nicht unterstützt wird, wird der Benutzer dazu aufgefordert, seinen Benutzernamen und sein Kennwort einzugeben. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird die automatische Anmeldung nur in der Intranetzone zugelassen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird für die Anmeldung „Automatisches Anmelden nur in der Intranetzone“ festgelegt.
  
  **Standard**: Eingabeaufforderung  
  
- **Internet Explorer restricted zone allow vbscript to run** (Zulassen der Ausführung von VBScript in einer eingeschränkten Internet Explorer-Zone)  </br>  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob das VBScript über die in Internet Explorer festgelegte Zone auf Seiten ausgeführt werden kann. Wenn Sie die Option „Aktivieren“ im Dropdownfeld ausgewählt haben, kann das VBScript ohne Benutzereingriff verwendet werden. Wenn Sie die Option „Bestätigen“ im Dropdownfeld ausgewählt haben, werden Benutzer dazu aufgefordert, auszuwählen, ob das VBScript ausgeführt werden darf. Wenn Sie die Option „Deaktivieren“ im Dropdownfeld ausgewählt haben, wird die Ausführung des VBScript verhindert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren oder deaktivieren, wird die Ausführung des VBScript verhindert.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone drag content from different domains across windows** (Ziehen von Inhalten aus verschiedenen Domänen zwischen Fenstern in einer Internetzone in Internet Explorer)  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern.
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe** (Initialisierung und Skript von ActiveX-Steuerelementen werden in der Intranetzone in Internet Explorer als unsicher gekennzeichnet)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt.
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer download enclosures** (Herunterladen von Anlagen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird verhindert, dass Benutzer Dateianlagen aus einem Feed auf den Computer herunterladen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Feedsynchronisierungsengine nicht über die Eigenschaftenseite für Feeds zum Herunterladen von Anlagen konfigurieren. Entwickler können die Downloadeinstellung über die Feed-APIs nicht ändern. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Feedsynchronisierungsengine über die Eigenschaftenseite für Feeds zum Herunterladen von Anlagen konfigurieren. Außerdem können Entwickler die Downloadeinstellung dann über die Feed-APIs ändern.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone download unsigned Active X controls** (Herunterladen nicht signierter ActiveX-Steuerelemente in einer eingeschränkten Zone in Internet Explorer)  </br>
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer nicht signierte ActiveX-Steuerelemente aus der Zone herunterladen können. Insbesondere, wenn Code aus einer nicht vertrauenswürdigen Zone stammt, kann er potenziell schädlich sein. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer nicht signierte Steuerelemente ohne Benutzereingriff ausführen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob die Ausführung von nicht signierten Steuerelementen zugelassen werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer nicht signierte Steuerelemente nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer nicht signierte Steuerelemente nicht ausführen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone drag content from different domains within windows** (Ziehen von Inhalten aus verschiedenen Domänen in Fenstern in einer Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer nicht signierte ActiveX-Steuerelemente aus der Zone herunterladen können. Insbesondere, wenn Code aus einer nicht vertrauenswürdigen Zone stammt, kann er potenziell schädlich sein. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer nicht signierte Steuerelemente ohne Benutzereingriff ausführen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob die Ausführung von nicht signierten Steuerelementen zugelassen werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer nicht signierte Steuerelemente nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer nicht signierte Steuerelemente nicht ausführen.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer processes restrict Active X install** (Einschränken der Installation von ActiveX-Steuerelementen mit Internet Explorer-Prozessen)  </br>
  Diese Richtlinieneinstellung ermöglicht es Anwendungen, die das WebBrowser-Steuerelement hosten, die automatische Eingabeaufforderung für die Installation von ActiveX-Steuerelementen zu blockieren. Wenn Sie diese Richtlinieneinstellung aktivieren, blockiert das WebBrowser-Steuerelement die automatische Eingabeaufforderung für die Installation von ActiveX-Steuerelementen für alle Prozesse. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die automatische Eingabeaufforderung für die Installation von ActiveX-Steuerelementen nicht vom Webbrowsersteuerelement für alle Prozesse blockiert.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer internet zone scriptlets** (Skriptlets für Internetzonen in Internet Explorer) Mit dieser Richtlinieneinstellung können Sie verwalten, ob Benutzer Skriptlets ausführen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Skriptlets ausführen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Skriptlets nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Skriptlets aktivieren oder deaktivieren.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files** (Drag & Drop oder Kopieren und Einfügen von Dateien in einer eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer Dateien aus einer Quelle innerhalb der Zone per Drag & Drop verschieben oder kopieren und einfügen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Dateien automatisch aus dieser Zone per Drag & Drop verschieben oder kopieren und einfügen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob sie Dateien aus dieser Zone ziehen oder kopieren möchten. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Dateien aus dieser Zone nicht per Drag & Drop verschieben oder kopieren und einfügen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Benutzer dazu aufgefordert, auszuwählen, ob sie Dateien aus dieser Zone ziehen oder kopieren möchten.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer software when signature is invalid** (Software bei ungültiger Signatur in Internet Explorer) </br>
  Mit dieser Richtlinie können Sie verwalten, ob Software, z.B. ActiveX-Steuerelemente und Dateidownloads, von Benutzern installiert oder ausgeführt werden können, wenn die Signatur ungültig ist. Eine ungültige Signatur kann darauf hindeuten, dass die Datei manipuliert wurde. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Benutzer zum Installieren oder Ausführen von Dateien mit einer ungültigen Signatur aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Dateien mit ungültiger Signatur weder ausführen noch installieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer entscheiden, ob sie Dateien mit ungültiger Signatur ausführen oder installieren.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone copy and paste via script** (Kopieren und Einfügen in einer eingeschränkten Zone mithilfe eines Skripts in Internet Explorer) </br> Mit dieser Richtlinieneinstellung können Sie festlegen, ob Skripts in einer angegebenen Region Zwischenablagevorgänge (z.B. Ausschneiden, Kopieren und Einfügen) durchführen dürfen. Wenn Sie diese Richtlinieneinstellung aktivieren, können Skripts Zwischenablagevorgänge durchführen. Wenn Sie „Bestätigen“ im Dropdownfeld auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob Zwischenablagevorgänge ausgeführt werden dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Skripts keine Zwischenablagevorgänge durchführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Skripts keine Zwischenablagevorgänge durchführen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone drag content from different domains across windows** (Ziehen von Inhalten aus verschiedenen Domänen zwischen Fenstern in einer eingeschränkten Zone in Internet Explorer)  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern.  <br><br>
  **Standard**: Deaktiviert  
  
- **Internet Explorer users adding sites** (Internet Explorer-Benutzer dürfen keine Sites hinzufügen)  
  Durch diese Einstellung wird verhindert, dass Benutzer Sites zu Sicherheitszonen hinzufügen oder aus diesen entfernen. Bei einer Sicherheitszone handelt es sich um Websites, die die gleiche Sicherheitsstufe aufweisen. Wenn Sie diese Richtlinie aktivieren, werden die Verwaltungseinstellungen für Sites für Sicherheitszonen deaktiviert. (Sie können die Verwaltungseinstellungen für Sites für Sicherheitszonen aufrufen, indem Sie im Dialogfeld „Internetoptionen“ auf die Registerkarte „Sicherheit“ und dann auf die Schaltfläche „Sites“ klicken.) Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können Benutzer Websites hinzufügen oder aus den Zonen für vertrauenswürdige oder eingeschränkte Sites entfernen oder die Einstellungen für das lokale Intranet bearbeiten. Durch diese Richtlinie wird verhindert, dass Benutzer die Verwaltungseinstellungen für Sites für Sicherheitszonen ändern, die vom Administrator eingerichtet wurden. Hinweis: Die Richtlinie „Sicherheitsseite deaktivieren“ (unter \Benutzerkonfiguration\Administrative Vorlagen\Windows-Komponenten\Internet Explorer\Internetsystemsteuerung) entfernt die Registerkarte „Sicherheit“ aus der Benutzeroberfläche und hat somit Vorrang vor dieser Richtlinie. Ist sie aktiviert, wird diese Richtlinie ignoriert. Weitere Informationen finden Sie im Abschnitt zur Richtlinie „Sicherheitszonen: Nur Computereinstellungen verwenden“.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone script initiated windows** (Durch Skripts geöffnete Fenster für die Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Einschränkungen zu durch Skripts geöffneten Popupfenstern und Fenstern mit Titel und Leisten verwalten. Wenn Sie diese Richtlinieneinstellung aktivieren, gilt das Sicherheitsfeature für Fenstereinschränkungen in dieser Zone nicht. Die Sicherheitszone wird also ohne die Sicherheitsebene ausgeführt, die von diesem Feature bereitgestellt wird. Wenn Sie diese Richtlinieneinstellung deaktivieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer – Sicherheitszonen: Nur Computereinstellungen verwenden**  
  Mit dieser Einstellung werden Informationen zu Sicherheitszonen für alle Benutzer desselben Computers angewendet. Bei einer Sicherheitszone handelt es sich um Websites, die die gleiche Sicherheitsstufe aufweisen. Wenn Sie diese Richtlinie aktivieren, werden die Änderungen, die ein Benutzer an einer Sicherheitszone vornimmt, für alle Benutzer dieses Computers übernommen. Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können die Benutzer des Computers eigene Einstellungen für Sicherheitszonen einrichten. Verwenden Sie diese Richtlinie, um sicherzustellen, dass die Einstellungen für Sicherheitszonen einheitlich auf einen Benutzer angewendet werden und sich nicht von Benutzer zu Benutzer unterscheiden. Weitere Informationen finden Sie im Abschnitt zur Richtlinie „Sicherheitszonen: Benutzer können keine Einstellungen ändern“.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer locked down local machine zone java permissions** (Java-Berechtigungen für gesperrte Zonen mit lokalen Computern in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.
  
  **Standard**: Java deaktivieren 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer ausführen)  </br>
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode** (Mit Authenticode signierte .NET Framework-Komponenten in der eingeschränkten Zone von Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone access to data sources** (Zugriff auf Datenquellen in eingeschränkten Zonen in Internet Explorer)  
  Durch diese Richtlinieneinstellung können Sie festlegen, ob Internet Explorer mithilfe von Microsoft XML Parser (MSXML) oder ActiveX Data Objects (ADO) auf Daten aus anderen Sicherheitszonen zugreifen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer eine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie im Dropdownfeld „Prompt“ (Bestätigen) auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob eine Seite in der Zone geladen werden soll, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen.
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer internet zone don't run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in Internetzonen in Internet Explorer ausführen)  </br>
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone copy and paste via script** (Kopieren und Einfügen in einer Internetzone mithilfe eines Skripts in Internet Explorer) </br> Mit dieser Richtlinieneinstellung können Sie festlegen, ob Skripts in einer angegebenen Region Zwischenablagevorgänge (z.B. Ausschneiden, Kopieren und Einfügen) durchführen dürfen. Wenn Sie diese Richtlinieneinstellung aktivieren, können Skripts Zwischenablagevorgänge durchführen. Wenn Sie „Bestätigen“ im Dropdownfeld auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob Zwischenablagevorgänge ausgeführt werden dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Skripts keine Zwischenablagevorgänge durchführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Skripts Zwischenablagevorgänge durchführen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer use Active X installer service** (ActiveX-Installationsdienst in Internet Explorer verwenden)  </br>
  Mit dieser Richtlinieneinstellung können Sie festlegen, wie ActiveX-Steuerelemente installiert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente nur installiert, wenn der ActiveX-Installationsdienst vorhanden ist und dafür konfiguriert wurde, die Installation von ActiveX-Steuerelementen zuzulassen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden ActiveX-Steuerelemente (einschließlich Benutzersteuerelemente) über den Standardinstallationsvorgang installiert.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer processes protection from zone elevation** (Schutz vor Erhöhung der Rechte von Prozessen für Zonen in Internet Explorer)  
  Internet Explorer wendet auf jede Website, die geöffnet wird, Einschränkungen an. Diese hängen vom Speicherort der Webseite ab (z.B. Internet, Intranet, lokaler Computer). Für Webseiten, die sich auf lokalen Computern befinden, gelten beispielsweise die niedrigsten Sicherheitseinschränkungen. Sie befinden sich in der Zone „Lokaler Computer“, sodass diese in der Regel das Primärziel von Angreifern darstellt. Wenn Sie diese Richtlinieneinstellung aktivieren, kann jede Zone gegen die Erhöhung der Rechte durch alle Prozesse geschützt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, ist kein Schutz vor Prozessen vorhanden, die nicht Internet Explorer oder die in der Prozessliste aufgeführten Prozesse darstellen.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer internet zone download unsigned Active X controls** (Herunterladen nicht signierter ActiveX-Steuerelemente in Internetzonen in Internet Explorer)  </br>
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer nicht signierte ActiveX-Steuerelemente aus der Zone herunterladen können. Insbesondere, wenn Code aus einer nicht vertrauenswürdigen Zone stammt, kann er potenziell schädlich sein. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer nicht signierte Steuerelemente ohne Benutzereingriff ausführen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob die Ausführung von nicht signierten Steuerelementen zugelassen werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer nicht signierte Steuerelemente nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer nicht signierte Steuerelemente nicht ausführen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone navigate windows and frames across different domains** (Windows und Frames von verschiedenen Domänen öffnen – Internetzone in Internet Explorer)  </br>
  Mit dieser Richtlinieneinstellung können Sie festlegen, wie Fenster und Frames geöffnet werden, und den Zugriff auf Anwendungen über verschiedene Domänen regeln. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Fenster und Frames von anderen Domänen öffnen und auf Anwendungen von anderen Domänen zugreifen. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob Fenster und Frames auf Anwendungen von anderen Domänen zugreifen dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Fenster und Frames für den Zugriff auf Anwendungen von anderen Domänen öffnen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Fenster und Frames von anderen Domänen öffnen und auf Anwendungen von anderen Domänen zugreifen.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone updates to status bar via script** (Skriptgesteuerte Updates für die Statusleiste in der Internetzone von Internet Explorer)  
  Über diese Richtlinieneinstellung können Sie festlegen, ob die Statusleiste in der Zone durch Skripts aktualisiert werden darf. Wenn Sie diese Richtlinieneinstellung aktivieren, kann die Statusleiste durch Skripts aktualisiert werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann die Statusleiste nicht über Skripts aktualisiert werden.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone include local path when uploading files to server** (Informationen zu lokalen Pfaden beim Hochladen von Dateien auf Server einfügen – eingeschränkte Zone in Internet Explorer)  </br> Mit dieser Richtlinieneinstellung können Sie festlegen, ob Informationen zu lokalen Pfaden beim Hochladen einer Datei über ein HTML-Formular übermittelt werden. Wenn die Informationen zu lokalen Pfaden übermittelt werden, kann es vorkommen, dass einige davon versehentlich für den Server offengelegt werden. Dabei kann es sich beispielsweise um Dateien vom Desktop des Benutzers handeln, die den Benutzernamen im Pfad enthalten. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular entfernt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt werden sollen. Die Pfadinformationen werden standardmäßig gesendet.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer processes restrict file download** (Dateidownloads für Prozesse in Internet Explorer einschränken)  </br> Diese Richtlinieneinstellung ermöglicht es Anwendungen, die das WebBrowser-Steuerelement hosten, die automatische Eingabeaufforderung für nicht vom Benutzer initiierte Dateidownloads zu blockieren. Wenn Sie diese Richtlinieneinstellung aktivieren, blockiert das WebBrowser-Steuerelement die automatische Eingabeaufforderung für nicht vom Benutzer initiierte Dateidownloads für alle Prozesse. Wenn Sie diese Richtlinieneinstellung deaktivieren, blockiert das WebBrowser-Steuerelement die automatische Eingabeaufforderung für nicht vom Benutzer initiierte Dateidownloads für alle Prozesse nicht.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls** (Nur genehmigte Domänen können das ActiveX-Steuerelement in eingeschränkten Zonen in Internet Explorer verwenden)  </br>
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer dazu aufgefordert werden, zuzulassen, dass ActiveX-Steuerelemente auf Websites ausgeführt werden, die nicht die Website sind, auf der das ActiveX-Steuerelement installiert wurde. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Benutzer zur Bestätigung aufgefordert, bevor die ActiveX-Steuerelemente von Websites in dieser Zone ausgeführt werden können. Der Benutzer kann die Ausführung des Steuerelements wahlweise für die aktuelle Website oder für alle Websites zulassen. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Benutzer nicht pro Website zum Zulassen von ActiveX aufgefordert, und ActiveX-Steuerelemente dürfen für alle Websites in dieser Zone ausgeführt werden.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe** (ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer initialisieren und ausführen, die als unsicher gekennzeichnet sind)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt.
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer users changing policies** (Ändern von Einstellungen durch Benutzer in Internet Explorer)  
    Durch diese Einstellung wird verhindert, dass Benutzer die Einstellungen für Sicherheitszonen ändern können. Bei einer Sicherheitszone handelt es sich um Websites, die die gleiche Sicherheitsstufe aufweisen. Wenn Sie diese Richtlinie aktivieren, werden die Schaltfläche „Custom Level“ (Stufe anpassen) und der Schieberegler „Sicherheitsstufe“ auf der Registerkarte „Sicherheit“ im Dialogfeld „Internetoptionen“ deaktiviert. Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können Benutzer die Einstellungen für Sicherheitszonen bearbeiten. Durch diese Richtlinie wird verhindert, dass Benutzer die Einstellungen für Sicherheitszonen ändern, die vom Administrator eingerichtet wurden. Hinweis: Die Richtlinie „Sicherheitsseite deaktivieren“ (unter \Benutzerkonfiguration\Administrative Vorlagen\Windows-Komponenten\Internet Explorer\Internetsystemsteuerung) entfernt die Registerkarte „Sicherheit“ aus Internet Explorer in der Systemsteuerung und hat somit Vorrang vor dieser Richtlinie. Ist sie aktiviert, wird diese Richtlinie ignoriert. Weitere Informationen finden Sie im Abschnitt zur Richtlinie „Sicherheitszonen: Nur Computereinstellungen verwenden“.
    
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone protected mode** (Popupblocker in der eingeschränkten Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie den geschützten Modus aktivieren. Im geschützten Modus wird Internet Explorer vor der Ausnutzung von Schwachstellen geschützt. Hierbei wird die Anzahl der Speicherorte in der Registrierung und im Dateisystem verringert, in die Internet Explorer schreiben kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der geschützte Modus aktiviert. Benutzer können den geschützten Modus nicht deaktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der geschützte Modus deaktiviert. Benutzer können den geschützten Modus nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer den geschützten Modus aktivieren oder deaktivieren.
  
  **Standard**: Aktivieren  
  
- **Internet Explorer internet zone user data persistence** (Speichern von Benutzerdaten in der Internetzone von Internet Explorer)  
  Über diese Richtlinieneinstellung können Sie die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite regeln. Wenn ein Benutzer eine gespeicherte Seite erneut besucht, kann der Zustand der Seite wiederhergestellt werden, wenn Sie diese Richtlinieneinstellung entsprechend konfiguriert haben. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite aktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite aktivieren.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone scripting of web browser controls** (Anwenden von Skripts auf WebBrowser-Steuerelemente in der Internetzone von Internet Explorer)  
 
  Diese Richtlinieneinstellung bestimmt, ob eine Seite eingebettete WebBrowser-Steuerelemente per Skript steuern kann. Wenn Sie diese Richtlinieneinstellung aktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement möglich. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement nicht möglich. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer den Skriptzugriff auf das WebBrowser-Steuerelement aktivieren oder deaktivieren. Standardmäßig ist der Skriptzugriff auf das WebBrowser-Steuerelement nur auf dem lokalen Computer und in Intranetzonen möglich.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone user data persistence** (Speichern von Benutzerdaten in der eingeschränkten Zone von Internet Explorer)  
    Über diese Richtlinieneinstellung können Sie die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite regeln. Wenn ein Benutzer eine gespeicherte Seite erneut besucht, kann der Zustand der Seite wiederhergestellt werden, wenn Sie diese Richtlinieneinstellung entsprechend konfiguriert haben. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite aktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite nicht aktivieren.  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer locked down intranet zone java permissions** (Java-Berechtigungen für die gesperrte Intranetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.
  
  **Standard**: Java deaktivieren  
  
- **Internet Explorer enhanced protected mode** (Erweiterter geschützter Modus in Internet Explorer)  
  Der erweiterte geschützte Modus bietet einen zusätzlichen Schutz gegen Websites mit Schadsoftware, indem er bei 64-Bit-Versionen von Windows 64-Bit-Prozesse verwendet. Bei Computern mit Windows 8 oder höher beschränkt der erweiterte geschützte Modus außerdem die Speicherorte von Internet Explorer in der Registrierung und im Dateisystem. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der erweiterte geschützte Modus aktiviert. In allen Zonen mit aktiviertem geschützten Modus wird der erweiterte geschützte Modus verwendet. Die Benutzer können den erweiterten geschützten Modus nicht deaktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der erweiterte geschützte Modus deaktiviert. In allen Zonen mit aktiviertem geschützten Modus wird die Version des geschützten Modus verwendet, die mit Internet Explorer 7 für Windows Vista eingeführt wurde. Wenn Sie diese Richtlinie nicht konfigurieren, können die Benutzer den erweiterten geschützten Modus über die Registerkarte „Erweitert“ im Dialogfeld „Internetoptionen“ ein oder ausschalten.
  
  **Standard**: Aktiviert  
  
- **Internet Explorer bypass smart screen warnings** (SmartScreen-Warnungen in Internet Explorer umgehen)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer Warnungen des SmartScreen-Filters umgehen können. Der SmartScreen-Filter warnt Benutzer vor ausführbaren Dateien im Internet, die selten von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung aktivieren, hindern die Warnungen des SmartScreen-Filters Benutzer am Herunterladen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Warnungen des SmartScreen-Filters umgehen.
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone meta refresh** (Meta Refresh-Tag in einer eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzerbrowser auf eine andere Webseite umgeleitet werden können, wenn der Autor der Webseite die Einstellung „Meta Refresh“ (Tag) verwendet, um Browser auf eine andere Webseite umzuleiten. Wenn Sie diese Richtlinieneinstellung aktivieren, können Browser, die eine Seite mit einer aktiven Meta Refresh-Einstellung laden, auf andere Webseiten umgeleitet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Browser, die eine Seite mit einer aktiven Meta Refresh-Einstellung laden, nicht auf andere Webseiten umgeleitet werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Browser, die eine Seite mit einer aktiven Meta Refresh-Einstellung laden, nicht auf andere Webseiten umgeleitet werden.
  
  **Standard**: Deaktiviert  
  
### <a name="local-policies-security-options"></a>Sicherheitsoptionen für lokale Richtlinien
Weitere Informationen finden Sie unter [Policy CSP – LocalPoliciesSecurityOptions (Richtlinien-Konfigurationsdienstanbieter: LocalPoliciesSecurityOptions)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in der Windows-Dokumentation. 

- **Restrict anonymous access to named pipes and shares** (Anonymen Zugriff auf Named Pipes und Freigaben einschränken)  
  Wenn diese Sicherheitseinstellung aktiviert ist, wird der anonyme Zugriff auf Freigaben und Pipes für folgende Einstellungen eingeschränkt: (1) Named Pipes, auf die anonym zugegriffen werden kann; (2) Freigaben, auf die anonym zugegriffen werden kann
  
  **Standard**: Ja  
  
- **Minimum session security for NTLM SSP based servers** (Minimale Sitzungssicherheit für NTLM-basierte SSP-Server)  
  Mit dieser Sicherheitseinstellung kann die Aushandlung der 128-Bit-Verschlüsselung und bzw. oder der NTLMv2-Sitzungssicherheit für einen Server als erforderlich festgelegt werden. Diese Werte hängen vom Wert des Sicherheitseinstellungswerts für die LAN Manager-Authentifizierungsebene ab. Die Optionen sind: „NTLMv2-Sitzungssicherheit erfordern: Die Verbindung schlägt fehl, wenn die Nachrichtenintegrität nicht ausgehandelt wird“. 128-Bit-Verschlüsselung erfordern: Die Verbindung schlägt fehl, wenn die keine starke Verschlüsselung (128-Bit) ausgehandelt wird.
  
  **Standard**: NTLMv2- und 128-Bit-Verschlüsselung verlangen  
  
- **Minutes of lock screen inactivity until screen saver activates** (Inaktivität in Minuten für Anmeldebildschirm bis zur Aktivierung des Bildschirmschoners)  
  Windows bemerkt die Inaktivität einer Anmeldesitzung, führt den Bildschirmschoner aus und sperrt die Sitzung, wenn der Zeitraum der Inaktivität die jeweilige Obergrenze überschreitet.
  
  **Standard**: 15
  
- **Require client to always digitally sign communications** (Digitale Signierung der Kommunikation immer vom Client erfordern) Diese Sicherheitseinstellung bestimmt, ob von Domänenmitgliedern gestarteter Datenverkehr über den sicheren Kanal signiert oder verschlüsselt sein muss. Wenn ein Computer einer Domäne beitritt, wird ein Computerkonto erstellt. Daraufhin wird das Kennwort des Computerkontos beim Starten des Systems zum Erstellen eines sicheren Kanals mit einem Domänencontroller als Domäne verwendet. Dieser sichere Kanal wird verwendet, um Vorgänge wie die NTLM-Pass-Through-Authentifizierung, LSA SID/Namenlookups usw. durchzuführen. Diese Einstellung bestimmt, ob jeglicher Datenverkehr über den sicheren Kanal, der von Domänenmitgliedern gestartet wird, den Mindestanforderungen für die Sicherheit entspricht. Insbesondere bestimmt sie, ob von Domänenmitgliedern gestarteter Datenverkehr über den sicheren Kanal signiert oder verschlüsselt sein muss. Wenn diese Richtlinie aktiviert ist, wird der sichere Kanal nicht erstellt, es sei denn, die Signierung oder Verschlüsselung des gesamten Datenverkehrs über den sicheren Kanal wird ausgehandelt. Wenn diese Richtlinie deaktiviert ist, wird die Verschlüsselung und Signierung des gesamten Datenverkehrs über den sicheren Kanal mit dem Domänencontroller ausgehandelt. In diesem Fall sind die Signierung und Verschlüsselung von der Version des Domänencontrollers und den Einstellungen der beiden folgenden Richtlinien abhängig: „Domänenmitglied: Daten des sicheren Kanals digital verschlüsseln (wenn möglich)“; „Domänenmitglied: Daten des sicheren Kanals digital signieren (wenn möglich)“
  
  **Standard**: Ja
  
- **Authentifizierungsebene**  
  Mit dieser Sicherheitseinstellung wird festgelegt, welches Abfrage/Antwort-Authentifizierungsprotokoll für Netzwerkanmeldungen verwendet wird. Diese Auswahl wirkt sich wie folgt auf das von Clients verwendete Authentifizierungsprotokoll, die ausgehandelte Sitzungssicherheit und die von Servern akzeptierte Authentifizierung aus:  
  - *LM- und NTLM-Antworten senden*: Clients verwenden die NTLM-Authentifizierung und nie die NTLMv2-Sitzungssicherheit. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Send LM and NTLM - NTLMv2 if negotiated* (LM- und NTLM-Antworten senden – NTLMv2, wenn ausgehandelt): Clients verwenden die LM- und NTLM-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Nur NTLM-Antworten senden*: Clients verwenden ausschließlich die NTLM-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Nur NTLMv2-Antworten senden*: Clients verwenden ausschließlich die NTLMv2-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Nur NTLMv2-Antworten senden. LM ablehnen*: Clients verwenden ausschließlich die NTLMv2-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller lehnen die LM-Authentifizierung ab (sie akzeptieren nur die NTLM- und NTLMv2-Authentifizierungen). 
  - *Nur NTLMv2-Antworten senden. LM und NTLM ablehnen*: Clients verwenden ausschließlich die NTLMv2-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller lehnen die LM- und NTLM-Authentifizierung ab (sie akzeptieren nur die NTLMv2-Authentifizierung). 
    
  **Standard**: Nur NTLMv2-Antworten senden. LM und NTLM ablehnen.
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers** (Senden von unverschlüsselten Kennwörtern von Clients an SMB-Server von Drittanbietern verhindern)  
  Wenn diese Sicherheitseinstellung aktiviert ist, darf der SMB-Redirector (Server Message Block) Klartextkennwörter an Nicht-Microsoft-SMB-Server senden, die keine Kennwortverschlüsselung während der Authentifizierung unterstützen. Das Senden unverschlüsselter Kennwörter ist ein Sicherheitsrisiko.
  
  **Standard**: Ja
  
- **Disable server digitally signing communications always** (Digitale Signierung durch Server für die Kommunikation immer deaktivieren)  
  Mit dieser Sicherheitseinstellung wird festgelegt, ob der SMB-Client versucht, die SMB-Paketsignierung auszuhandeln. Das SMB-Protokoll (Server Message Block) stellt die Grundlage für Microsoft-Dateien und die Druckfreigabe sowie viele andere Netzwerkvorgänge, z.B. die Windows-Remoteverwaltung. Das SMB-Protokoll unterstützt das digitale Signieren von SMB-Paketen, um Man-in-the-Middle-Angriffe zu vermeiden, die SMB-Pakete während der Übermittlung ändern. Mit dieser Richtlinieneinstellung wird festgelegt, ob die SMB-Clientkomponente versucht, die Signierung von SMB-Paketen auszuhandeln, wenn eine Verbindung mit einem SMB-Server hergestellt wird. Wenn diese Einstellung aktiviert wird, fordert der Microsoft-Netzwerkclient den Server dazu auf, die SMB-Paketsignatur bei der Einrichtung der Sitzung durchzuführen. Wenn die Paketsignatur auf dem Server aktiviert wurde, wird die Paketsignatur ausgehandelt. Wenn diese Richtlinie deaktiviert ist, handelt der SMB-Client nie die SMB-Paketsignatur aus.
  
  **Standard**: Ja
  
- **Administrator elevation prompt behavior** (Verhalten für Administratoren bei der Eingabeaufforderung für erhöhte Rechte)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Administratoren bestimmen. Folgende Optionen sind verfügbar: 
  - *Erhöhte Rechte ohne Eingabeaufforderung*: Ermöglicht mit Rechten versehenen Konten das Ausführen eines Vorgangs, für den erhöhte Rechte erforderlich sind, ohne dass dafür Zustimmung oder Anmeldeinformationen erforderlich sind. Hinweis: Verwenden Sie diese Option nur in Umgebungen, die besonders starken Beschränkungen unterliegen. 
  - *Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop zur Eingabe eines entsprechenden Benutzernamens und Kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt. 
  - *Eingabeaufforderung zur Zustimmung auf dem sicheren Desktop*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop zur Auswahl von „Zulassen“ oder „Verweigern“ aufgefordert. Wenn der Benutzer „Zulassen“ auswählt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt. 
  - *Eingabeaufforderung zu Anmeldeinformationen*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer zur Eingabe eines Administratorbenutzernamens und -kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt. 
  - *Eingabeaufforderung zur Zustimmung*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wählen Sie entweder „Zulassen“ oder „Verweigern“ aus. Wenn der Benutzer „Zulassen“ auswählt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt.  
  - *Eingabeaufforderung zur Zustimmung für Nicht-Windows-Binärdateien*: Wenn für einen Vorgang für eine nicht von Microsoft stammende Anwendung erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop aufgefordert, entweder „Zulassen“ oder „Verweigern“ auszuwählen. Wenn der Benutzer „Zulassen“ auswählt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt.   
  
  **Standard**: Zustimmungsaufforderung für sicheren Desktop
  
- **Minimum session security for NTLM SSP based clients** (Minimale Sitzungssicherheit für NTLM-basierte SSP-Clients)  
  Mit dieser Sicherheitseinstellung kann die Aushandlung der 128-Bit-Verschlüsselung und bzw. oder der NTLMv2-Sitzungssicherheit für einen Client als erforderlich festgelegt werden. Diese Werte hängen vom Wert des Sicherheitseinstellungswerts für die LAN Manager-Authentifizierungsebene ab. Folgende Optionen sind verfügbar:
  - „NTLMv2-Sitzungssicherheit erfordern“: Die Verbindung schlägt fehl, wenn das NTLMv2-Protokoll nicht ausgehandelt wird. 
  - *128-Bit-Verschlüsselung erfordern*: Die Verbindung schlägt fehl, wenn keine starke Verschlüsselung (128-Bit) ausgehandelt wird.
  - *NTLMv2- und 128-Bit-Verschlüsselung erfordern*. 

  **Standard**: NTLMv2- und 128-Bit-Verschlüsselung erfordern
  
- **Smart card removal behavior** (Verhalten beim Entfernen von Smartcards)  
  Diese Sicherheitseinstellung legt fest, was geschieht, wenn die Smartcard für einen angemeldeten Benutzer aus dem Smartcardleser entfernt wird. Folgende Optionen sind verfügbar:
  - *Keine Aktion*. 
  - *Arbeitsstation sperren* – Die Arbeitsstation wird beim Entfernen der Smartcard gesperrt, sodass Benutzer den Arbeitsbereich verlassen, die Smartcard mitnehmen und dennoch eine geschützte Sitzung aufrechterhalten können.
  - *Abmeldung erzwingen*: Der Benutzer wird automatisch abgemeldet, wenn die Smartcard entfernt wird.
  - *Disconnect Remote Desktop session* (Remotedesktopsitzung beenden): Das Entfernen der Smartcard beendet die Sitzung, ohne den Benutzer abzumelden. Dies ermöglicht es Benutzern, die Smartcard einzulegen und die Sitzung später oder auf einem anderen Computer mit Smartcard-Leser fortzusetzen, ohne sich erneut anmelden zu müssen. Wenn die Sitzung lokal stattfindet, funktioniert diese Richtlinie genau wie „Arbeitsstation sperren“.  <br><br>

  **Standard**: Arbeitsstation sperren
  
- **Block anonymous enumeration of SAM accounts and shares** (Anonyme Aufzählung von SAM-Konten und Freigaben blockieren)  
  Diese Sicherheitseinstellung legt fest, ob die anonyme Aufzählung von SAM-Konten und Freigaben zugelassen wird. Windows erlaubt anonymen Benutzern bestimmte Aktionen, z.B. das Aufzählen der Namen von Domänenkonten und Netzwerkfreigaben. Das kann z. B. besonders nützlich sein, wenn ein Administrator Benutzern in einer vertrauenswürdigen Domäne Zugriffsberechtigungen gewähren möchte, die diese Vertrauensstellung nicht erwidert. Wenn Sie die anonyme Aufzählung von SAM-Konten und Freigaben nicht zulassen möchten, legen Sie für diese Richtlinie *Ja* fest.
  
  **Standard**: Ja
  
- **Block remote logon with blank password** (Remoteanmeldung mit leerem Kennwort blockieren)  
  Diese Sicherheitseinstellung legt fest, ob lokale Konten, die nicht kennwortgeschützt sind, zum Anmelden an anderen Orten als der Konsole des physischen Computers verwendet werden können. Wenn diese Einstellung aktiviert ist, können lokale Konten ohne Kennwortschutz nur über die Computertastatur angemeldet werden. 

  *Warnung*: Für Computer, die sich nicht an physisch sicheren Orten befinden, sollten immer strikte Kennwortrichtlinien für alle Benutzerkonten verwendet werden. Ansonsten kann sich jeder mit physischem Zugang zu dem Computer mit einem Benutzerkonto ohne Kennwort anmelden. Dies gilt besonders für tragbare Computer. 

  Wenn Sie diese Sicherheitsrichtlinie auf die Gruppe „Alle“ anwenden, kann sich niemand über Remotedesktopdienste anmelden. Diese Einstellung wirkt sich nicht auf Anmeldungen mit Domänenkonten aus. Anwendungen mit interaktiven Remoteanmeldungen können diese Einstellung umgehen.
  
  **Standard**: Ja
  
- **Standard user elevation prompt behavior** (Verhalten für Standardbenutzer bei der Eingabeaufforderung für erhöhte Rechte)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Standardbenutzer bestimmen. 
  - *Anforderungen für erhöhte Rechte automatisch ablehnen*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird eine konfigurierbare Fehlermeldung für verweigerten Zugriff angezeigt. Ein Unternehmen, in dem Desktops mit Standardbenutzerrechten ausgeführt werden, kann diese Einstellung auswählen, um die Anzahl der Anrufe beim Helpdesk zu verringern. 
  - *Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop zur Eingabe eines anderen Benutzernamens und Kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt. 
  - *Eingabeaufforderung zu Anmeldeinformationen*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer zur Eingabe eines Administratorbenutzernamens und -kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt.  
  
  **Standard**: Anforderungen für erhöhte Rechte automatisch ablehnen
  
- **Require admin approval mode for administrators** (Administratorgenehmigungsmodus für Administratoren erfordern)  
  Mit dieser Richtlinieneinstellung wird das Verhalten aller UAC-Richtlinieneinstellungen (User Account Control, Benutzerkontensteuerung) für den Computer bestimmt. Wenn Sie diese Richtlinieneinstellung ändern, muss der Computer neu gestartet werden. Folgende Optionen sind verfügbar:   
  - *Nicht konfiguriert*: Der Administratorgenehmigungsmodus und alle verwandten UAC-Richtlinieneinstellungen sind deaktiviert. Hinweis: Wenn diese Richtlinieneinstellung deaktiviert ist, werden Sie vom Sicherheitscenter benachrichtigt, dass die allgemeine Sicherheit des Betriebssystems eingeschränkt ist. 
  - *Ja*: Der Administratorgenehmigungsmodus ist aktiviert. Diese Richtlinieneinstellung muss aktiviert und verwandte UAC-Richtlinieneinstellungen müssen entsprechend festgelegt werden, damit das integrierte Administratorkonto und alle anderen Benutzerkonten, die Mitglieder der Administratorgruppe sind, im Administratorgenehmigungsmodus ausgeführt werden können.  
  
  **Standard**: Ja
  
- **Prevent anonymous enumeration of SAM accounts** (Anonyme Enumerationen von SAM-Konten verhindern)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, welche zusätzlichen Berechtigungen für anonyme Verbindungen mit dem Computer gewährt werden. Windows erlaubt anonymen Benutzern bestimmte Aktionen, z.B. das Aufzählen der Namen von Domänenkonten und Netzwerkfreigaben. Das kann z. B. besonders nützlich sein, wenn ein Administrator Benutzern in einer vertrauenswürdigen Domäne Zugriffsberechtigungen gewähren möchte, die diese Vertrauensstellung nicht erwidert. Mit dieser Sicherheitseinstellung können die folgenden zusätzlichen Einschränkungen für anonyme Verbindungen vorgenommen werden: 
  - *Ja*: Enumeration von SAM-Konten nicht zulassen. Diese Option ersetzt die Option „Everyone with Authenticated Users“ (Jeder mit authentifizierten Benutzern) in den Sicherheitsberechtigungen für Ressourcen.
  - *Nicht konfiguriert*: Keine zusätzlichen Einschränkungen. Es gelten die Standardberechtigungen.  
  
  **Standard**: Ja
  
- **Allow remote calls to security accounts manager** (Remoteaufrufe vom Sicherheitskonto-Manager zulassen)  
  Mit dieser Richtlinieneinstellung können Sie RPC-Verbindungen mit dem SAM einschränken. Wenn diese Einstellung nicht festgelegt wurde, wird die Standardsicherheitsbeschreibung verwendet.
  
  **Standard**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode** (Administratorgenehmigungsmodus verwenden)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten des Administratorgenehmigungsmodus für das integriertes Administratorkonto bestimmen. Folgende Optionen sind verfügbar: 
  - *Ja*: Für das integrierte Administratorkonto wird der Administratorgenehmigungsmodus verwendet. Standardmäßig wird der Benutzer bei jedem Vorgang, der die Höherstufung von Rechten erfordert, zur Genehmigung aufgefordert. 
  - *Nicht konfiguriert*: Mit dem integrierten Administratorkonto werden alle Anwendungen mit vollständigen Administratorrechten ausgeführt.  

  **Standard**: Ja
  
- **Allow UI access applications for secure locations** (Anwendungen für Benutzeroberflächenbedienungshilfe für sichere Standorte zulassen)  
  Mit dieser Sicherheitseinstellung können Sie bestimmen, ob Programme für Bedienungshilfen für die Benutzeroberfläche (UIAccess oder UIA) automatisch den sicheren Desktop für Eingabeaufforderungen mit erhöhten Rechten eines Standardbenutzers deaktivieren kann. 
  - *Ja*: UIA-Programme, darunter Windows-Remoteunterstützung, deaktivieren automatisch den sicheren Desktop für Eingabeaufforderungen für erhöhte Rechte. Wenn die Richtlinieneinstellung „Benutzerkontensteuerung: Bei Benutzeraufforderung nach erhöhten Rechten zum sicheren Desktop wechseln“ nicht deaktiviert wird, werden die Eingabeaufforderungen auf dem Desktop des interaktiven Benutzers und nicht auf dem sicheren Desktop angezeigt. 
  - *Nicht konfiguriert*: Der sichere Desktop kann nur vom Benutzer des interaktiven Desktops oder durch Deaktivieren der Richtlinieneinstellung „Benutzerkontensteuerung: Bei Benutzeraufforderung nach erhöhten Rechten zum sicheren Desktop wechseln“ deaktiviert werden.  

  **Standard**: Ja

- **Detect application installations and prompt for elevation** (Anwendungsinstallationen erkennen und erhöhte Rechte anfordern)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten bei der Erkennung einer Anwendungsinstallation auf dem Computer bestimmen. Folgende Optionen sind verfügbar: 
  - *Aktiviert*: Wenn ein Anwendungsinstallationspaket erkannt wird, das erhöhte Rechte erfordert, wird der Benutzer zur Eingabe eines Administratorbenutzernamens und -kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt. 
  - *Deaktiviert*: Anwendungsinstallationspakete werden nicht erkannt, und es wird keine Eingabeaufforderung für erhöhte Rechte angezeigt. Unternehmen, die Standardbenutzerdesktops und delegierte Installationstechnologien wie Gruppenrichtlinien-Softwareinstallation oder Systems Management Server (SMS) verwenden, sollten diese Richtlinieneinstellung deaktivieren. In diesem Fall ist keine Installationserkennung erforderlich.  
  
  **Standard**: Ja
  
- **Prevent storing LAN manager hash value on next password change** (Speicher des Hashwerts des LAN-Managers bei der nächsten Kennwortänderung verhindern)  
  Mit dieser Sicherheitseinstellung können Sie bestimmen, ob der Hashwert des LAN-Managers (LM) bei der nächsten Kennwortänderung für das neue Kennwort gespeichert werden soll. Der LM-Hashwert ist im Vergleich zum kryptografisch stärkeren Windows NT-Hashwert relativ schwach und angreifbar. Da der LM-Hashwert auf dem lokalen Computer in der Sicherheitsdatenbank gespeichert wird, können die Kennwörter gefährdet sein, wenn die Sicherheitsdatenbank angegriffen wird.
  
  **Standard**: Ja

- **Virtualize file and registry write failures to per user locations** (Fehler bei Schreibvorgängen für Dateien und Registrierung pro Benutzer virtualisieren)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Fehler bei Anwendungsschreibvorgängen an definierte Registrierungs- und Dateisystemspeicherorte weitergeleitet werden. Mit dieser Richtlinieneinstellung werden Anwendungen, die mit Administratorrechten ausgeführt werden und die Laufzeitanwendungsdaten schreiben, zum folgenden Verzeichnis migriert: *%Programme%* , *%Windir%* , *%Windir%\system32* oder *HKLM\Software*.
  
  **Standard**: Ja

### <a name="ms-security-guide"></a>MSSecurityGuide  

Weitere Informationen finden Sie unter [Policy CSP - MSSecurityGuide (Richtlinien-CSP: MSSecurityGuide)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in der Windows-Dokumentation.  

- **Apply UAC restrictions to local accounts on network logon** (UAC-Einschränkungen auf lokale Konten bei der Netzwerkanmeldung anwenden)  
  **Standard**: Aktiviert
  
- **SMB v1 client driver start configuration** (Startkonfiguration den SMB v1-Clienttreibers)  
  **Standard**: Treiber deaktiviert
  
- **SMB v1 server** (SMB v1-Server)  
  **Standard**: Deaktiviert
  
- **Digest authentication** (Digestauthentifizierung)  
  **Standard**: Deaktiviert
  
- **Structured exception handling overwrite protection** (Überschreibungsschutz bei der Behandlung strukturierter Ausnahmen)  
  **Standard**: Aktiviert
  
### <a name="mss-legacy"></a>MSS Legacy  

Weitere Informationen finden Sie unter [Policy CSP - MSSLegacy (Richtlinen-CSP: MSSLegacy)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in der Windows-Dokumentation.  

- **Network IP source routing protection level** (Schutzebene für das Quellrouting von Netzwerk-IP-Adressen)  
  **Standard**: Höchster Schutz  
  
- **Network ignore NetBIOS name release requests except from WINS servers** (Das Netzwerk ignoriert Namensanforderungen von NetBIOS, es sei denn, sie stammen von WINS-Servern)  
  **Standard**: Aktiviert
  
- **Network IPv6 source routing protection level** (Schutzebene für das Quellrouting von Netzwerk-IPv6-Adressen)  
  **Standard**: Höchster Schutz

- **Network ICMP redirects to override OSPF generated routes** (Umleitungen durch das Netzwerk-ICMP zum Überschreiben von Routen, die vom OSPF generiert wurden)  
  **Standard**: Deaktiviert
  
### <a name="power"></a>Power  

Weitere Informationen finden Sie unter [Policy CSP - Power (Richtlinien-CSP: Power)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in der Windows-Dokumentation.  

- **Require password on wake while plugged in** (Kennwort bei Reaktivierung im Netzbetrieb anfordern)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Benutzer zur Eingabe eines Kennworts aufgefordert wird, wenn das System aus dem Energiesparmodus reaktiviert wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, wird der Benutzer beim Verlassen des Energiesparmodus zur Eingabe eines Kennworts aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der Benutzer beim Verlassen des Energiesparmodus nicht zur Eingabe eines Kennworts aufgefordert.
  
  **Standard**: Aktiviert
  
- **Standby states when sleeping while on battery** (Standbyzustände im Energiesparmodus im Akkubetrieb)  
  Diese Richtlinieneinstellung legt fest, ob Windows Standbyzustände verwenden kann, wenn der Computer in den Energiesparmodus versetzt wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, verwendet Windows Standbyzustände, um den Computer in den Energiesparmodus zu versetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren, sind Standbyzustände (S1–S3) nicht zulässig.
  
  **Standard**: Deaktiviert
  
- **Standby states when sleeping while plugged in** (Standbyzustände im Energiesparmodus im Netzbetrieb)  
  Diese Richtlinieneinstellung legt fest, ob Windows Standbyzustände verwenden kann, wenn der Computer in den Energiesparmodus versetzt wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, verwendet Windows Standbyzustände, um den Computer in den Energiesparmodus zu versetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren, sind Standbyzustände (S1–S3) nicht zulässig.
  
  **Standard**: Deaktiviert
  
- **Require password on wake while on battery** (Kennwort bei Reaktivierung im Akkubetrieb anfordern)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Benutzer zur Eingabe eines Kennworts aufgefordert wird, wenn das System aus dem Energiesparmodus reaktiviert wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, wird der Benutzer beim Verlassen des Energiesparmodus zur Eingabe eines Kennworts aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der Benutzer beim Verlassen des Energiesparmodus nicht zur Eingabe eines Kennworts aufgefordert.
  
  **Standard**: Aktiviert
  
### <a name="remote-desktop-services"></a>Remotedesktopdienste  

Weitere Informationen finden Sie unter [Policy CSP – RemoteDesktopServices (Richtlinien-Konfigurationsdienstanbieter: RemoteDesktopServices)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in der Windows-Dokumentation.  

- **Block password saving** (Speichern von Kennwörtern blockieren)  
  Diese Richtlinieneinstellung steuert, ob Kennwörter auf diesem Computer über die Remotedesktopverbindung gespeichert werden können. Wenn Sie diese Einstellung aktivieren, wird das Kontrollkästchen für die Kennwortspeicherung in der Remotedesktopverbindung deaktiviert, und Benutzer können Kennwörter nicht mehr speichern. Wenn ein Benutzer eine RDP-Datei über die Remotedesktopverbindung öffnet und seine Einstellungen speichert, werden alle zuvor in der RDP-Datei vorhandenen Kennwörter gelöscht. Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, kann der Benutzer Kennwörter über die Remotedesktopverbindung speichern.
  
   **Standard**: Aktiviert
  
- **Secure RPC communication** (RPC-Kommunikation sichern)  
  Diese Richtlinieneinstellung legt fest, ob für einen Remotedesktopsitzungs-Hostserver die sichere RPC-Kommunikation mit allen Clients erforderlich bzw. ob die unsichere Kommunikation zulässig ist. Mit dieser Einstellung können Sie die Sicherheit der RPC-Kommunikation mit Clients verbessern, indem Sie nur authentifizierte und verschlüsselte Anforderungen zulassen. Wenn die Einstellung aktiviert ist, akzeptieren Remotedesktopdienste Anforderungen von RPC-Clients, die sichere Anforderungen unterstützen, und unterstützen keine unsichere Kommunikation mit nicht vertrauenswürdigen Clients. Wenn die Einstellung deaktiviert ist, muss der gesamte RPC-Datenverkehr für Remotedesktopdienste immer sicher sein. Für RPC-Clients, die nicht auf die Anforderung reagieren, ist jedoch eine unsichere Kommunikation zulässig. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, ist die unsichere Kommunikation zulässig. Hinweis: Die RPC-Schnittstelle wird zum Verwalten und Konfigurieren der Remotedesktopdienste verwendet.
  
  **Standard**: Aktiviert
  
- **Block drive redirection** (Laufwerkumleitung blockieren)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob die Zuordnung von Clientlaufwerken während einer Remotedesktopdienst-Sitzung (Laufwerkumleitung) verhindert werden soll. Remotedesktopdienst-Hostserver ordnen Clientlaufwerke standardmäßig beim Herstellen der Verbindung automatisch zu. Zugeordnete Laufwerke werden in der Sitzungsordnerstruktur im Datei-Explorer oder unter Computer mit dem Format *\<Laufwerkbuchstabe>* auf *\<Computername>* angezeigt. Mit dieser Richtlinieneinstellung können Sie dieses Verhalten überschreiben. Wenn Sie diese Richtlinieneinstellung aktivieren, ist die Umleitung von Clientlaufwerken in Remotedesktopdienst-Sitzungen nicht zulässig, und die Zwischenablageumleitung beim Kopieren von Dateien ist auf Computern unter Windows Server 2003, Windows 8 und Windows XP nicht zulässig. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist die Umleitung von Clientlaufwerken immer zulässig. Außerdem ist die Zwischenablageumleitung beim Kopieren von Dateien immer zulässig, wenn die Zwischenablageumleitung zulässig ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die Umleitung von Clientlaufwerken und die Zwischenablageumleitung beim Kopieren von Dateien nicht auf Gruppenrichtlinienebene festgelegt.
  
  **Standard**: Aktiviert
  
- **Prompt for password upon connection** (Kennwort bei der Herstellung einer Verbindung anfordern)  
  Diese Richtlinieneinstellung legt fest, ob Remotedesktopdienste beim Herstellen einer Verbindung immer ein Kennwort vom Client anfordern. Mit dieser Einstellung können Sie erzwingen, dass Benutzer, die sich bei Remotedesktopdiensten anmelden, selbst dann zur Eingabe eines Kennworts aufgefordert werden, wenn sie das Kennwort bereits im Remotedesktopverbindungs-Client angegeben haben. Remotedesktopdienste lassen standardmäßig zu, dass Benutzer sich automatisch anmelden, indem sie ein Kennwort im Remotedesktopverbindungs-Client eingeben. Wenn Sie diese Richtlinieneinstellung aktivieren, können sich Benutzer nicht automatisch bei Remotedesktopdiensten anmelden, indem sie ihr Kennwort im Remotedesktopverbindungs-Client eingeben. Sie müssen bei der Anmeldung ein Kennwort eingeben. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer sich immer automatisch bei Remotedesktopdiensten anmelden, indem sie ihr Kennwort im Remotedesktopverbindungs-Client eingeben. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die automatische Anmeldung nicht auf Gruppenrichtlinienebene festgelegt. 
  
  **Standard**: Aktiviert
  
- **Remote desktop services client connection encryption level** (Verschlüsselungsstufe der Verbindung des Remotedesktopdienst-Clients)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob eine bestimmte Verschlüsselungsstufe zum Schutz der Kommunikation zwischen Clientcomputern und RD-Sitzungshostservern während RDP-Verbindungen (Remotedesktopprotokoll) erforderlich ist. Diese Richtlinie gilt nur, wenn Sie die native RDP-Verschlüsselung verwenden. Allerdings wird von der Verwendung der nativen RDP-Verschlüsselung (im Gegensatz zur SSL-Verschlüsselung) abgeraten. Diese Richtlinie gilt nicht für die SSL-Verschlüsselung. Wenn Sie diese Richtlinieneinstellung aktivieren, muss für die gesamte Kommunikation zwischen Clients und RD-Sitzungshostservern während Remoteverbindungen die in dieser Einstellung festgelegte Verschlüsselungsmethode verwendet werden. Die Verschlüsselungsstufe ist standardmäßig auf „Hoch“ festgelegt. Die folgenden Verschlüsselungsmethoden stehen zur Verfügung:  
  - *Hoch*: Mit der Einstellung „Hoch“ werden zwischen dem Client und dem Server gesendete Daten mit einer starken 128-Bit-Verschlüsselung verschlüsselt. Verwenden Sie diese Verschlüsselungsstufe in Umgebungen, die nur 128-Bit-Clients enthalten (z.B. Clients mit Remotedesktopverbindung). Clients, die diese Verschlüsselungsstufe nicht unterstützen, können keine Verbindung mit RD-Sitzungshostservern herstellen.  
  - *Clientkompatibel*: Mit der Einstellung „Clientkompatibel“ werden zwischen dem Client und dem Server gesendete Daten mit der vom Client unterstützten maximalen Schlüsselstärke verschlüsselt. Verwenden Sie diese Verschlüsselungsstufe für Umgebungen mit Clients, die keine 128-Bit-Verschlüsselung unterstützen.  
  - *Niedrig*: Mit der Einstellung „Niedrig“ werden nur vom Client an den Server gesendete Daten mithilfe der 56-Bit-Verschlüsselung verschlüsselt.  
  
  Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, wird die für Remoteverbindungen mit RD-Sitzungshostservern zu verwendende Verschlüsselungsstufe nicht über Gruppenrichtlinien erzwungen. Wichtig: die FIPS-Konformität (Federal Information Processing Standard) kann mithilfe der Systemkryptografie konfiguriert werden. Verwenden Sie FIPS-konforme Algorithmen für die Verschlüsselung, das Hashing und das Signieren von Einstellungen in der Gruppenrichtlinie (unter Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options). Mit der FIPS-konformen Einstellung werden Daten, die vom Client an den Server und vom Server an den Client gesendet werden, mit Verschlüsselungsalgorithmen gemäß FIPS 140 mithilfe von kryptografischen Modulen von Microsoft verschlüsselt und entschlüsselt. Verwenden Sie diese Verschlüsselungsstufe, wenn die Kommunikation zwischen Clients und RD-Sitzungshostservern die höchste Verschlüsselungsstufe erfordert.
  
  **Standard**: Hoch
  
### <a name="remote-management"></a>Remoteverwaltung  

Weitere Informationen finden Sie unter [Policy CSP – RemoteManagement (Richtlinien-Konfigurationsdienstanbieter: RemoteManagement)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in der Windows-Dokumentation.  

- **Block storing run as credentials** (Speichern von Anmeldeinformationen für „Ausführen als“ blockieren)  
  Standardclientauthentifizierung
  
  **Standard**: Aktiviert
  
- **Standardauthentifizierung**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Windows-Remoteverwaltungsdienst (Windows Remote Management, WinRM) die Standardauthentifizierung von einem Remoteclient akzeptiert. Wenn Sie diese Richtlinieneinstellung aktivieren, akzeptiert der WinRM-Dienst die Standardauthentifizierung von einem Remoteclient. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, akzeptiert der WinRM-Dienst keine Standardauthentifizierung von einem Remoteclient.
  
  **Standard**: Deaktiviert
  
- **Client unencrypted traffic** (Unverschlüsselter Clientdatenverkehr)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Windows-Remoteverwaltungsclient die Digestauthentifizierung verwendet. Wenn Sie diese Richtlinieneinstellung aktivieren, verwendet der WinRM-Client keine Digestauthentifizierung. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, verwendet der WinRM-Client die Digestauthentifizierung.
  
  **Standard**: Aktiviert
  
- **Unverschlüsselter Datenverkehr**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der WinRM-Dienst unverschlüsselte Nachrichten über das Netzwerk sendet und empfängt. Wenn Sie diese Richtlinieneinstellung aktivieren, sendet und empfängt der WinRM-Client unverschlüsselte Nachrichten über das Netzwerk. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, sendet und empfängt der WinRM-Client nur verschlüsselte Nachrichten über das Netzwerk.  
  
  **Standard**: Deaktiviert
  
- **Unverschlüsselter Clientdatenverkehr**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der WinRM-Client unverschlüsselte Nachrichten über das Netzwerk sendet und empfängt. Wenn Sie diese Richtlinieneinstellung aktivieren, sendet und empfängt der WinRM-Client unverschlüsselte Nachrichten über das Netzwerk. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, sendet und empfängt der WinRM-Client nur verschlüsselte Nachrichten über das Netzwerk.
  
  **Standard**: Deaktiviert
  
- **Standardclientauthentifizierung**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der WinRM-Client die Standardauthentifizierung verwendet. Wenn Sie diese Richtlinieneinstellung aktivieren, verwendet der WinRM-Client die Standardauthentifizierung. Wenn WinRM für die Verwendung des HTTP-Transports konfiguriert ist, werden der Benutzername und das Kennwort unverschlüsselt über das Netzwerk übertragen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, verwendet der WinRM-Client die Standardauthentifizierung nicht.
  
  **Standard**: Deaktiviert
  

### <a name="remote-procedure-call"></a>Remoteprozeduraufruf  

Weitere Informationen finden Sie unter [Policy CSP – RemoteProcedureCall (Richtlinien-Konfigurationsdienstanbieter: RemoteProcedureCall)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in der Windows-Dokumentation.  

- **RPC unauthenticated client options** (Nicht authentifizierte RPC-Clientoptionen)  
  Diese Richtlinieneinstellung steuert, wie die RPC-Server-Runtime nicht authentifizierte RPC-Clients behandelt, die sich mit RPC-Servern verbinden. Diese Richtlinieneinstellung betrifft alle RPC-Anwendungen. Verwenden Sie diese Richtlinieneinstellung in einer Domänenumgebung mit Vorsicht, da sie eine Vielzahl von Funktionen, darunter auch die Gruppenrichtlinienverarbeitung selbst, beeinträchtigen kann. Um nach einer Änderung die Richtlinieneinstellung wiederherzustellen, kann ein manueller Eingriff auf jedem betroffenen Computer erforderlich sein. Diese Richtlinieneinstellung sollte niemals auf einen Domänencontroller angewendet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, verwendet die RPC-Server-Runtime den Wert für „Authenticated“ (Authentifiziert) auf dem Windows-Client und den Wert für „None“ (Keine Authentifizierung) auf Windows-Server-Versionen, die diese Richtlinieneinstellung unterstützen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, bleibt sie deaktiviert. Die RPC-Server-Runtime verhält sich so, als wäre sie aktiviert mit dem für Windows-Clients verwendeten Wert für „Authenticated“ (Authentifiziert) und dem für Server-SKUs verwendeten Wert für „None“ (Keine Authentifizierung), die diese Richtlinieneinstellung unterstützen. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die RPC-Server-Runtime angewiesen, nicht authentifizierte RPC-Clients, die sich mit RPC-Servern verbinden, welche auf einem Computer ausgeführt werden, einzuschränken. Ein Client gilt als authentifizierter Client, wenn er für die Kommunikation mit dem Server eine benannte Pipe verwendet, oder wenn er RPC-Sicherheit verwendet. RPC-Schnittstellen, die speziell den Zugriff durch nicht authentifizierte Clients angefordert haben, können von dieser Einschränkung ausgenommen werden, abhängig von dem für diese Richtlinieneinstellung gewählten Wert.  
  - Durch *None* (Keine Authentifzierung) wird allen RPC-Clients gestattet, sich mit RPC-Servern zu verbinden, die auf dem Computer ausgeführt werden, auf den die Richtlinieneinstellung angewandt wird. 
  - Durch *Authenticated* (Authentifiziert) wird nur authentifizierten RPC-Clients (per oben stehender Definition) gestattet, sich mit RPC-Servern zu verbinden, die auf dem Computer ausgeführt werden, auf den die Richtlinieneinstellung angewandt wird. Ausnahmen werden für Schnittstellen gewährt, die solche angefordert haben. 
  - Durch *Authenticated without exceptions* (Authentifiziert ohne Ausnahmen) wird nur authentifizierten RPC-Clients (per oben stehender Definition) gestattet, sich mit RPC-Servern zu verbinden, die auf dem Computer ausgeführt werden, auf den die Richtlinieneinstellung angewandt wird. Ausnahmen sind nicht zulässig. Hinweis: Diese Richtlinieneinstellung wird erst angewendet, wenn das System neu gestartet wird.  

  **Standard**: Authentifiziert

### <a name="search"></a>Suchen  

Weitere Informationen finden Sie unter [Policy CSP - Search (Richtlinien-Konfigurationsdienstanbieter: Search)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in Ihrer Windows-Dokumentation.  

- **Indizierung verschlüsselter Elemente deaktivieren**  
  Hiermit wird die Indizierung von Elementen zugelassen oder verweigert. Diese Option ist für die Windows Search-Indexerstellung bestimmt und steuert, ob verschlüsselte Elemente wie beispielsweise WIP-geschützte Dateien (Windows Information Protection) indiziert werden. Wenn die Richtlinie aktiviert ist, werden WIP-geschützte Elemente indiziert und die zugehörigen Metadaten werden an einem nicht verschlüsselten Speicherort gespeichert. Die Metadaten umfassen beispielsweise den Dateipfad und das Änderungsdatum. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente nicht indiziert und sie werden nicht in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Ferner sind bei Fotos und Groove-Apps Leistungseinbußen möglich, wenn sich auf dem Gerät große Mengen an WIP-geschützten Mediendateien befinden.
  
**Standard**: Ja
  
### <a name="smart-screen"></a>SmartScreen  

Weitere Informationen finden Sie unter [Policy CSP - SmartScreen (Richtlinien-Konfigurationsdienstanbieter: SmartScreen)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in Ihrer Windows-Dokumentation.  

- **Ausführen nicht überprüfter Dateien blockieren**  
  Hindern Sie Benutzer am Ausführen von nicht überprüften Dateien. 
  - *Nicht konfiguriert*: Mitarbeiter können SmartScreen-Warnungen ignorieren und schädliche Dateien ausführen. 
  - *Ja*: Mitarbeiter können SmartScreen-Warnungen nicht ignorieren und keine schädlichen Dateien ausführen.

  **Standard**: Ja

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **SmartScreen für Apps und Dateien anfordern**  
  Ermöglicht IT-Administratoren das Konfigurieren von SmartScreen für Windows.

  **Standard**: Ja
  
### <a name="system"></a>System  

Weitere Informationen finden Sie unter [Policy CSP - System (Richtlinien-Konfigurationsdienstanbieter: System)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in Ihrer Windows-Dokumentation.  

- **Starttreiberinitialisierung für Systemstart**  
  Mit dieser Richtlinieneinstellung können Sie angeben, welche Bootstarttreiber initialisiert werden. Dies geschieht basierend auf einer durch den Bootstarttreiber für den Antischadsoftware-Frühstart festgelegten Klassifizierung. Der Bootstarttreiber für den Antischadsoftware-Frühstart kann die folgenden Klassifizierungen für die einzelnen Bootstarttreiber zurückgeben: 
  - *Gut*: Der Treiber wurde signiert und nicht manipuliert.  
  - *Schlecht:* Der Treiber wurde als Schadsoftware identifiziert. Wir empfehlen, die Initialisierung von bekannten schlechten Treibern nicht zuzulassen. 
  - *Schlecht, doch für den Bootvorgang erforderlich*: Der Treiber wurde als Schadsoftware identifiziert, doch der Computer kann nicht erfolgreich gestartet werden, ohne diesen Treiber zu laden. 
  - *Unbekannt*: Dieser Treiber wurde von Ihrer Anwendung zur Erkennung von Schadsoftware nicht bestätigt und vom Bootstarttreiber für den Antischadsoftware-Frühstart nicht klassifiziert.  

  Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie auswählen, welche Bootstarttreiber beim nächsten Start des Computers initialisiert werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden die guten, unbekannten oder schlechten, aber für den Bootvorgang erforderlichen Bootstarttreiber initialisiert. Die Initialisierung von schlechten Treibern wird übersprungen. Falls Ihre Anwendung für die Erkennung von Schadsoftware keinen Bootstarttreiber für den Antischadsoftware-Frühstart enthält oder dieser Treiber deaktiviert wurde, ist diese Richtlinieneinstellung wirkungslos, und alle Bootstarttreiber werden initialisiert.  
  
  **Standard**: Gut, unbekannt und schlecht, aber erforderlich


### <a name="wi-fi"></a>WLAN  

Weitere Informationen finden Sie unter [Policy CSP - Wifi (Richtlinien-Konfigurationsdienstanbieter: Wifi)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in Ihrer Windows-Dokumentation.  

- **Internetfreigabe blockieren**  
  Gibt an, ob die Internetfreigabe auf dem Gerät möglich ist.  

  **Standard**: Ja  

- **Automatisches Verbinden mit WLAN-Hotspots blockieren**  
  Gestattet oder verweigert das automatische Verbinden des Geräts mit WLAN-Hotspots.  

  **Standard**: Ja  
  
### <a name="windows-connection-manager"></a>Windows-Verbindungs-Manager  

Weitere Informationen finden Sie unter [Policy CSP - WindowsConnectionManager (Richtlinien-Konfigurationsdienstanbieter: WindowsConnectionManager)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in Ihrer Windows-Dokumentation.  

- **Verbindung zu Nicht-Domänennetzwerken blockieren**  
  Diese Richtlinieneinstellung verhindert, dass Computer gleichzeitig eine Verbindung zu einem domänenbasierten Netzwerk und zu einem nicht-domänenbasierten Netzwerk herstellen. Wenn diese Richtlinieneinstellung aktiviert ist, reagiert der Computer, abhängig von den folgenden Situationen, wie folgt auf automatische und manuelle Versuche, eine Netzwerkverbindung herzustellen: 
  - Automatische Verbindungsversuche: Wenn der Computer bereits mit einem domänenbasierten Netzwerk verbunden ist, werden alle automatischen Verbindungsversuche zu nicht-domänenbasierten Netzwerken blockiert. Wenn der Computer bereits mit einem nicht-domänenbasierten Netzwerk verbunden ist, werden automatische Verbindungsversuche zu domänenbasierten Netzwerken blockiert. 
  - Manuelle Verbindungsversuche: Wenn der Computer bereits mit einem nicht-domänenbasierten Netzwerk oder einem domänenbasierten Netzwerk über andere Medien als Ethernet verbunden ist, und ein Benutzer versucht, entgegen dieser Richtlinieneinstellung eine manuelle Verbindung zu einem zusätzlichen Netzwerk herzustellen, wird die bestehende Netzwerkverbindung abgebrochen und die manuelle Verbindung gestattet. Wenn der Computer bereits mit einem nicht-domänenbasierten Netzwerk oder einem domänenbasierten Netzwerk über Ethernet verbunden ist, und ein Benutzer versucht, entgegen dieser Richtlinieneinstellung eine manuelle Verbindung zu einem zusätzlichen Netzwerk herzustellen, wird die bestehende Ethernet-Verbindung gehalten und der manuelle Verbindungsversuch wird blockiert.  

  Wenn diese Richtlinieneinstellung nicht konfiguriert oder deaktiviert wird, ist es zulässig, dass Computer gleichzeitig eine Verbindung mit einem Domänen- und einem Nicht-Domänennetzwerk herstellen.  

  **Standard**: Aktiviert
  
### <a name="windows-defender"></a>Windows Defender  

Weitere Informationen finden Sie unter [Policy CSP - Defender (Richtlinien-Konfigurationsdienstanbieter: Defender)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in Ihrer Windows-Dokumentation.  

- **Eingehende E-Mail überprüfen**  
  Gestattet oder verweigert das Überprüfen von E-Mails.
  
  **Standard**: Ja  

- **Office apps launch child process type** (Untergeordnete Prozesse in Office-Apps starten)  
  Das Erstellen von untergeordneten Prozessen mit Office-Apps ist nicht gestattet. Dazu zählen Microsoft Word, Excel, PowerPoint, OneNote und Access. Dies ist ein typisches Verhalten für eine Schadsoftware, besonders für makrobasierte Angriffe, mit denen versucht wird, Office-Apps zum Starten oder Herunterladen ausführbarer schädlicher Dateien zu verwenden.
  
  **Standard**: Blockieren
  
- **Defender sample submission consent type** (Zustimmungstyp für die Übermittlung von Beispielen in Windows Defender)  
  Diese Einstellung sucht nach der Benutzerzustimmungsebene in Windows Defender, um Daten zu senden. Wenn die erforderliche Zustimmung bereits erteilt wurde, sendet Windows Defender die Daten. Wenn nicht (und wenn der Benutzer angegeben hat, nie zu fragen), wird die Benutzeroberfläche gestartet, um nach der Benutzerzustimmung zu fragen (wenn Defender/AllowCloudProtection gestattet ist), bevor Daten gesendet werden.
  
  **Standard**: Sichere Beispiele automatisch senden 
  
- **Signature update interval (in hours)** (Intervall für das Aktualisieren von Signaturen (in Stunden))  
  Intervall zum Aktualisieren von Signaturen in Windows Defender in Stunden
  
  **Standard**: 4
  
- **Ausführungstyp für heruntergeladene Nutzlast für Skript**  
  Ausführungstyp für heruntergeladene Nutzlast für Skript in Defender
  
  **Standard**: Blockieren
  
- **Diebstahl von Anmeldeinformationen verhindern**  
  Windows Defender Credential Guard nutzt auf Virtualisierung basierende Sicherheitsverfahren, um geheime Daten zu isolieren, damit nur durch privilegierte Systemsoftware auf diese Daten zugegriffen werden kann. Ein nicht autorisierter Zugriff auf diese geheimen Daten kann Angriffe zum Diebstahl von Anmeldeinformationen zur Folge haben (z. B. Pass-the-Hash- oder Pass-the-Ticket-Angriffe). Windows Defender Credential Guard verhindert diese Angriffe durch den Schutz von NTLM-Kennworthashes, Kerberos Ticket-Granting Tickets und Anmeldeinformationen, die von Anwendungen als Domänenanmeldeinformationen gespeichert werden.
  
  **Standard**: Aktivieren

- **Ausführungstyp für E-Mail-Inhalt**  
  Diese Regel verhindert die Ausführung oder das Starten der folgenden Dateitypen aus einer E-Mail, die in Microsoft Outlook oder einem webbasierten E-Mail-Dienst (z.B. Gmail.com oder Outlook.com) angezeigt wird: ausführbare Dateien (z.B. EXE, DLL oder SCR), Skriptdateien (z.B. PS PowerShell, VBS VisualBasic oder JS JavaScript) und Skriptarchivdateien.
  
  **Standard**: Blockieren
  
- **Netzwerkschutztyp**  
  Mit dieser Richtlinieneinstellung können Sie Netzwerkschutz in Windows Defender Exploit Guard aktivieren (blockieren/überwachen) oder deaktivieren. Netzwerkschutz ist ein Feature von Windows Defender Exploit Guard, das Arbeitnehmer davor schützt, eine Anwendung im Zuge betrügerischer Phishing-Versuche mit Zugriffsabsicht, Hostseiten für Exploits und schädliche Inhalte im Internet zu verwenden. Dabei wird auch verhindert, dass Browser von Drittanbietern Verbindungen zu gefährlichen Websites herstellen. Der Werttyp ist Integer. Wenn Sie diese Einstellung aktivieren, wird der Netzwerkschutz aktiviert, und Arbeitnehmer können ihn nicht mehr deaktivieren. Sein Verhalten kann mit den folgenden Optionen gesteuert werden: „Blockieren“ und „Überwachen“. Wenn Sie diese Richtlinie mit der Option „Blockieren“ aktivieren, können Benutzer und Anwendungen keine Verbindungen zu gefährlichen Domänen herstellen. Diese Aktivität wird im Windows Defender Security Center angezeigt. Wenn Sie diese Richtlinie mit der Option „Überwachen“ aktivieren, können Benutzer/Anwendungen Verbindungen zu gefährlichen Domänen herstellen. Diese Aktivität wird jedoch trotzdem im Windows Defender Security Center angezeigt. Wenn Sie diese Richtlinie deaktivieren, können Benutzer/Anwendungen Verbindungen zu gefährlichen Domänen herstellen. Im Windows Defender Security Center werden keine Netzwerkaktivitäten angezeigt. Wenn Sie diese Richtlinie nicht konfigurieren, wird die Blockierung des Netzwerks standardmäßig deaktiviert.
  
  **Standard**: Aktivieren
  
- **Defender-Überprüfungstag planen**  
  Defender-Überprüfungstag planen.
  
  **Standard**: Täglich
  
- **Schutz über die Cloud**  
  Um Ihren PC bestmöglich zu schützen, sendet Windows Defender zu jedem entdeckten Problem Informationen an Microsoft. Microsoft analysiert diese Informationen, erfährt mehr über die Probleme, die Sie und andere Kunden betreffen, und bietet verbesserte Lösungen an.
  
  **Standard**: Ja  

- **Potenziell unerwünschte App-Aktion in Defender**  
  Die PUA-Schutzfunktion (für potenziell unerwünschte Anwendungen) in Windows Defender Antivirus kann PUAs identifizieren und sie daran hindern, Endpunkte herunterzuladen und in ihrem Netzwerk zu installieren. Bei diesen Anwendungen handelt es sich nicht um Viren, Schadsoftware oder andere Arten von Bedrohungen. Diese Anwendungen können Aktionen auf Endpunkten ausführen, die deren Leistung oder Verwendung beeinträchtigen. Mit PUAs können auch Anwendungen gemeint sein, die einen schlechten Ruf haben. Typisches PUA-Verhalten umfasst: Verschiedene Arten von Softwarebündelungen; Einschleusung von Werbung in Webbrowser; Treiber- und Registrierungsoptimierungen, die Probleme erkennen, eine Zahlung zur Fehlerbehebung anfordern, aber auf dem Endpunkt verbleiben und weder Änderungen noch Optimierungen vornehmen (auch bekannt als „Rogue-Sicherheitssoftware“). Diese Anwendungen können das Risiko einer Infektion mit Schadsoftware für Ihr Netzwerk erhöhen, das Identifizieren von Infektionen erschweren und unnötig IT-Ressourcen zum Bereinigen der Anwendungen belegen.  
  
  **Standard**: Blockieren  

- **Verborgener Makrocodetyp von Skripten**  
  Schadsoftware und andere Bedrohungen versuchen möglicherweise ihren schädlichen Code in einigen Skriptdateien zu verbergen oder auszublenden. Mit dieser Regel wird verhindert, dass verborgen scheinende Skripts ausgeführt werden.
  
  **Standard**: Blockieren
  
- **Bei einer vollständigen Überprüfung Wechseldatenträger überprüfen**  
  Ermöglicht Windows Defender die Überprüfung von Wechseldatenträgern (z.B. USB-Speichersticks) auf schädliche und unerwünschte Software während einer vollständigen Überprüfung. Windows Defender Antivirus überprüft auf USB-Geräten alle Dateien, bevor diese ausgeführt werden.
  
  **Standard**: Ja  
  
- **Archivdateien überprüfen**  
  Archivdateien überprüfen in Defender.
  
  **Standard**: Ja
  
- **Verhaltensüberwachung**  
  Erlaubt oder verhindert die Funktionalität der Windows Defender-Verhaltensüberwachung. Diese in Windows 10 eingebetteten Sensoren sammeln und verarbeiten Signale zum Verhalten des Betriebssystems und senden diese Sensordaten an Ihre private, isolierte Cloudinstanz von Microsoft Defender ATP.
  
  **Standard**: Ja

- **Über Netzwerkordner geöffnete Dateien überprüfen**  
  Wenn Dateien schreibgeschützt sind, können Benutzer entdeckte Schadsoftware nicht entfernen.
  
  **Standard**: Ja

- **Nicht vertrauenswürdiger USB-Prozesstyp**  
  Mit dieser Regel können Administratoren verhindern, dass nicht signierte oder nicht vertrauenswürdige ausführbare Dateien von USB-Wechseldatenträgern, einschließlich SD-Karten, ausgeführt werden.
  
  **Standard**: Blockieren
  
- **Injectionstyp für andere Prozesse in Office-Apps**  
  Office-Apps, einschließlich Word, Excel, PowerPoint und OneNote, können keinen Code in andere Prozesse einfügen. Dieses Verfahren zum Ausführen von schädlichem Code ist typisch für Schadsoftware bei dem Versuch, die Aktivität vor Antivirusprogrammen zu verstecken.
  
  **Standard**: Blockieren
  
- **Win32-Importtyp aus Office-Makrocode gestatten**  
  Schadsoftware kann Makrocode in Office-Dateien verwenden, um Win32-DLLs zu importieren und zu laden, mit denen dann API-Aufrufe möglich sind, um eine Infektion des gesamten Systems zu ermöglichen. Mit dieser Regel wird versucht, Office-Dateien zu blockieren, die Makrocode enthalten, in den Win32-DLLs importiert werden können. Dazu zählen Microsoft Word, Excel, PowerPoint und OneNote.
  
  **Standard**: Blockieren  
  
- **Defender-Cloud-Block-Level**  
  Defender-Cloud-Block-Level.
  
  **Standard**: Nicht konfiguriert

- **Echtzeitüberwachung**  
  Für Defender ist eine Echtzeitüberwachung erforderlich.
  
  **Standard**: Ja
  
- **Mit Office-Apps ausführbare Inhaltserstellung oder Starttypen**  
  Diese Regel zielt auf typische Verhalten von verdächtigen und schädlichen Add-Ons und Skripts (Erweiterungen) ab, die ausführbare Dateien erstellen oder starten. Dies ist ein typisches Verfahren von Schadsoftware. Die Verwendung von Erweiterungen durch Office-Apps wird blockiert. Typischerweise verwenden diese Erweiterungen den Windows Scripting Host (WSH-Dateien), um Skripts auszuführen, die bestimmte Aufgaben automatisieren oder von Benutzern erstellte Add-On-Features bieten.
  
  **Standard**: Blockieren

### <a name="windows-ink-workspace"></a>Windows Ink-Arbeitsbereich  

Weitere Informationen finden Sie unter [Policy CSP - WindowsInkWorkspace (Richtlinien-Konfigurationsdienstanbieter - WindowsInkWorkspace)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in Ihrer Windows-Dokumentation.  

- **Ink-Arbeitsbereich**  
  Gibt an, ob der Benutzer auf den Ink-Arbeitsbereich zugreifen darf. 
  - *Deaktiviert*: Der Zugriff auf den Ink-Arbeitsbereich ist deaktiviert. Die Funktion ist deaktiviert.
  - *Aktiviert*: Der Ink-Arbeitsbereich ist aktiviert, aber der Benutzer kann nicht über den Sperrbildschirm darauf zugreifen.
  - *Nicht konfiguriert* – Der Ink-Arbeitsbereich ist aktiviert, und der Benutzer kann über den Sperrbildschirm darauf zugreifen.  

  **Standard**: Aktiviert
 
### <a name="windows-powershell"></a>Windows PowerShell  

Weitere Informationen finden Sie unter [Policy CSP - WindowsPowerShell (Richtlinien-Konfigurationsdienstanbieter - WindowsPowerShell)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in Ihrer Windows-Dokumentation.  

- **PowerShell-Shellskriptblock-Protokollierung**  
  Mit dieser Richtlinieneinstellung können alle PowerShell-Skript-Eingaben im Microsoft-Windows-PowerShell/Operational-Ereignisprotokoll protokolliert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, protokolliert Windows PowerShell die Verarbeitung von Befehlen, Skriptblöcken, Funktionen und Skripts, unabhängig davon, ob diese interaktiv oder automatisch aufgerufen wurden. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist das Protokollieren von PowerShell-Skript-Eingaben deaktiviert. Wenn Sie die Protokollierung von Skriptblockaufrufen aktivieren, protokolliert PowerShell zusätzlich Protokollereignisse, wenn ein Befehl, ein Skriptblock, eine Funktion oder Skriptstarts oder -stops aufgerufen werden. Das Aktivieren der Protokollierung von Aufrufen führt zu einer großen Anzahl von Ereignisprotokollen. Hinweis: Diese Richtlinieneinstellung ist sowohl unter„Computerkonfiguration“ als auch unter „Benutzerkonfiguration“ im Editor für Gruppenrichtlinien vorhanden. Die Richtlinieneinstellung in der Computerkonfiguration hat Vorrang vor der Richtlinieneinstellung in der Benutzerkonfiguration.
  
  **Standard**: Aktiviert
 
## <a name="next-steps"></a>Nächste Schritte  

[Aktuelle Baselineversion anzeigen](security-baseline-settings-mdm-all.md?pivots=mdm-may-2019)  
[Upgradeprofile für die Verwendung einer neuen Baselineversion](security-baselines.md#change-the-baseline-version-for-a-profile)
