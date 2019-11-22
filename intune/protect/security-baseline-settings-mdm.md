---
title: Intune-Einstellungen für Sicherheitsbaselines in Windows 10
titleSuffix: Microsoft Intune
description: Überprüfen Sie die Standardeinstellungen und verfügbaren Einstellungen in der Windows MDM-Sicherheitsbaseline für Windows 10-Geräte, die Sie mit InTune verwalten.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d673650a26f3917fa32babba42e5e2054c87e59
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74060027"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>MDM-Einstellungen für Sicherheitsbaselines in Intune  

Zeigen Sie die MDM-Sicherheitsbaseline-Einstellungen an, die von Microsoft InTune für Geräte unterstützt werden, die Windows 10 oder höher ausführen. Die Standardwerte für Einstellungen in dieser Baseline stellen die empfohlene Konfiguration für anwendbare Geräte dar und stimmen möglicherweise nicht mit den Basis Linien Standards aus anderen Sicherheitsbaselines ab.  

Die neueste Baselineversion ist die **MDM-Sicherheitsbaseline für Mai 2019** .  

Weitere Informationen zu den Änderungen, die in der aktuellen Version dieser Baseline von der vorherigen Version geändert wurden, finden Sie unter Was hat sich [in der neuen Vorlage geändert](#whats-changed-in-the-new-template).  

> [!NOTE]  
> Im Juni 2019 wurde die Vorschauversion der MDM-Sicherheitsbaseline durch die Version der *MDM-Sicherheitsbaseline für* die Vorlage "Mai 2019" ersetzt, die allgemein verfügbar ist (nicht in der Vorschau). Profile, die vor der Verfügbarkeit der *MDM-Sicherheitsbaseline für* die Baseline "Mai 2019" erstellt wurden, werden nicht aktualisiert, um die Einstellungen und Werte in der MDM-Sicherheitsbaseline für die Version von Mai 2019 widerzuspiegeln.  Obwohl Sie keine neuen Profile basierend auf der Vorschau Vorlage erstellen können, können Sie die zuvor erstellten Profile, die auf der Vorschau Vorlage basieren, bearbeiten und weiter verwenden.   
  
Weitere Informationen zur Verwendung von Sicherheitsbaselines mit InTune finden Sie unter [Verwenden von Sicherheitsbaselines](security-baselines.md).  


   
## <a name="above-lock"></a>Sperrbildschirm  
Weitere Informationen finden Sie unter [Policy CSP - AboveLock (Richtlinien-Konfigurationsdienstanbieter: AboveLock)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in Ihrer Windows-Dokumentation.  

- **Anzeige von Popupbenachrichtigungen blockieren**  
  Diese Richtlinieneinstellung ermöglicht Ihnen, zu verhindern, dass App-Benachrichtigungen auf dem Sperrbildschirm angezeigt werden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden keine App-Benachrichtigungen auf dem Sperrbildschirm angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer wählen, welche Apps Benachrichtigungen auf dem Sperrbildschirm anzeigen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Standard**: Ja  

- **Sprachaktivierung von Apps über Sperrbildschirm**  

  **Standard**: Deaktiviert

## <a name="app-runtime"></a>App-Laufzeit    
Weitere Informationen finden Sie unter [Policy CSP - AppRuntime (Richtlinien-Konfigurationsdienstanbieter: AppRuntime)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in Ihrer Windows-Dokumentation.  

- **Microsoft-Konten optional für Windows Store-Apps**  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob für Windows Store-Apps, die eine Anmeldung mit einem Konto erfordern, Microsoft-Konten optional sind. Diese Richtlinie betrifft nur Windows Store-Apps, die dies unterstützen. Wenn Sie diese Richtlinieneinstellung aktivieren, ermöglichen Windows Store-Apps, die normalerweise die Anmeldung mit einem Microsoft-Konto erfordern, Benutzern stattdessen die Anmeldung mit einem Unternehmenskonto. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, müssen Benutzer sich mit einem Microsoft-Konto anmelden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Standard**: Aktiviert  

## <a name="application-management"></a>Anwendungsverwaltung   
Weitere Informationen finden Sie unter [Policy CSP - ApplicationManagement (Richtlinien-Konfigurationsdienstanbieter: ApplicationManagement)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in Ihrer Windows-Dokumentation.  

- **Benutzersteuerung für Installationen blockieren**  
  Diese Richtlinien Einstellung ermöglicht es Benutzern, Installationsoptionen zu ändern, die in der Regel nur für Systemadministratoren verfügbar sind. Wenn Sie diese Richtlinien Einstellung aktivieren, werden einige der Sicherheitsfunktionen von Windows Installer umgangen. Sie ermöglicht die Ausführung von Installationen, die andernfalls aufgrund einer Sicherheitsverletzung angehalten werden. Wenn Sie diese Richtlinien Einstellung deaktivieren oder nicht konfigurieren, können die Sicherheitsfunktionen von Windows Installer verhindern, dass Benutzer Installationsoptionen ändern, die in der Regel für Systemadministratoren reserviert sind, z. b. das Verzeichnis, in dem die Dateien installiert werden. Wenn Windows Installer feststellt, dass der Benutzer durch ein Installationspaket eine geschützte Option ändern kann, wird die Installation angehalten, und es wird eine Meldung angezeigt. Diese Sicherheitsfeatures funktionieren nur, wenn das Installationsprogramm in einem privilegierten Sicherheitskontext ausgeführt wird, in dem Sie Zugriff auf Verzeichnisse hat, die für den Benutzer verweigert wurden. Diese Richtlinien Einstellung ist für weniger restriktive Umgebungen konzipiert. Sie kann verwendet werden, um Fehler in einem Installationsprogramm zu umgehen, das verhindert, dass Software installiert wird.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Standard**: Ja

- **Blockieren von MSI-App-Installationen mit erhöhten Rechten**  
  Diese Richtlinieneinstellung weist den Windows Installer an, bei der Installation von Programmen auf dem System erhöhte Rechte anzuwenden.  
  - *Wenn Sie diese Richtlinien Einstellung aktivieren*, werden Berechtigungen auf alle Programme ausgeweitet. Diese Berechtigungen sind in der Regel für Programme reserviert, die dem Benutzer (auf dem Desktop angeboten) zugewiesen, dem Computer zugewiesen (automatisch installiert) werden oder in der Systemsteuerung unter Software verfügbar gemacht wurden. Diese Profileinstellung ermöglicht es Benutzern, Programme zu installieren, die Zugriff auf Verzeichnisse benötigen, für die der Benutzer möglicherweise nicht über die Berechtigung zum Anzeigen oder ändern verfügt, einschließlich der Verzeichnisse auf stark eingeschränkten Computern.
  - *Wenn Sie diese Richtlinien Einstellung deaktivieren oder nicht konfigurieren*, wendet das System die Berechtigungen des aktuellen Benutzers an, wenn Programme installiert werden, die von einem Systemadministrator nicht verteilt oder angeboten werden. Hinweis: Diese Richtlinieneinstellung wird sowohl in den Ordnern für die Computerkonfiguration als auch für die Benutzerkonfiguration angezeigt. Damit diese Richtlinien Einstellung wirksam wird, müssen Sie Sie in beiden Ordnern aktivieren. Vorsicht: qualifizierte Benutzer können die Berechtigungen nutzen, die diese Richtlinien Einstellung erteilt, um Ihre Berechtigungen zu ändern und permanenten Zugriff auf eingeschränkte Dateien und Ordner zu erhalten. Beachten Sie, dass die Benutzer Konfigurations Version dieser Richtlinien Einstellung nicht garantiert sicher ist.  
  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Standard**: Ja

- **Game DVR (nur Desktop) blockieren**  
  konfiguriert, ob Aufzeichnen und Übertragen von Spielen zulässig ist.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Standard**: Ja  

## <a name="auto-play"></a>Automatische Wiedergabe   
Weitere Informationen finden Sie unter [Policy CSP - Autoplay (Richtlinien-Konfigurationsdienstanbieter: Autoplay)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in Ihrer Windows-Dokumentation.  

- **Standardverhalten für automatische Ausführung der automatischen Wiedergabe**  
  Diese Einstellung betrifft das Standardverhalten für AutoRun-Befehle. AutoRun-Befehle werden in autorun.inf-Dateien gespeichert und können Installationsprogramme oder andere Routinen auslösen. Wenn das Standardverhalten für AutoRun-Befehle *Aktiviert* ist, können es Administratoren auf einem Gerät ändern, das Windows Vista oder eine höhere Version ausführt. Für das Verhalten bestehen die folgenden Einstellungsmöglichkeiten: a) AutoRun-Befehle komplett deaktivieren, oder b) Wiederherstellen des Verhaltens vor der Ausführung von Windows Vista, damit AutoRun-Befehle wieder automatisch ausgeführt werden. Wenn *Deaktiviert* oder *Nicht konfiguriert* eingestellt ist, wird der Benutzer von Geräten, auf denen Windows Vista ausgeführt wird, dazu aufgefordert, zu entscheiden, ob ein AutoRun-Befehl ausgeführt werden soll.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Standard**: Nicht ausführen  
  
- **Modus für automatische Wiedergabe**  
  Diese Richtlinieneinstellung ermöglicht Ihnen, die Funktion für die automatische Wiedergabe zu deaktivieren. Die automatische Wiedergabe startet den Lesevorgang von einem Laufwerk, sobald Sie Medien in das Laufwerk einlegen. Daher wird die Installationsdatei von Programmen sofort gestartet, und Musik auf Audiomedien wird sofort abgespielt. In Versionen vor Windows XP SP2 ist die automatische Wiedergabe standardmäßig auf Wechseldatenträgern wie dem Diskettenlaufwerk (nicht aber auf dem CD-ROM-Laufwerk) und Netzlaufwerken deaktiviert. Ab Windows XP SP2 ist die automatische Wiedergabe auch für Wechseldatenträger, einschließlich Ziplaufwerken und einigen USB-Massenspeichergeräten, aktiviert. Wenn Sie diese Richtlinieneinstellung aktivieren, ist die automatische Wiedergabe auf CD-ROM-Laufwerken und Wechselmedien oder auf allen Laufwerken deaktiviert. Diese Richtlinieneinstellung deaktiviert die automatische Wiedergabe auf weiteren Laufwerktypen. Sie können diese Einstellung nicht dazu verwenden, die automatische Wiedergabe auf Laufwerken zu aktivieren, auf denen sie standardmäßig deaktiviert ist. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, ist die automatische Wiedergabe aktiviert. Hinweis: Diese Richtlinieneinstellung wird sowohl in den Ordnern für die Computerkonfiguration als auch für die Benutzerkonfiguration angezeigt. Wenn die Richtlinieneinstellungen miteinander im Konflikt stehen, hat die Richtlinieneinstellung in der Computerkonfiguration Vorrang gegenüber der Richtlinieneinstellung in der Benutzerkonfiguration.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Standard**: Deaktiviert

- **Automatische Wiedergabe für Nicht-Volume-Geräte blockieren**  
  Diese Richtlinieneinstellung deaktiviert die automatische Wiedergabe für MTP-Geräte wie Kameras oder Telefone. Wenn Sie diese Richtlinieneinstellung aktivieren, ist die automatische Wiedergabe auf MTP-Geräten wie Kameras oder Telefonen nicht möglich. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, ist die automatische Wiedergabe für Nicht-Volume-Geräte aktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Standard**: Aktiviert  

## <a name="bitlocker"></a>BitLocker    
Weitere Informationen finden Sie unter [Policy CSP - BitLocker (Richtlinien-Konfigurationsdienstanbieter: BitLocker)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in Ihrer Windows-Dokumentation.  

- **Richtlinie für BitLocker-Verschlüsselung von Wechseldatenträgern**  
  Diese Richtlinieneinstellung wird verwendet, um die Verschlüsselungsmethode und Verschlüsselungsstärke zu steuern. Die Werte dieser Richtlinie bestimmen die Stärke der Verschlüsselung, die BitLocker für die Verschlüsselung verwendet. Unternehmen sollten die Verschlüsselungsstufe für erhöhte Sicherheit steuern (AES-256 ist sicherer als AES-128). Wenn Sie diese Einstellung aktivieren, können Sie einen Verschlüsselungsalgorithmus konfigurieren und für Festplattenlaufwerke, Betriebssystemlaufwerke und Wechseldatenträger die Verschlüsselungsstärke für Schlüssel individuell konfigurieren. Für Festplatten- und Betriebssystemlaufwerke wird die Verwendung des XTS-AES-Algorithmus empfohlen. Für Wechseldatenträger sollten Sie AES-CBC 128-Bit oder AES-CBC 256-Bit verwenden, wenn es in anderen Geräten verwendet wird, auf denen nicht Windows 10, Version 1511 oder höher ausgeführt wird. Das Ändern der Verschlüsselungsmethode hat keine Auswirkungen, wenn das Laufwerk bereits verschlüsselt ist oder die Verschlüsselung gerade ausgeführt wird. In diesen Fällen wird diese Richtlinieneinstellung ignoriert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Konfigurieren Sie bei der Richtlinie für BitLocker-Verschlüsselung von Wechseldatenträgern die folgende Einstellung:

  - **Verschlüsselung für Schreibzugriff anfordern**  
    **Standard**: Ja  
  

## <a name="browser"></a>Browser  
Weitere Informationen finden Sie unter [Policy CSP - Browser (Richtlinien-Konfigurationsdienstanbieter - Browser)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in Ihrer Windows-Dokumentation.  

- **SmartScreen für Microsoft Edge anfordern**  
  Microsoft Edge verwendet Microsoft Defender SmartScreen (aktiviert), um Benutzer standardmäßig vor potenziellen betrügerischen Phishingangriffen und Schadsoftware zu schützen. Standardmäßig ist auch eingestellt, dass Benutzer Microsoft Defender SmartScreen nicht deaktivieren können. Wenn Sie diese Richtlinie aktivieren, wird Microsoft Defender SmartScreen deaktiviert und kann von Benutzern nicht aktiviert werden. Konfigurieren Sie diese Richtlinie nicht so, dass Benutzer auswählen können, ob Microsoft Defender SmartScreen aktiviert oder deaktiviert wird.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Standard**: Ja  
  
- **Zugriff auf schädliche Websites blockieren**  
  Standardmäßig ermöglicht Microsoft Edge es Benutzern, die Warnungen von Microsoft Defender SmartScreen zu potenziell schädlichen Websites zu umgehen (ignorieren) und trotzdem auf die betreffende Website zuzugreifen. Mit dieser Richtlinie können Sie Microsoft Edge jedoch so konfigurieren, dass Benutzer die Warnungen nicht umgehen und nicht auf die Website zugreifen können.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Standard**: Ja  
  
- **Block unverified file download** (Herunterladen nicht überprüfter Dateien blockieren)  
  Standardmäßig ermöglicht Microsoft Edge es Benutzern, die Warnungen von Microsoft Defender SmartScreen zu potenziell schädlichen Dateien zu umgehen (ignorieren) und nicht geprüfte Dateien trotzdem herunterzuladen. Durch die Aktivierung dieser Richtlinie wird verhindert, dass Benutzer die Warnungen umgehen und die nicht geprüfte(n) Datei(en) herunterladen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Standard**: Ja  
  
- **Kennwort-Manager blockieren**  
  Standardmäßig verwendet Microsoft Edge den Kennwort-Manager automatisch, wodurch Benutzern die lokale Verwaltung von Kennwörtern ermöglicht wird. Wenn diese Richtlinie deaktiviert wird, kann Microsoft Edge den Kennwort-Manager nicht nutzen. Konfigurieren Sie diese Richtlinie nicht, wenn Sie Benutzern erlauben möchten, selbst zu entscheiden, ob sie den Kennwort-Manager zum lokalen Speichern und Verwalten von Kennwörtern verwenden möchten.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Standard**: Ja  
  
- **Prevent certificate error overrides** (Überschreiben von Zertifikatfehlern verhindern)  
  Diese Richtlinieneinstellung verhindert, dass der Benutzer SSL/TLS-Zertifikatfehler (Secure Sockets Layer/Transport Layer Security), die die Navigation in Internet Explorer unterbrechen (z.B. „Abgelaufen“, „Gesperrt“ oder „Name stimmt nicht überein“ ) ignoriert. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer das Browsen nicht mehr fortsetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann der Benutzer entscheiden, ob Zertifikatfehler ignoriert werden sollen und das Browsen fortsetzen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Standard**: Ja  

## <a name="connectivity"></a>Verbindung  
Weitere Informationen finden Sie unter [Policy CSP – Connectivity (Richtlinien-Konfigurationsdienstanbieter: Konnektivität)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in der Windows-Dokumentation.  

- **Block Internet download for web publishing and online ordering wizards** (Internet-Download für die Assistenten „Webpublishing“ und „Onlinebestellung von Abzügen“ deaktivieren)  
  Diese Richtlinieneinstellung legt fest, ob Windows eine Liste von Anbietern für den Webpublishing-Assistenten und den Assistenten für Onlinebestellung herunterladen soll. Diese Assistenten ermöglichen Benutzern, aus einer Liste Firmen auszuwählen, die Dienste wie Onlinespeicherung und Fotodruck anbieten. Standardmäßig werden zusätzlich zu den in der Registrierung angegebenen Anbietern auch solche angezeigt, die von einer Windows-Website heruntergeladen wurden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden keine Anbieter heruntergeladen, sondern nur die Dienstanbieter angezeigt, die in der lokalen Registrierung zwischengespeichert sind. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird eine Liste von Anbietern heruntergeladen, wenn der Benutzer den Webpublishing-Assistenten und den Assistenten für Onlinebestellung verwendet. Weitere Informationen über den Webpublishing-Assistenten und den Assistenten für Onlinebestellung finden Sie in der Dokumentation, einschließlich Details über das Angeben von Dienstanbietern in der Registrierung.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Standard**: Aktiviert  

- **Sicheren Zugriff auf UNC-Pfade konfigurieren**  
  Diese Richtlinien Einstellung konfiguriert den sicheren Zugriff auf UNC-Pfade. Wenn Sie diese Richtlinie aktivieren, lässt Windows nur den Zugriff auf die angegebenen UNC-Pfade zu, nachdem zusätzliche Sicherheitsanforderungen erfüllt wurden.
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **Standard**: Windows so konfigurieren, dass nur der Zugriff auf die angegebenen UNC-Pfade gestattet wird, nachdem zusätzliche Sicherheitsanforderungen erfüllt wurden
  
  Wenn Sie *Windows so konfigurieren, dass nur der Zugriff auf die angegebenen UNC-Pfade gestattet wird, nachdem die Sicherheitsanforderungen erfüllt* sind, können Sie die Liste * der UNC-Pfade mit dem Namen "nicht definiert" Konfigurieren
  - **Liste der festgeschriebenen UNC-Pfade**  
    Wählen Sie **Hinzufügen** aus, um zusätzliche sicherheitsflags und Server Pfade anzugeben.  

- **Block downloading of print drivers over HTTP** (Download von Druckertreibern über HTTP blockieren)  
  Diese Richtlinieneinstellung gibt an, ob dieser Client Druckertreiberpakete über HTTP herunterladen darf. Nicht im Lieferumfang enthaltene Treiber müssen über HTTP heruntergeladen werden, um das HTTP-Drucken einzurichten. Hinweis: Diese Richtlinieneinstellung hindert den Client nicht, auf Druckern im Intranet oder Internet über HTTP zu drucken. Sie verhindert nur das Herunterladen von Treibern, die noch nicht lokal installiert sind. Wenn Sie diese Richtlinieneinstellung aktivieren, können keine Druckertreiber über HTTP heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können die Benutzer Druckertreiber über HTTP herunterladen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Standard**: Aktiviert  

## <a name="credentials-delegation"></a>Delegierung von Anmeldeinformationen  
Weitere Informationen finden Sie unter [Policy CSP – CredentialsDelegation (Richtlinien-Konfigurationsdienstanbieter: CredentialsDelegation)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in der Windows-Dokumentation.  

- **Remote host delegation of non-exportable credentials** (Remotehostdelegierung nicht exportierbarer Anmeldeinformationen)  
  Remotehost ermöglicht die Delegierung nicht exportierbarer Anmeldeinformationen. Bei Verwendung der Delegierung von Anmeldeinformationen stellen Geräte eine exportierbare Version der Anmeldeinformationen für den Remotehost bereit. Dadurch laufen Benutzer Gefahr, dass ihre Anmeldeinformationen von Angreifern auf dem Remotehost gestohlen werden. Wenn Sie die Richtlinieneinstellung aktivieren, unterstützt der Host den eingeschränkten Verwaltungsmodus oder Remote Credential Guard-Modus. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden der eingeschränkte Verwaltungsmodus und der Remote Credential Guard-Modus nicht unterstützt, und Benutzer müssen ihre Anmeldeinformationen immer an den Host übergeben.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Standard**: Aktiviert  

## <a name="credentials-ui"></a>Benutzeroberfläche für Anmeldeinformationen  
Weitere Informationen finden Sie unter [Policy CSP – Connectivity (Richtlinien-Konfigurationsdienstanbieter: CredentialsUI)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in der Windows-Dokumentation.  

- **Enumerate administrators** (Administratoren auflisten) Diese Richtlinieneinstellung steuert, ob Administratorkonten angezeigt werden, wenn ein Benutzer versucht, eine Anwendung mit erhöhten Rechten auszuführen. Standardmäßig werden Administratorkonten beim Versuch eines Benutzers, eine Anwendung mit erhöhten Rechten auszuführen, nicht angezeigt. Wenn Sie diese Richtlinieneinstellung aktivieren, werden alle lokalen Administratorkonten auf dem Computers angezeigt, damit der Benutzer eines auswählen und das richtige Kennwort eingeben kann. Wenn Sie diese Richtlinieneinstellung deaktivieren, müssen Benutzer jedes Mal einen Benutzernamen und ein Kennwort eingeben, um eine Anwendung mit erhöhten Rechten auszuführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Standard**: Deaktiviert  

## <a name="data-protection"></a>Schutz von Daten  
Weitere Informationen finden Sie unter [Policy CSP – Defender (Richtlinien-Konfigurationsdienstanbieter: DataProtection)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in der Windows-Dokumentation.  

- **Block direct memory access** (Direkten Speicherzugriff blockieren)  
  Mit dieser Richtlinieneinstellung können Sie den direkten Speicherzugriff (Direct Memory Access, DMA) für alle Hot-Plug-PCI-Downstream-Anschlüsse blockieren, bis sich ein Benutzer bei Windows anmeldet. Sobald sich ein Benutzer anmeldet, werden die mit den Hot-Plug-PCI-Anschlüssen verbundenen PCI-Geräte von Windows aufgezählt. Jedes Mal, wenn der Benutzer den Computer sperrt, wird DMA an Hot-Plug-PCI-Anschlüssen ohne untergeordnete Geräte blockiert, bis sich der Benutzer erneut anmeldet. Geräte, die vor dem Entsperren des Computers bereits aufgezählt wurden, sind weiterhin funktionsfähig, bis sie entfernt werden oder das System neu gestartet bzw. in den Ruhezustand versetzt wird. Die Richtlinieneinstellung wird nur erzwungen, wenn BitLocker oder die Geräteverschlüsselung aktiviert ist.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Standard**: Ja  

## <a name="device-guard"></a>Device Guard  
Weitere Informationen finden Sie unter [Policy CSP – DeviceGuard (Richtlinien-Konfigurationsdienstanbieter: DeviceGuard)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in der Windows-Dokumentation.  

- **Credential Guard**  
  Mit dieser Einstellung können Benutzer Credential Guard mit virtualisierungsbasierter Sicherheit aktivieren, um den Schutz von Anmeldeinformationen beim nächsten Neustart zu unterstützen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Standard**: Mit UEFI-Sperre aktivieren 

- **Enable virtualization based security**  (Virtualisierungsbasierte Sicherheit aktivieren)  
  Aktiviert die virtualisierungsbasierte Sicherheit (VBS) beim nächsten Neustart. Virtualisierungsbasierte Sicherheit verwendet Windows Hypervisor, um die Sicherheitsdienste zu unterstützen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Standard**: Ja  


- **Launch system guard**   (Systemschutz starten)  
  **Standard**: Aktiviert  

## <a name="device-installation"></a>Geräteinstallation  
Weitere Informationen finden Sie unter [Policy CSP – DeviceInstallation (Richtlinien-Konfigurationsdienstanbieter: DeviceInstallation)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in der Windows-Dokumentation.  

- **Hardware device installation by device identifiers** (Installation von Hardwaregeräten anhand der Geräte-ID)  
  Mit dieser Richtlinieneinstellung können Sie eine Liste von Plug & Play-Hardware-IDs und kompatiblen IDs für Geräte angeben, deren Installation unter Windows verhindert wird. Diese Richtlinieneinstellung hat Vorrang gegenüber jeder anderen Richtlinieneinstellung, die die Installation eines Geräts ermöglicht. Wenn Sie diese Richtlinieneinstellung aktivieren, kann ein Gerät nicht installiert oder aktualisiert werden, wenn die zugehörige Hardware-ID oder kompatible ID in der von Ihnen erstellten Liste enthalten ist. Wenn Sie diese Richtlinieneinstellung auf einem Remotedesktopserver aktivieren, wirkt sich dies auf die Umleitung der angegebenen Geräte von einem Remotedesktopclient an den Remotedesktopserver aus. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Geräte installiert und aktualisiert werden, sofern andere Richtlinieneinstellungen dies zulassen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
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
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Standard**: Block hardware device installation (Hardwaregeräteinstallation blockieren)  

  Wenn *Block hardware device installation* ausgewählt wurde, stehen die folgenden Einstellungen zur Verfügung.
  - **Remove matching hardware devices**   (Übereinstimmende Hardwaregeräte entfernen)  
    Diese Einstellung ist nur verfügbar, wenn *Hardware device installation by setup classes (Hardwaregeräteinstallation nach Setup-Klasse)* auf *Block hardware device installation (Hardwaregeräteinstallation blockieren)* eingestellt ist.  

    **Standard**: *Keine Standardkonfiguration*  

  - **Hardware device identifiers that are blocked** (Blockierte Bezeichner von Hardwaregeräten)  
    Diese Einstellung ist nur verfügbar, wenn *Hardware device installation by setup classes (Hardwaregeräteinstallation nach Setup-Klasse)* auf *Block hardware device installation (Hardwaregeräteinstallation blockieren)* eingestellt ist.
    
    **Standard**: *Keine Standardkonfiguration*  

## <a name="device-lock"></a>Gerätesperre  
Weitere Informationen finden Sie unter [Policy CSP - DeviceLock (Richtlinien-CSP: DeviceLock)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in Ihrer Windows-Dokumentation.  

- **Verwendung der Kamera verhindern**  
  Deaktiviert das Ein-/Ausschalten der Kamera auf dem Sperrbildschirm in den PC-Einstellungen und verhindert, dass eine Kamera auf dem Sperrbildschirm aufgerufen wird. Standardmäßig können Benutzer das Aufrufen einer verfügbaren Kamera auf dem Sperrbildschirm aktivieren. Wenn Sie diese Einstellung aktivieren, können Benutzer den Kamerazugriff auf den Sperrbildschirm in den PC-Einstellungen nicht mehr aktivieren, und die Kamera kann nicht mehr auf dem Sperrbildschirm aufgerufen werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Standard**: Aktiviert  

- **Kennwort anfordern**  
  Gibt an, ob eine Gerätesperre aktiviert ist.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Standard**: Ja  
  
  Wenn *Kennwort anfordern* auf *Ja* festgelegt wurde, stehen die folgenden Einstellungen zur Verfügung.

  - **Mindestanzahl von Zeichensätzen für Kennwörter**  
    Anzahl der komplexen Elementtypen (Groß- und Kleinbuchstaben, Zahlen und Interpunktionszeichen), die für eine sichere PIN oder ein sicheres Kennwort erforderlich sind. Die PIN erzwingt das folgende Verhalten für Desktop- und mobile Geräte: 1 – nur Ziffern; 2 – Ziffern und Kleinbuchstaben sind erforderlich; 3 – Ziffern, Kleinbuchstaben und Großbuchstaben sind erforderlich. Nicht unterstützt in Microsoft- und Domänenkonten für Desktopgeräte. 4: Ziffern, Kleinbuchstaben, Großbuchstaben und Sonderzeichen sind erforderlich. Nicht unterstützt für Desktop-Geräte. Der Standardwert lautet 1.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Standard**: 3  

  - **Anzahl von fehlgeschlagenen Anmeldungen, bevor das Gerät zurückgesetzt wird**  
    Die Anzahl von zulässigen Authentifizierungsfehlern bevor das Gerät zurückgesetzt wird. Der Wert 0 deaktiviert die Rücksetzfunktion eines Geräts.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Standard**: 10  

  - **Kennwortablauf (Tage)**  
    Die Richtlinieneinstellung für das maximale Kennwortalter bestimmt die Zeitspanne (in Tagen), in der ein Kennwort verwendet werden kann, bevor das System den Benutzer zum Ändern des Kennworts auffordert. Sie können einstellen, dass Kennwörter nach einer bestimmten Anzahl von Tagen (zwischen 1 und 999) ablaufen, oder dass Kennwörter nie ablaufen, indem Sie die Anzahl der Tage auf 0 einstellen. Wenn das maximale Kennwortalter zwischen 1 und 999 Tagen liegt, muss das minimale Kennwortalter darunter liegen. Wenn das maximale Kennwortalter auf 0 eingestellt ist, kann das minimale Kennwortalter ein Wert zwischen 0 und 998 Tagen sein.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Standard**: 60  

  - **Erforderlicher Kennworttyp**  
    Bestimmt den Typ der erforderlichen PIN oder des erforderlichen Kennworts.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Standard**: Alphanumerisch  

  - **Minimale Kennwortlänge**  
    Die Richtlinieneinstellung für die minimale Kennwortlänge bestimmt die Mindestanzahl von Zeichen, die ein Kennwort für ein Benutzerkonto besitzen muss. Sie können einen Wert zwischen 1 und 14 Zeichen einstellen, oder Sie können einstellen, dass kein Kennwort erforderlich ist, indem Sie die Zeichenanzahl auf 0 einstellen.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Standard**: 8  

  - **Einfache Kennwörter blockieren**  
    Gibt an, ob PINs oder Kennwörter wie „1111“ oder „1234“ zulässig sind. Für Desktop-Geräte wird auch die Verwendung von Bildcodes gesteuert.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Standard**: Ja  
      *Eine Einstellung auf „Ja“ verhindert die Verwendung einfacher Kennwörter.* 

  - **Wiederverwendung vorheriger Kennwörter verhindern**  
    Gibt an, wie viele Kennwörter, die nicht mehr verwendet werden können, im Verlauf gespeichert werden können. Der Wert schließt das aktuelle Kennwert des Benutzers mit ein. So kann der Benutzer beispielsweise bei der Einstellung *1* sein aktuelles Kennwort nicht ändern, wenn er ein neues Kennwort auswählt. Die Einstellung *5* bedeutet, dass ein Benutzer sein neues Kennwort nicht auf sein aktuelles Kennwort oder eines seiner vorherigen vier Kennwörter festlegen kann.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Standard**: 24  

- **Diashow verhindern**  
  Deaktiviert die Diashow-Einstellungen für den Sperrbildschirm in den PC-Einstellungen und verhindert das Abspielen einer Diashow auf dem Sperrbildschirm. Standardmäßig können Benutzer eine Diashow aktivieren, die nach dem Sperren des Computers abgespielt wird. Wenn Sie diese Einstellung aktivieren, können Benutzer Diashow-Einstellungen in den PC-Einstellungen nicht ändern, und es kann keine Diashow gestartet werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Standard**: Aktiviert  
  *Die Einstellung „Deaktiviert“ verhindert das Abspielen von Diashows.* 

- **Minimales Kennwortalter in Tagen**  
  Die Richtlinieneinstellung für das minimale Kennwortalter bestimmt die Zeitspanne (in Tagen), in der ein Kennwort verwendet werden muss, bevor der Benutzer es ändern kann. Sie können einen Wert zwischen 1 und 998 Tagen festlegen, oder Sie können Kennwortänderungen sofort zulassen, indem Sie die Anzahl der Tage auf 0 setzen. Das minimale Kennwortalter muss unter dem maximalen Kennwortalter liegen, es sei denn, das maximale Kennwortalter ist auf 0 eingestellt, was bedeutet, dass ein Kennwörter nie ablaufen. Wenn das maximale Kennwortalter auf 0 eingestellt ist, kann für das minimale Kennwortalter ein Wert zwischen 0 und 998 eingestellt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Standard**: 1  

## <a name="dma-guard"></a>DMA-Wächter  
Weitere Informationen finden Sie unter [Policy CSP – DmaGuard (Richtlinien-Konfigurationsdienstanbieter: DmaGuard)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) in der Windows-Dokumentation.
- **Aufzählung externer Geräte, die mit Kernel-DMA-Schutz nicht kompatibel sind**  
  Diese Richtlinie soll zusätzliche Sicherheit gegen externe DMA-fähige Geräte bereitstellen. Sie ermöglicht eine bessere Kontrolle über die Aufzählung von externen DMA-fähigen Geräten, die mit DMA Remapping/Gerätespeicherisolation und Sandboxing nicht kompatibel sind. Diese Richtlinie gilt nur, wenn der Kernel-DMA-Schutz unterstützt wird und durch die Systemfirmware aktiviert wurde. Der Kernel DMA-Schutz ist ein Platt Form Feature, das nicht über Richtlinien oder Endbenutzer gesteuert werden kann. Er muss zum Zeitpunkt der Herstellung vom System unterstützt werden. Um zu überprüfen, ob das System Kernel DMA-Schutz unterstützt, überprüfen Sie das Feld Kernel DMA Protection auf der Seite Zusammenfassung von Msinfo32. exe.  
  [Erfahren Sie mehr](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Standard**: Alles blockieren   

## <a name="event-log-service"></a>Ereignisprotokolldienst  
Weitere Informationen finden Sie unter [Policy CSP - EventLogService (Richtlinien-Konfigurationsdienstanbieter: EventLogService)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in Ihrer Windows-Dokumentation.  

- **Sicherheitsprotokoll: maximale Dateigröße in kB**  
  Diese Richtlinieneinstellung gibt die maximale Größe der Protokolldatei in Kilobyte an. Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie die maximale Protokolldateigröße so konfigurieren, dass sie zwischen 1 Megabyte (1.024 Kilobyte) und 2 Terabyte (2.147.483.647 Kilobyte) in Kilobyte-Schritten liegt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die maximale Größe der Protokolldatei auf den lokal konfigurierten Wert eingestellt. Dieser Wert kann durch den lokalen Administrator über das Dialogfeld „Protokolleigenschaften“ geändert werden und wird standardmäßig auf 20 Megabyte eingestellt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Standard**: 196608  

- **Systemprotokoll: maximale Dateigröße in kB**  
  Diese Richtlinieneinstellung gibt die maximale Größe der Protokolldatei in Kilobyte an. Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie die maximale Protokolldateigröße so konfigurieren, dass sie zwischen 1 Megabyte (1.024 Kilobyte) und 2 Terabyte (2.147.483.647 Kilobyte) in Kilobyte-Schritten liegt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die maximale Größe der Protokolldatei auf den lokal konfigurierten Wert eingestellt. Dieser Wert kann durch den lokalen Administrator über das Dialogfeld „Protokolleigenschaften“ geändert werden und wird standardmäßig auf 20 Megabyte eingestellt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Standard**: 32768  

- **Anwendungsprotokoll: maximale Dateigröße in kB**  
  Diese Richtlinieneinstellung gibt die maximale Größe der Protokolldatei in Kilobyte an. Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie die maximale Protokolldateigröße so konfigurieren, dass sie zwischen 1 Megabyte (1.024 Kilobyte) und 2 Terabyte (2.147.483.647 Kilobyte) in Kilobyte-Schritten liegt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die maximale Größe der Protokolldatei auf den lokal konfigurierten Wert eingestellt. Dieser Wert kann durch den lokalen Administrator über das Dialogfeld „Protokolleigenschaften“ geändert werden und wird standardmäßig auf 20 Megabyte eingestellt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Standard**: 32768  

## <a name="experience"></a>Erfahrung  
Weitere Informationen finden Sie unter [Policy CSP - Experience (Richtlinien-Konfigurationsdienstanbieter: Experience)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in Ihrer Windows-Dokumentation.  

- **Windows-Blickpunkt blockieren**  
  Ermöglicht IT-Administratoren, alle Features von Windows-Blickpunkt zu deaktivieren – Windows-Blickpunkt auf dem Sperrbildschirm, Windows-Tipps, Microsoft-Features für Endbenutzer und weitere ähnliche Features.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Standard**: Ja  

  Wenn *Windows-Blickpunkt blockieren* auf *Ja* festgelegt wurde, stehen die folgenden Einstellungen zur Verfügung.
  
  - **Drittanbietervorschläge in Windows-Blickpunkt blockieren**  
    Gibt an, ob App- und Inhaltsvorschläge durch Herausgeber von Drittanbieter-Software in Features von Windows-Blickpunkt (z.B. Windows-Blickpunkt auf dem Sperrbildschirm, vorgeschlagene Apps im Startmenü oder Windows-Tipps) zulässig sind. Benutzer sehen möglicherweise trotzdem Vorschläge für Microsoft-Features, -Apps und -Dienste.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Standard**: Ja  
  - **Bestimmte Funktionen für Endbenutzer blockieren**  
    Ermöglicht IT-Administratoren das Aktivieren von Funktionen, die normalerweise nur für Endbenutzer bestimmt sind, beispielsweise Startvorschläge, Mitgliedschaftsbenachrichtigungen, App-Installation nach Anzeige der Windows-Willkommensseite und Kachelumleitungen.  
    [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Standard**: Ja  

## <a name="exploit-guard"></a>Exploit Guard  
Weitere Informationen finden Sie unter [Policy CSP - ExploitGuard (Richtlinien-Konfigurationsdienstanbieter: ExploitGuard)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in Ihrer Windows-Dokumentation.  

- **Exploit-Schutz-XML**  
  Ermöglicht dem IT-Administrator, eine Konfiguration vorzunehmen, die für alle Geräte in der Organisation die gewünschten Optionen zur Risikominderung für System und Anwendungen abbildet. Die Konfiguration wird in einer XML-Datei vorgenommen. Durch den Exploit-Schutz können Geräte vor Schadsoftware geschützt werden, die Exploits für die Verbreitung und den Befall von Systemen verwendet. Sie können die App „Windows-Sicherheit“ oder PowerShell verwenden, um Lösungen zur Entschärfung (Konfigurationen) zu erstellen. Diese Konfiguration können Sie anschließend als XML-Datei exportieren und für die Computer in Ihrem Netzwerk freigeben, sodass diese über dieselben Einstellungen zur Entschärfung verfügen. Sie können außerdem eine vorhandene XML-Konfigurationsdatei aus EMET in eine XML-Konfigurationsdatei für den Exploit-Schutz konvertieren und importieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Standard:** *Sample xml is provided* (XML-Beispieldatei wird bereitgestellt) 
 
## <a name="file-explorer"></a>Datei-Explorer  
Weitere Informationen finden Sie unter [Policy CSP - FileExplorer (Richtlinien-CSP: FileExplorer)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in der Windows-Dokumentation.  

- **Block data execution prevention** (Schutz vor Ausführung von Daten blockieren)  
  Wenn Sie den Schutz vor der Ausführung von Daten deaktivieren, können bestimmte veraltete Plug-In-Anwendungen erfolgreich ausgeführt werden, ohne dass der Explorer geschlossen wird.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Standard**: Deaktiviert  
   
- **Block heap termination on corruption** (Beenden von Heaps bei Beschädigung blockieren)  
  Wenn Sie das Beenden von Heaps bei Beschädigung deaktivieren, können bestimmte veraltete Plug-In-Anwendungen erfolgreich ausgeführt werden, ohne dass der Explorer sofort geschlossen wird. Der Explorer wird jedoch möglicherweise zu einem späteren Zeitpunkt unerwartet beendet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Standard**: Deaktiviert  
    

## <a name="internet-explorer"></a>Internet Explorer  
Weitere Informationen finden Sie unter [Policy CSP - Internet Explorer (Richtlinien-CSP: Internet Explorer)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in der Windows-Dokumentation.  

- **Internet Explorer restricted zone updates to status bar via script** (Skriptgesteuerte Updates für die Statusleiste in der eingeschränkten Zone von Internet Explorer)  
  Über diese Richtlinieneinstellung können Sie festlegen, ob die Statusleiste in der Zone durch Skripts aktualisiert werden darf. 
  - *Wenn Sie diese Richtlinieneinstellung aktivieren*, kann die Statusleiste über Skripts aktualisiert werden.
  - *Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren*, kann die Statusleiste nicht über Skripts aktualisiert werden.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Standard**: Deaktiviert

- **Internet Explorer internet zone drag and drop or copy and paste files** (Drag & Drop oder Kopieren und Einfügen von Dateien in einer Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer Dateien aus einer Quelle innerhalb der Zone per Drag & Drop verschieben oder kopieren und einfügen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Dateien automatisch aus dieser Zone per Drag & Drop verschieben oder kopieren und einfügen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob sie Dateien aus dieser Zone ziehen oder kopieren möchten. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Dateien aus dieser Zone nicht per Drag & Drop verschieben oder kopieren und einfügen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Dateien automatisch aus dieser Zone per Drag & Drop verschieben oder kopieren und einfügen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Standard**: Deaktivieren

- **Internet Explorer restricted zone .NET Framework reliant components**   (.NET Framework-Komponenten in eingeschränkten Zonen von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die nicht mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer nicht signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob nicht signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer nicht signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer nicht signierte verwaltete Komponenten nicht aus.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Standard**: Deaktivieren


- **Internet Explorer local machine zone do not run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in lokaler Computerzone in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Standard**: Deaktiviert

- **Internet Explorer internet zone access to data sources** (Zugriff auf Datenquellen in Internetzonen in Internet Explorer)  
  Durch diese Richtlinieneinstellung können Sie festlegen, ob Internet Explorer mithilfe von Microsoft XML Parser (MSXML) oder ActiveX Data Objects (ADO) auf Daten aus anderen Sicherheitszonen zugreifen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer eine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie im Dropdownfeld „Prompt“ (Bestätigen) auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob eine Seite in der Zone geladen werden soll, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone drag content from different domains within windows** (Ziehen von Inhalten aus verschiedenen Domänen in Fenstern in einer eingeschränkten Zone in Internet Explorer)  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel im selben Fenster befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel im selben Fenster befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ nicht ändern.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Standard**: Deaktiviert
  
- **Internet Explorer certificate address mismatch warning** (Warnung für Zertifikatadressenkonflikte in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Sicherheitswarnung für Zertifikatadressenkonflikte aktivieren. Wenn diese Richtlinieneinstellung aktiviert ist, wird der Benutzer gewarnt, wenn eine sichere HTTP-Website (HTTPS) Zertifikate enthält, die für eine andere Adresse ausgestellt wurden. Durch diese Warnung können Spoofingangriffe verhindert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die Warnung für Zertifikatadressenkonflikte immer angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann der Benutzer über die Seite „Erweitert“ in der Internetsystemsteuerung festlegen, ob die Warnung für Zertifikatadressenkonflikte angezeigt wird.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Standard**: Aktiviert 
  
- **Internet Explorer restricted zone less privileged sites** (Websites mit geringeren Berechtigung in der eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Websites aus Zonen mit geringeren Berechtigungen, z.B. aus der Internetzone, zu dieser Zone navigieren können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Websites aus Zonen mit geringeren Berechtigungen neue Fenster in dieser Zone öffnen oder zu dieser Zone navigieren. Die Sicherheitszone wird ohne den zusätzlichen Schutz durch das Sicherheitsfeature „Schutz vor Zonenanhebung“ ausgeführt. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer gewarnt, dass er dabei ist, in einen möglicherweise gefährlichen Bereich zu navigieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden potentiell gefährliche Navigationsvorgänge verhindert. Wie von „Schutz vor Zonenanhebung“ festgelegt, ist das Internet Explorer-Sicherheitsfeature ist in dieser Zone aktiviert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden potentiell gefährliche Navigationsvorgänge verhindert. Wie von „Schutz vor Zonenanhebung“ festgelegt, ist das Internet Explorer-Sicherheitsfeature ist in dieser Zone aktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone automatic prompt for file downloads** (Automatische Eingabeaufforderung für Dateidownloads in der eingeschränkten Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob eine Eingabeaufforderung bei Dateidownloads angezeigt wird, die nicht vom Benutzer gestartet werden. Downloaddialogfelder werden unabhängig von dieser Einstellung für vom Benutzer gestartete Downloadvorgänge angezeigt. Wenn Sie diese Einstellung aktivieren, werden den Benutzern Downloaddialogfelder für automatische Downloadversuche angezeigt. Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, werden Dateidownloads, die nicht von Benutzern gestartet werden, blockiert, und Benutzern wird die Benachrichtigungsleiste anstelle des Downloaddialogfelds angezeigt. Die Benutzer können dann auf die Benachrichtigungsleiste klicken, um den Dateidownload zu genehmigen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Standard**: Deaktiviert
  
- **Internet Explorer internet zone .NET Framework reliant components** (.NET Framework-Komponenten in Internetzonen von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die nicht mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer nicht signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob nicht signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer nicht signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer nicht signierte verwaltete Komponenten aus.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer internet zone allow only approved domains to use tdc Active X controls** (Nur genehmigte Domänen können das TDC-ActiveX-Steuerelement in Internetzonen in Internet Explorer verwenden)  
  Diese Richtlinieneinstellung steuert, ob der Benutzer das TDC-ActiveX-Steuerelement auf Websites ausführen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird das TDC-ActiveX-Steuerelement nicht von Websites in dieser Zone ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird das TDC-ActiveX-Steuerelement von allen Websites in dieser Zone ausgeführt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Standard**: Aktiviert 
  
- **Internet Explorer restricted zone script initiated windows** (Durch Skripts geöffnete Fenster für die eingeschränkte Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Einschränkungen zu durch Skripts geöffneten Popupfenstern und Fenstern mit Titel und Leisten verwalten. Wenn Sie diese Richtlinieneinstellung aktivieren, gilt das Sicherheitsfeature für Fenstereinschränkungen in dieser Zone nicht. Die Sicherheitszone wird also ohne die Sicherheitsebene ausgeführt, die von diesem Feature bereitgestellt wird. Wenn Sie diese Richtlinieneinstellung deaktivieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer internet zone include local path when uploading files to server** (Informationen zu lokalen Pfaden beim Hochladen von Dateien auf Server einfügen – Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, ob Informationen zu lokalen Pfaden beim Hochladen einer Datei über ein HTML-Formular übermittelt werden. Wenn die Informationen zu lokalen Pfaden übermittelt werden, kann es vorkommen, dass einige davon versehentlich für den Server offengelegt werden. Dabei kann es sich beispielsweise um Dateien vom Desktop des Benutzers handeln, die den Benutzernamen im Pfad enthalten. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular entfernt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt werden sollen. Die Pfadinformationen werden standardmäßig gesendet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer disable processes in enhanced protected mode** (Deaktivieren von Prozessen im erweiterten geschützten Modus in Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob 64-Bit-Prozesse (höhere Sicherheit) oder 32-Bit-Prozesse (bessere Kompatibilität) von Internet Explorer 11 verwendet werden, wenn unter 64-Bit-Versionen von Windows der erweiterte geschützte Modus aktiv ist. Wichtig: Einige ActiveX-Steuerelemente und Symbolleisten sind möglicherweise nicht verfügbar, wenn 64-Bit-Prozesse verwendet werden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden 64-Bit-Registerkartenprozesse von Internet Explorer 11 verwendet, sofern der erweiterte geschützte Modus unter 64-Bit-Versionen von Windows aktiv ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden 32-Bit-Registerkartenprozesse von Internet Explorer 11 verwendet, sofern der erweiterte geschützte Modus unter 64-Bit-Versionen von Windows aktiv ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer dieses Feature über die Internet Explorer-Einstellungen ein- oder ausschalten. Dieses Feature ist standardmäßig deaktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Standard**: Aktiviert 
  
- **Internet Explorer ignore certificate errors** (Zertifikatfehler in Internet Explorer ignorieren)  
  Diese Richtlinieneinstellung verhindert, dass der Benutzer SSL/TLS-Zertifikatfehler (Secure Sockets Layer/Transport Layer Security), die die Navigation in Internet Explorer unterbrechen (z.B. „Abgelaufen“, „Gesperrt“ oder „Name stimmt nicht überein“ ) ignoriert. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer das Browsen nicht mehr fortsetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann der Benutzer entscheiden, ob Zertifikatfehler ignoriert werden sollen und das Browsen fortsetzen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer internet zone loading of XAML files** (Laden von XAML-Dateien in der Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie das Laden von XAML-Dateien (Extensible Application Markup Language) verwalten. XAML ist eine deklarative Markupsprache auf XML-Grundlage, die normalerweise zum Erstellen intelligenter Benutzeroberflächen und Grafiken verwendet wird, die Windows Presentation Foundation nutzen. Wenn Sie diese Richtlinieneinstellung aktivieren und im Dropdownfeld „Aktivieren“ festgelegt ist, werden die XAML-Dateien automatisch in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer zum Laden von XAML-Dateien aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden XAML-Dateien nicht in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer entscheiden, ob XAML-Dateien in Internet Explorer geladen werden sollen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer internet zone automatic prompt for file downloads** (Automatische Eingabeaufforderung für Dateidownloads in der Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob eine Eingabeaufforderung bei Dateidownloads angezeigt wird, die nicht vom Benutzer gestartet werden. Downloaddialogfelder werden unabhängig von dieser Einstellung für vom Benutzer gestartete Downloadvorgänge angezeigt. Wenn Sie diese Einstellung aktivieren, werden den Benutzern Downloaddialogfelder für automatische Downloadversuche angezeigt. Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, werden Dateidownloads, die nicht von Benutzern gestartet werden, blockiert, und Benutzern wird die Benachrichtigungsleiste anstelle des Downloaddialogfelds angezeigt. Die Benutzer können dann auf die Benachrichtigungsleiste klicken, um den Dateidownload zu genehmigen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files** (Sicherheitswarnung für potenziell unsichere Dateien in der eingeschränkten Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob die Nachricht „Datei öffnen – Sicherheitswarnung“ angezeigt wird, wenn der Benutzer versucht, ausführbare Dateien oder andere potenziell unsichere Dateien (z.B. aus einer Dateifreigabe im Intranet über den Datei-Explorer) zu öffnen. Wenn Sie diese Richtlinieneinstellung aktivieren und „Aktivieren“ im Dropdownfeld auswählen, werden diese Dateien ohne Sicherheitswarnung geöffnet. Wenn Sie das Dropdownfeld auf „Bestätigen“ einstellen, wird eine Sicherheitswarnung angezeigt, bevor die Dateien geöffnet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden diese Dateien nicht geöffnet. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer konfigurieren, wie der Computer diese Dateien behandeln soll. Standardmäßig werden diese Dateien in der eingeschränkten Zone blockiert, in der Intranetzone sowie in Zonen für lokale Computer aktiviert und in Internetzonen und vertrauenswürdigen Zonen auf „Bestätigen“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone cross site scripting filter** (Cross-Site Scripting-Filter in der Internetzone von Internet Explorer)  
  Mit dieser Richtlinie können Sie steuern, ob websiteübergreifende Skripteinschleusungen in Websites in dieser Zone vom XSS-Filter (Cross-Site Scripting) erkannt und verhindert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der XSS-Filter für Websites in dieser Zone aktiviert, um Versuche einer websiteübergreifenden Skripteinschleusung zu blockieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der XSS-Filter für Websites in dieser Zone deaktiviert, und Internet Explorer lässt die websiteübergreifende Skripteinschleusung zu.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Standard**: Aktiviert 
  
- **Internet Explorer fallback to SSL3** (Fallback auf SSL3 in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie unsichere Fallbacks auf SSL 3.0 blockieren. Wenn die Richtlinie aktiviert ist und TLS 1.0 oder höher einen Fehler verursacht, versucht Internet Explorer, über SSL 3.0 oder eine niedrigere Version eine Verbindung mit Websites herzustellen. Es wird empfohlen, unsichere Fallbacks nicht zuzulassen, um Man-in-the-Middle-Angriffe zu vermeiden. Die Richtlinie wirkt sich nicht darauf aus, welche Sicherheitsprotokolle aktiviert sind. Wenn Sie diese Richtlinie deaktivieren, werden die Standardeinstellungen des Systems verwendet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Standard**: Keine Standorte  

- **Unterstützung der Internet Explorer-Verschlüsselung**  
  Mit dieser Richtlinien Einstellung können Sie die Unterstützung für Transport Layer Security (TLS) 1,0, TLS 1,1, TLS 1,2 Secure Sockets Layer (SSL) 2,0 oder SSL 3,0 im Browser deaktivieren. TLS und SSL sind Protokolle, die den Schutz der Kommunikation zwischen dem Browser und dem Zielserver erleichtern. Wenn der Browser versucht, eine geschützte Kommunikation mit dem Zielserver einzurichten, verhandeln der Browser und der Server, welches Protokoll und welche Version verwendet werden sollen. Der Browser und der Server versuchen, die Liste der unterstützten Protokolle und Versionen der jeweils anderen Liste zu vergleichen, und wählen die am meisten bevorzugte Übereinstimmung aus. Wenn Sie diese Richtlinien Einstellung aktivieren, aushandelt der Browser einen Verschlüsselungs Tunnel mit den von Ihnen ausgewählten Verschlüsselungsmethoden in der Dropdown Liste und aushandelt ihn nicht. Wenn Sie diese Richtlinien Einstellung deaktivieren oder nicht konfigurieren, kann der Benutzer auswählen, welche Verschlüsselungsmethode der Browser unterstützt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Standard**: 2 Elemente: TLS v 1.1 und TLS v 1.2  
  *Wählen Sie den Pfeil nach unten aus, um Optionen anzuzeigen, die Sie für diese Einstellung auswählen können.*
  
- **Internet Explorer locked down internet zone java permissions** (SmartScreen-Filter für gesperrte Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Standard**: Aktiviert 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame** (Anwendungen und Dateien in einem iFrame in einer eingeschränkten Zone in Internet Explorer starten)  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob Anwendungen ausgeführt und Dateien aus einem iFrame-Verweis im HTML-Code der Seiten in dieser Zone heruntergeladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Anwendungen ausführen und Dateien aus iFrames auf den Seiten in dieser Zone ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ aus dem Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob Anwendungen ausgeführt und Daten aus iFrames auf den Seiten in dieser Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Anwendungen ausführen und keine Daten aus iFrames auf den Seiten in dieser Zone herunterladen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer keine Anwendungen ausführen und keine Daten aus iFrames auf den Seiten in dieser Zone herunterladen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer bypass smart screen warnings about uncommon files** (SmartScreen-Warnungen zu ungewöhnlichen Dateien in Internet Explorer umgehen)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer Warnungen des SmartScreen-Filters umgehen können. Der SmartScreen-Filter warnt Benutzer vor ausführbaren Dateien im Internet, die selten von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung aktivieren, hindern die Warnungen des SmartScreen-Filters Benutzer am Herunterladen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Warnungen des SmartScreen-Filters umgehen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone protected mode** (Popupblocker für die Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob unerwünschte Popupfenster angezeigt werden. Popupfenster, die geöffnet werden, wenn der Endbenutzer auf einen Link klickt, werden nicht blockiert. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die meisten unerwünschten Popupfenster nicht angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Popupfenster angezeigt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die meisten unerwünschten Popupfenster nicht angezeigt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Standard**: Aktivieren  
  
- **Internet Explorer processes consistent MIME handling** (Prozesse für die konsistente MIME-Verarbeitung in Internet Explorer)  
  Internet Explorer enthält dynamische Binärverhalten: Komponenten, die spezifische Funktionalität für die HTML-Elemente einkapseln, an die sie angefügt sind. Mit dieser Richtlinieneinstellung wird gesteuert, ob Binärverhalten durch die Sicherheitseinschränkungen verhindert oder zugelassen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Binärverhalten für alle Datei-Explorer- und Internet Explorer-Prozesse verhindert. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Binärverhalten für alle Datei-Explorer- und Internet Explorer-Prozesse zugelassen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Binärverhalten für alle Datei-Explorer- und Internet Explorer-Prozesse verhindert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone java permissions (Java-Berechtigungen für eingeschränkte Zonen in Internet Explorer)**  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Standard**: Java deaktivieren  
    
  
- **Internet Explorer Active X controls in protected mode** (ActiveX-Steuerelemente im geschützten Modus in Internet Explorer)  
  Diese Richtlinieneinstellung verhindert, dass ActiveX-Kontrollen im geschützten Modus ausgeführt werden, wenn der erweiterte geschützte Modus aktiviert ist. Hat ein Benutzer eine ActiveX-Kontrolle installiert, die nicht mit dem erweiterten geschützten Modus kompatibel ist, und versucht eine Website, diese Kontrolle zu laden, zeigt Internet Explorer dem Benutzer eine entsprechende Benachrichtigung an und bietet die Option an, die Website im regulären geschützten Modus auszuführen. Diese Richtlinieneinstellung deaktiviert diese Benachrichtigung und erzwingt die Ausführung aller Websites im erweiterten geschützten Modus. Der erweiterte geschützte Modus bietet einen zusätzlichen Schutz gegen Websites mit Schadsoftware, indem er bei 64-Bit-Versionen von Windows 64-Bit-Prozesse verwendet. Bei Computern mit Windows 8 oder höher beschränkt der erweiterte geschützte Modus außerdem die Speicherorte von Internet Explorer in der Registrierung und im Dateisystem. Wenn ein Benutzer bei aktiviertem erweiterten geschützten Modus eine Website aufruft, die versucht, eine ActiveX-Kontrolle zu laden, die nicht mit dem erweiterten geschützten Modus kompatibel ist, zeigt Internet Explorer dem Benutzer eine entsprechende Benachrichtigung an und bietet die Option an, die Website im regulären geschützten Modus auszuführen. Wenn Sie diese Richtlinieneinstellung deaktivieren, zeigt der Internet Explorer dem Benutzer die Option, den erweiterten geschützten Modus zu deaktivieren, nicht an. Alle Websites, die im geschützten Modus ausgeführt werden sollten, werden im erweiterten geschützten Modus ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, zeigt Internet Explorer dem Benutzer eine Benachrichtigung an, in der er ihm die Option bietet, Websites mit nicht kompatiblen ActiveX-Kontrollen im regulären geschützten Modus auszuführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone loading of XAML files** (Laden von XAML-Dateien in eingeschränkten Zonen in Internet Explorer zulassen)  
  Mit dieser Richtlinieneinstellung können Sie das Laden von XAML-Dateien (Extensible Application Markup Language) verwalten. XAML ist eine deklarative Markupsprache auf XML-Grundlage, die normalerweise zum Erstellen intelligenter Benutzeroberflächen und Grafiken verwendet wird, die Windows Presentation Foundation nutzen. Wenn Sie diese Richtlinieneinstellung aktivieren und im Dropdownfeld „Aktivieren“ festgelegt ist, werden die XAML-Dateien automatisch in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer zum Laden von XAML-Dateien aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden XAML-Dateien nicht in Internet Explorer geladen. Benutzer können dieses Verhalten nicht ändern. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer entscheiden, ob XAML-Dateien in Internet Explorer geladen werden sollen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer processes MK protocol security restriction** (Internet Explorer-Prozesse, Sicherheitseinschränkung für Skriptfenster)  
  Internet Explorer lässt zu, das Skripts programmgesteuert Fenster verschiedener Typen öffnen und in Größe und Position anpassen können. Die Sicherheitsfunktion für Fenstereinschränkungen schränkt Popupfenster ein und verhindert, dass Skripts Fenster anzeigen, in denen Titel- und Statusleiste für den Benutzer nicht sichtbar sind oder die die Sichtbarkeit der Titel- und Statusleiste anderer Fenster behindern. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Skriptfenster für alle Prozesse eingeschränkt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden Skriptfenster nicht eingeschränkt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Standard**: Aktiviert   
  
- **Internet Explorer restricted zone download signed Active X controls** (Signierte ActiveX-Steuerelemente und -Plug-Ins in eingeschränkten Zonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob ActiveX-Steuerelemente und Plug-Ins über die festgelegte Zone auf Seiten in Internet Explorer ausgeführt werden kann. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Steuerelemente und Plug-Ins ohne Benutzereingriff ausgeführt. Wenn Sie die Option „Bestätigen“ im Dropdownfeld ausgewählt haben, werden Benutzer dazu aufgefordert, auszuwählen, ob Steuerelemente oder Plug-Ins ausgeführt werden dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Steuerelemente und Plug-Ins nicht ausgeführt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Steuerelemente und Plug-Ins nicht ausgeführt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting** (ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer ausführen, die für die Skripterstellung als sicher gekennzeichnet wurden)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob ein ActiveX-Steuerelement, das für die Skripterstellung als sicher gekennzeichnet wurde, mit einem Skript interagieren darf. Wenn Sie diese Richtlinie aktivieren, kann mit Skripts automatisch ohne Benutzereingriff interagiert werden. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob sie die Skriptinteraktion erlauben möchten. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist keine Skriptinteraktion erlaubt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, ist keine Skriptinteraktion erlaubt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone logon options** (Anmeldeoptionen für eingeschränkte Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Einstellungen für Anmeldeoptionen verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie eine der folgenden Anmeldeoptionen auswählen. 
  - *Anonym*: Verwenden Sie die anonyme Anmeldung, um die HTTP-Authentifizierung zu deaktivieren. Das Gastkonto kann nur für das CIFS-Protokoll (Common Internet File System) verwendet werden. 
  - *Nach Benutzername und Kennwort fragen*: Verwenden Sie „Nach Benutzername und Kennwort fragen“, um die Benutzer-IDs und Kennwörter von Benutzern abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. 
  - *Automatisches Anmelden nur in der Intranetzone* – Verwenden Sie diese Option, um Benutzer-IDs und Kennwörter von Benutzern in anderen Zonen abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. 
  - *Automatische Anmeldung mit aktuellem Benutzernamen und Kennwort* – Verwenden Sie diese Option, um die Anmeldung mithilfe der NTLM-Authentifizierung (auch bekannt als „integrierte Windows-Authentifizierung“ oder „Windows NT Challenge Response“) durchzuführen. Wenn der Server die NTLM-Authentifizierung unterstützt, wird der Netzwerkbenutzername und das Kennwort des Benutzers für die Anmeldung verwendet. Wenn die NTLM-Authentifizierung vom Server nicht unterstützt wird, wird der Benutzer dazu aufgefordert, seinen Benutzernamen und sein Kennwort einzugeben. 

  Wenn Sie diese Richtlinieneinstellung deaktivieren, wird die *automatische Anmeldung nur in der Intranetzone zugelassen*. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird *Nach Benutzername und Kennwort fragen* für die Anmeldung festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Standard**: Anonym  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe** (ActiveX-Steuerelementen in vertrauenswürdigen Zonen in Internet Explorer initialisieren und skripten, die als unsicher gekennzeichnet sind)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer check server certificate revocation** (Serverzertifikatwiderrufstatus in Internet Explorer prüfen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Internet Explorer den Widerrufstatus der Serverzertifikat prüft. Zertifikate werden widerrufen, wenn sie kompromittiert wurden oder nicht mehr gültig sind. Durch diese Option wird verhindert, dass Benutzer vertrauliche Daten an eine Website übermitteln, die unter Betrugsverdacht steht oder nicht sicher ist. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer, ob Serverzertifikate widerrufen wurden. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer nicht, ob Serverzertifikate widerrufen wurden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer nicht, ob Serverzertifikate widerrufen wurden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Standard**: Aktiviert 
  
- **Internet Explorer internet zone less privileged sites** (Websites mit geringeren Berechtigung in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Websites aus Zonen mit geringeren Berechtigungen, z.B. eingeschränkte Websites, zu dieser Zone navigieren können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Websites aus Zonen mit geringeren Berechtigungen neue Fenster in dieser Zone öffnen oder zu dieser Zone navigieren. Die Sicherheitszone wird ohne den zusätzlichen Schutz durch das Sicherheitsfeature „Schutz vor Zonenanhebung“ ausgeführt. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, wird der Benutzer gewarnt, dass er dabei ist, in einen möglicherweise gefährlichen Bereich zu navigieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden potentiell gefährliche Navigationsvorgänge verhindert. Wie von „Schutz vor Zonenanhebung“ festgelegt, ist das Internet Explorer-Sicherheitsfeature ist in dieser Zone aktiviert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Websites aus Zonen mit geringeren Berechtigungen neue Fenster in dieser Zone öffnen oder zu dieser Zone navigieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone file downloads** (Dateidownloads in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Dateidownloads aus dieser Zone zulässig sind. Diese Option hängt von der Zone der Webseite ab, die den Downloadlink enthält, und nicht von der Zone, in die heruntergeladen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, können Dateien aus der Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können keine Dateien aus der Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können keine Dateien aus der Zone heruntergeladen werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with authenticode** (Mit Authenticode signierte .NET Framework-Komponenten in Internetzonen von Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer prevent per user installation of Active X controls** (Installation von ActiveX-Steuerelementen pro Benutzer in Internet Explorer verhindern)  
  Mit dieser Richtlinieneinstellung können Sie die Installation von ActiveX-Steuerelement pro Benutzer verhindern. Wenn Sie diese Richtlinieneinstellung aktivieren, können keine ActiveX-Steuerelemente pro Benutzer installiert werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können ActiveX-Steuerelemente pro Benutzer installiert werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer prevent managing smart screen filter** (Verwalten des SmartScreen Filters in Internet Explorer verhindern)  
  Diese Richtlinieneinstellung verhindert, dass der Benutzer den SmartScreen Filter verwalten kann, der den Benutzer warnt, wenn er eine Website besucht, die in der Vergangenheit durch Phishing persönliche Informationen gesammelt hat, oder wenn bekannt ist, dass die Website Schadsoftware hostet. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der Benutzer nicht aufgefordert, den SmartScreen-Filter zu aktivieren. Alle Websiteadressen, die sich nicht auf der Zulassungsliste des Filters befinden, werden automatisch an Microsoft gesendet, ohne dass der Benutzer dies bestätigen muss. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird der Benutzer bei der ersten Ausführung aufgefordert, den SmartScreen Filter zu aktivieren oder zu deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Standard**: Aktivieren  
  
- **Internet Explorer processes MIME sniffing safety feature** (Internet Explorer-Prozesse, Sicherheitsfunktion für MIME-Ermittlung)  
  Diese Richtlinieneinstellung bestimmt, ob die MIME-Ermittlung von Internet Explorer die Höherstufung einer Datei eines bestimmten Typs auf einen gefährlicheren Dateitypen verhindert. Wenn Sie diese Einstellung aktivieren, stuft die MIME-Ermittlung eine Datei eines bestimmten Typs nie auf einen gefährlicheren Dateityp hoch. Wenn Sie diese Richtlinieneinstellung deaktivieren, lassen Internet Explorer-Prozesse die Höherstufung eines Dateityps auf einen gefährlicheren Dateityp durch die MIME-Ermittlung zu. Wenn Sie diese Einstellung nicht konfigurieren, stuft die MIME-Ermittlung eine Datei eines bestimmten Typs nie auf einen gefährlicheren Dateityp hoch.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone download signed Active X controls** (Signierte ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer herunterladen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer signierte ActiveX-Steuerelemente auf einer Seite in der Zone herunterladen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer signierte Steuerelemente ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ in der Dropdownliste auswählen, werden Benutzer zur Bestätigung aufgefordert, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können signierte Steuerelemente nicht heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die Benutzer gefragt, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer auto complete** (AutoVervollständigen in Internet Explorer)  
  Die Funktion AutoVervollständigen kann Benutzernamen und Kennwörter speichern und beim Ausfüllen von Formularen vorschlagen. Wenn Sie diese Einstellung aktivieren, können die Benutzer die Einstellungen „Benutzernamen und Kennwörter für Formulare“ und „Nachfragen, ob Kennwörter gespeichert werden sollen“ anpassen. Die Funktion AutoVervollständigen wird für Benutzernamen und Kennwörter in Formularen aktiviert. Sie müssen sich entscheiden, ob Sie „Nachfragen, ob Kennwörter gespeichert werden sollen“ aktivieren möchten. Wenn Sie diese Einstellung deaktivieren, können die Benutzer die Einstellungen „Benutzernamen und Kennwörter für Formulare“ und „Nachfragen, ob Kennwörter gespeichert werden sollen“ nicht anpassen. Die Funktion AutoVervollständigen wird für Benutzernamen und Kennwörter in Formularen deaktiviert. Der Benutzer kann auch nicht selbst festlegen, dass er zur Bestätigung aufgefordert wird, ob das Kennwort gespeichert werden soll. Wenn Sie diese Einstellung nicht konfigurieren, kann der Benutzer AutoVervollständigen für „Benutzernamen und Kennwörter für Formulare“ und „Nachfragen, ob Kennwörter gespeichert werden sollen“ selbst aktivieren. Benutzer müssen zu „Internetoptionen“ navigieren und dann auf die Registerkarte „Inhalte“ und auf „Einstellungen“ klicken, um diese Option anzuzeigen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone allow vbscript to run** (Zulassen der Ausführung des VBScript in einer Internet Explorer-Zone)  
  Diese Einstellung bestimmt, ob das VBScript auf Seiten in bestimmten Internet Explorer-Zonen ausgeführt werden kann. Zu den Optionen gehören: 
  - *Aktivieren*: Das VBScript wird auf Seiten in bestimmten Zonen ohne Interaktionen ausgeführt. 
  - *Bestätigung*: Mitarbeiter werden aufgefordert festzulegen, ob das VBScript in der Zone ausgeführt werden soll. 
  - *Deaktivieren*: Das VBScript wird in der Zone nicht ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird das VBScript ohne Interaktionen in der angegebenen Zone ausgeführt.    

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls** (Nur genehmigte Domänen können das TDC-ActiveX-Steuerelement in eingeschränkten Zonen in Internet Explorer verwenden)  
  Diese Richtlinieneinstellung steuert, ob der Benutzer das TDC-ActiveX-Steuerelement auf Websites ausführen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird das TDC-ActiveX-Steuerelement nicht von Websites in dieser Zone ausgeführt. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird das TDC-ActiveX-Steuerelement von allen Websites in dieser Zone ausgeführt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in vertrauenswürdigen Zonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer local machine zone java permissions** (Java-Berechtigungen für Zonen mit lokalen Computern in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Mittlere Sicherheit“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Standard**: Java deaktivieren 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in Intranetzonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Standard**: Deaktiviert  

- **Internet Explorer restricted zone smart screen** (Scriptlets in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer Skriptlets ausführen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Skriptlets ausführen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Skriptlets nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Skriptlets aktivieren oder deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer processes notification bar** (Internet Explorer-Prozesse, Benachrichtigungsleiste)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob die Benachrichtigungsleiste für Internet Explorer-Prozesse angezeigt wird, wenn Datei- oder Codeinstallationen eingeschränkt sind. Die Benachrichtigungsleiste wird standardmäßig für Internet Explorer-Prozesse angezeigt. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die Benachrichtigungsleiste für Internet Explorer-Prozesse angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird die Benachrichtigungsleiste nicht für Internet Explorer-Prozesse angezeigt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Benachrichtigungsleiste für Internet Explorer-Prozesse angezeigt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer internet zone download signed Active X controls** (Herunterladen signierter ActiveX-Steuerelemente in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer signierte ActiveX-Steuerelemente auf einer Seite in der Zone herunterladen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer signierte Steuerelemente ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ in der Dropdownliste auswählen, werden Benutzer zur Bestätigung aufgefordert, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können signierte Steuerelemente nicht heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die Benutzer gefragt, ob Steuerelemente von nicht vertrauenswürdigen Herausgebern heruntergeladen werden sollen. Von vertrauenswürdigen Herausgebern signierter Code wird im Hintergrund heruntergeladen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone smart screen** (SmartScreen Filter in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Standard**: Aktiviert  
  
- **Schaltfläche „Run this time“ (Dieses Mal ausführen) für veraltete ActiveX-Steuerelemente in Internet Explorer entfernen**  
  Mit dieser Richtlinieneinstellung können Sie verhindern, dass Benutzer die Schaltfläche „Run this time“ (Dieses Mal ausführen) sehen und bestimmte veraltete ActiveX-Steuerelemente in Internet Explorer ausführen. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Schaltfläche „Run this time“ (Dieses Mal ausführen) in der Warnmeldung nicht sehen, die angezeigt wird, wenn Internet Explorer ein veraltetes ActiveX-Steuerelement blockiert. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Schaltfläche „Run this time“ in der Warnung sehen, die angezeigt wird, wenn Internet Explorer ein veraltetes ActiveX-Steuerelement in Internet Explorer blockiert. Durch Klicken auf diese Schaltfläche kann der Benutzer das veraltete ActiveX-Steuerelement einmal ausführen. Weitere Informationen finden Sie unter „Outdated ActiveX Controls“ (Veraltete ActiveX-Steuerelemente) in der TechNet-Bibliothek in Internet Explorer.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Standard**: Aktiviert 
  
- **Anwendungen und Dateien in einem iFrame starten für die Internetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob Anwendungen ausgeführt und Dateien aus einem iFrame-Verweis im HTML-Code der Seiten in dieser Zone heruntergeladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Anwendungen ausführen und Dateien aus iFrames auf den Seiten in dieser Zone ohne Benutzereingriff herunterladen. Wenn Sie „Bestätigen“ aus dem Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob Anwendungen ausgeführt und Daten aus iFrames auf den Seiten in dieser Zone heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Anwendungen ausführen und keine Daten aus iFrames auf den Seiten in dieser Zone herunterladen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Benutzer dazu aufgefordert, zu entscheiden, ob Anwendungen ausgeführt und Daten aus iFrames auf den Seiten in dieser Zone heruntergeladen werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Standard**: Deaktivieren 
  
- **Fenster und Frames zwischen verschiedenen Domänen navigieren für die eingeschränkte Zone von Internet Explorer**  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Standard**: Deaktivieren  
  
- **SmartScreen für die Internetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Standard**: Aktiviert  
  
- **Java-Berechtigungen für die gesperrte vertrauenswürdige Zone in Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Standard**: Java deaktivieren 
  
- **Signaturen von heruntergeladenen Programmen in Internet Explorer überprüfen**  
  Mit dieser Richtlinieneinstellung können Sie steuern, ob Internet Explorer auf Computern von Benutzern ausführbare Programme auf digitale Signaturen überprüft (was den Herausgeber von signierter Software identifiziert und verifiziert, dass diese nicht verändert oder manipuliert wurde), bevor diese heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft Internet Explorer die digitalen Signaturen von ausführbaren Programmen und zeigt ihre Identitäten an, bevor sie auf Computer von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, überprüft Internet Explorer die digitalen Signaturen von ausführbaren Programmen nicht oder zeigt ihre Identitäten nicht an, bevor sie auf Computer von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinie nicht konfigurieren, überprüft Internet Explorer die digitalen Signaturen von ausführbaren Programmen nicht oder zeigt ihre Identitäten nicht an, bevor sie auf Computer von Benutzern heruntergeladen werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Standard**: Aktiviert  
  
- **Scripting von WebBrowser-Steuerelementen in der eingeschränkten Zone von Internet Explorer**  
  Diese Richtlinieneinstellung bestimmt, ob eine Seite eingebettete WebBrowser-Steuerelemente per Skript steuern kann. Wenn Sie diese Richtlinieneinstellung aktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement möglich. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement nicht möglich. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer den Skriptzugriff auf das WebBrowser-Steuerelement aktivieren oder deaktivieren. Standardmäßig ist der Skriptzugriff auf das WebBrowser-Steuerelement nur auf dem lokalen Computer und in Intranetzonen möglich.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Standard**: Deaktiviert  
  
- **Cross-Site Scripting-Filter in der eingeschränkten Zone von Internet Explorer**  
  Mit dieser Richtlinie können Sie steuern, ob websiteübergreifende Skripteinschleusungen in Websites in dieser Zone vom XSS-Filter (Cross-Site Scripting) erkannt und verhindert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der XSS-Filter für Websites in dieser Zone aktiviert, um Versuche einer websiteübergreifenden Skripteinschleusung zu blockieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der XSS-Filter für Websites in dieser Zone deaktiviert, und Internet Explorer lässt die websiteübergreifende Skripteinschleusung zu.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Standard**: Aktiviert  
  
- **Dynamische Binär- und Skriptverhalten in der eingeschränkten Zone von Internet Explorer**  
  Diese Richtlinieneinstellung ermöglicht Ihnen, dynamische Binär- und Skriptverhalten zu verwalten: Komponenten, die spezifische Funktionalität für die HTML-Elemente einkapseln, an die sie angefügt wurden. Wenn Sie diese Richtlinieneinstellung aktivieren, stehen Binär- und Skriptverhalten zur Verfügung. Wenn Sie „Vom Administrator genehmigt“ in der Dropdownliste auswählen, sind nur Verhalten verfügbar, die in der Liste „Vom Administrator zugelassenes Verhalten“ der Richtlinie „ Sicherheitseinschränkung für Binärverhalten“ aufgeführt sind. Wenn Sie diese Richtlinieneinstellung deaktivieren, stehen Binär- und Skriptverhalten nicht zur Verfügung, es sei denn, Anwendungen haben einen benutzerdefinierten Sicherheits-Manager implementiert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, stehen Binär- und Skriptverhalten nicht zur Verfügung, es sei denn, Anwendungen haben einen benutzerdefinierten Sicherheits-Manager implementiert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Standard**: Deaktivieren  
  
- **Überprüfung der Sicherheitseinstellungen von Internet Explorer**  
  Mit dieser Richtlinieneinstellung wird die Funktion zur Überprüfung der Sicherheitseinstellungen deaktiviert, die die Sicherheitseinstellungen von Internet Explorer überprüft, um zu bestimmen, wann die Einstellungen für Internet Explorer ein potenzielles Risiko darstellen. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die Funktion deaktiviert. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die Funktion aktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Standard**: Aktiviert  
  
- **Sicherheitswarnung für potenziell unsichere Dateien in der Internetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob die Nachricht „Datei öffnen – Sicherheitswarnung“ angezeigt wird, wenn der Benutzer versucht, ausführbare Dateien oder andere potenziell unsichere Dateien (z.B. aus einer Dateifreigabe im Intranet über den Datei-Explorer) zu öffnen. Wenn Sie diese Richtlinieneinstellung aktivieren und „Aktivieren“ im Dropdownfeld auswählen, werden diese Dateien ohne Sicherheitswarnung geöffnet. Wenn Sie das Dropdownfeld auf „Bestätigen“ einstellen, wird eine Sicherheitswarnung angezeigt, bevor die Dateien geöffnet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden diese Dateien nicht geöffnet. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer konfigurieren, wie der Computer diese Dateien behandeln soll. Standardmäßig werden diese Dateien in der eingeschränkten Zone blockiert, in der Intranetzone sowie in Zonen für lokale Computer aktiviert und in Internetzonen und vertrauenswürdigen Zonen auf „Bestätigen“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Standard**: Eingabeaufforderung  
  
- **Java-Berechtigungen in der Intranetzone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Mittlere Sicherheit“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Standard**: Hohe Sicherheit 
  
- **Veraltete ActiveX-Steuerelementen in Internet Explorer blockieren**   
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Internet Explorer bestimmte veraltete ActiveX-Steuerelemente blockiert. Veraltete ActiveX-Steuerelemente werden in der Intranetzone nie blockiert. Wenn Sie diese Richtlinieneinstellung aktivieren, blockiert Internet Explorer veraltete ActiveX-Steuerelemente nicht mehr. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, blockiert Internet Explorer weiterhin bestimmte veraltete ActiveX-Steuerelemente. Weitere Informationen finden Sie unter „Outdated ActiveX Controls“ (Veraltete ActiveX-Steuerelemente) in der TechNet-Bibliothek in Internet Explorer.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Standard**: Aktiviert  
  
- **Popupblocker in der eingeschränkten Zone von Internet Explorer**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob unerwünschte Popupfenster angezeigt werden. Popupfenster, die geöffnet werden, wenn der Endbenutzer auf einen Link klickt, werden nicht blockiert. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die meisten unerwünschten Popupfenster nicht angezeigt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Popupfenster angezeigt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die meisten unerwünschten Popupfenster nicht angezeigt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Standard**: Aktivieren  
  
- **Internet Explorer processes MK protocol security restriction** (Internet Explorer-Prozesse, Sicherheitseinschränkung für MK-Protokoll)  
  Die Richtlinieneinstellung „Sicherheitseinschränkung für MK-Protokoll“ verringert die Angriffsfläche durch Blockieren des MK-Protokolls. Bei Ressourcen, die im MK-Prokoll gehostet werden, treten Fehler auf. Wenn Sie diese Richtlinieneinstellung aktivieren, wird das MK-Protokoll für den Datei-Explorer und Internet Explorer blockiert. Bei Ressourcen, die im MK-Protokoll gehostet werden, treten Fehler auf. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Anwendungen die MK-Protokoll-API verwenden. Ressourcen, die im MK-Protokoll gehostet werden, können für den Datei-Explorer und für Internet Explorer-Prozesse verwendet werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird das MK-Protokoll für den Datei-Explorer und Internet Explorer blockiert. Bei Ressourcen, die im MK-Protokoll gehostet werden, treten Fehler auf.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer trusted zone java permissions**  (Java-Berechtigungen für vertrauenswürdige Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Niedrige Sicherheit“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Standard**: Hohe Sicherheit  
  
- **Internet Explorer restricted zone scripting of java applets** (Skripting von Java-Applets in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Applets in dieser Zone für Skripts verfügbar gemacht werden. Wenn Sie diese Richtlinie aktivieren, können Skripts automatisch und ohne Benutzereingriff auf Applets zugreifen. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob ein Skript auf Applets zugreifen darf. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Skripts nicht auf Applets zugreifen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Skripts nicht auf Applets zugreifen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer locked down restricted zone java permissions**  (Java-Berechtigungen für gesperrte eingeschränkte Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Standard**: Java deaktivieren 
  
- **Internet Explorer internet zone allow only approved domains to use Active X controls**  (Nur genehmigte Domänen können das ActiveX-Steuerelement in Internetzonen in Internet Explorer verwenden)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer dazu aufgefordert werden, zuzulassen, dass ActiveX-Steuerelemente auf Websites ausgeführt werden, die nicht die Website sind, auf der das ActiveX-Steuerelement installiert wurde. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Benutzer zur Bestätigung aufgefordert, bevor die ActiveX-Steuerelemente von Websites in dieser Zone ausgeführt werden können. Der Benutzer kann die Ausführung des Steuerelements wahlweise für die aktuelle Website oder für alle Websites zulassen. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Benutzer nicht pro Website zum Zulassen von ActiveX aufgefordert, und ActiveX-Steuerelemente dürfen für alle Websites in dieser Zone ausgeführt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer include all network paths** (Alle Netzwerkpfade in Internet Explorer einbeziehen)  
  Alle Netzwerkpfade in Internet Explorer einbeziehen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer internet zone protected mode** (Geschützter Modus in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie den geschützten Modus aktivieren. Im geschützten Modus wird Internet Explorer vor der Ausnutzung von Schwachstellen geschützt. Hierbei wird die Anzahl der Speicherorte in der Registrierung und im Dateisystem verringert, in die Internet Explorer schreiben kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der geschützte Modus aktiviert. Benutzer können den geschützten Modus nicht deaktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der geschützte Modus deaktiviert. Benutzer können den geschützten Modus nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer den geschützten Modus aktivieren oder deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Standard**: Aktivieren 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe** (ActiveX-Steuerelemente in Internetzonen in Internet Explorer initialisieren und skripten, die als unsicher gekennzeichnet sind)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer locked down restricted zone java permissions**  (SmartScreen Filter für gesperrte eingeschränkte Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung aktivieren, überprüft der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden Seiten in dieser Zone vom SmartScreen-Filter nicht auf schädlichen Inhalt überprüft. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob der SmartScreen-Filter Seiten in dieser Zone auf schädlichen Inhalt überprüft. Hinweis: In Internet Explorer 7 steuert diese Richtlinieneinstellung, ob der Phishingfilter Seiten in dieser Zone auf schädlichen Inhalt überprüft.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer crash detection** (Absturzermittlung in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Absturzermittlungsfunktion der Add-On-Verwaltung verwalten. Wenn Sie diese Richtlinieneinstellung aktivieren, wird durch einen Absturz von Internet Explorer die Windows-Fehlerberichterstattung eingeleitet. Dieses Verhalten gibt es im Windows XP Professional Service Pack 1 und früher. Alle Richtlinieneinstellung für die Windows-Fehlerberichterstattung bleiben bestehen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, bleibt die Absturzermittlungsfunktion für die Add-On-Verwaltung aktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone java permissions** (Java-Berechtigungen in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die Berechtigung auf „Hohe Sicherheit“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Standard**: Java deaktivieren  
  
- **Internet Explorer restricted zone active scripting** (Active Scripting in eingeschränkten Zonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Skriptcode auf Seiten in der Zone ausgeführt werden darf. Wenn Sie diese Richtlinieneinstellung aktivieren, wird Skriptcode automatisch auf Seiten in der Zone ausgeführt. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob Skriptcode auf Seiten in der Zone ausgeführt werden darf. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird kein Skriptcode auf Seiten in der Zone ausgeführt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird kein Skriptcode auf Seiten in der Zone ausgeführt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone logon options** (Anmeldeoptionen für die Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Einstellungen für Anmeldeoptionen verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie eine der folgenden Anmeldeoptionen auswählen. Die Anmeldung kann anonym durchgeführt werden, um die HTTP-Authentifizierung zu deaktivieren, und das Gastkonto kann nur für das CIFS-Protokoll (Common Internet File System) verwendet werden. Sie können die Eingabe eines Benutzernamens und eines Kennworts anfordern, um die Benutzer-ID und Kennwörter von Benutzern abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. Sie können die automatische Anmeldung nur in der Intranetzone zulassen, um Benutzer-IDs und Kennwörter von Benutzern in anderen Zonen abzufragen. Nachdem ein Benutzer abgefragt wurde, können diese Werte für den Rest der Sitzung im Hintergrund verwendet werden. Sie können die automatische Anmeldung mit dem aktuellen Benutzernamen und Kennwort durchführen, um die Anmeldung mithilfe der NTLM-Authentifizierung (auch bekannt als Windows NT Challenge Response) durchzuführen. Wenn der Server die NTLM-Authentifizierung unterstützt, werden der Netzwerkbenutzername und das Kennwort für die Anmeldung verwendet. Wenn die NTLM-Authentifizierung vom Server nicht unterstützt wird, wird der Benutzer dazu aufgefordert, seinen Benutzernamen und sein Kennwort einzugeben. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird die automatische Anmeldung nur in der Intranetzone zugelassen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird für die Anmeldung „Automatisches Anmelden nur in der Intranetzone“ festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Standard**: Eingabeaufforderung  
  
- **Internet Explorer restricted zone allow vbscript to run**  (Zulassen der Ausführung von VBScript in einer eingeschränkten Internet Explorer-Zone)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob das VBScript über die in Internet Explorer festgelegte Zone auf Seiten ausgeführt werden kann. Wenn Sie die Option „Aktivieren“ im Dropdownfeld ausgewählt haben, kann das VBScript ohne Benutzereingriff verwendet werden. Wenn Sie die Option „Bestätigen“ im Dropdownfeld ausgewählt haben, werden Benutzer dazu aufgefordert, auszuwählen, ob das VBScript ausgeführt werden darf. Wenn Sie die Option „Deaktivieren“ im Dropdownfeld ausgewählt haben, wird die Ausführung des VBScript verhindert. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren oder deaktivieren, wird die Ausführung des VBScript verhindert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone drag content from different domains across windows** (Ziehen von Inhalten aus verschiedenen Domänen zwischen Fenstern in einer Internetzone in Internet Explorer)  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Standard**: Deaktiviert 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe** (Initialisierung und Skript von ActiveX-Steuerelementen werden in der Intranetzone in Internet Explorer als unsicher gekennzeichnet)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer download enclosures** (Herunterladen von Anlagen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung wird verhindert, dass Benutzer Dateianlagen aus einem Feed auf den Computer herunterladen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Feedsynchronisierungsengine nicht über die Eigenschaftenseite für Feeds zum Herunterladen von Anlagen konfigurieren. Entwickler können die Downloadeinstellung über die Feed-APIs nicht ändern. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Feedsynchronisierungsengine über die Eigenschaftenseite für Feeds zum Herunterladen von Anlagen konfigurieren. Außerdem können Entwickler die Downloadeinstellung dann über die Feed-APIs ändern.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone download unsigned Active X controls** (Herunterladen nicht signierter ActiveX-Steuerelemente in einer eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer nicht signierte ActiveX-Steuerelemente aus der Zone herunterladen können. Insbesondere, wenn Code aus einer nicht vertrauenswürdigen Zone stammt, kann er potenziell schädlich sein. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer nicht signierte Steuerelemente ohne Benutzereingriff ausführen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob die Ausführung von nicht signierten Steuerelementen zugelassen werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer nicht signierte Steuerelemente nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer nicht signierte Steuerelemente nicht ausführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone drag content from different domains within windows** (Ziehen von Inhalten aus verschiedenen Domänen in Fenstern in einer Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer nicht signierte ActiveX-Steuerelemente aus der Zone herunterladen können. Insbesondere, wenn Code aus einer nicht vertrauenswürdigen Zone stammt, kann er potenziell schädlich sein. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer nicht signierte Steuerelemente ohne Benutzereingriff ausführen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob die Ausführung von nicht signierten Steuerelementen zugelassen werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer nicht signierte Steuerelemente nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer nicht signierte Steuerelemente nicht ausführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer processes restrict Active X install**  (Einschränken der Installation von ActiveX-Steuerelementen mit Internet Explorer-Prozessen)  
  Diese Richtlinieneinstellung ermöglicht es Anwendungen, die das WebBrowser-Steuerelement hosten, die automatische Eingabeaufforderung für die Installation von ActiveX-Steuerelementen zu blockieren. Wenn Sie diese Richtlinieneinstellung aktivieren, blockiert das WebBrowser-Steuerelement die automatische Eingabeaufforderung für die Installation von ActiveX-Steuerelementen für alle Prozesse. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, wird die automatische Eingabeaufforderung für die Installation von ActiveX-Steuerelementen nicht vom Webbrowsersteuerelement für alle Prozesse blockiert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Standard**: Aktiviert  
  
- **Internet-Explorer-Skriptlets für Internet-Zonen**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer Skriptlets ausführen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Skriptlets ausführen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Skriptlets nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Skriptlets aktivieren oder deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files** (Drag & Drop oder Kopieren und Einfügen von Dateien in einer eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer Dateien aus einer Quelle innerhalb der Zone per Drag & Drop verschieben oder kopieren und einfügen können. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Dateien automatisch aus dieser Zone per Drag & Drop verschieben oder kopieren und einfügen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob sie Dateien aus dieser Zone ziehen oder kopieren möchten. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Dateien aus dieser Zone nicht per Drag & Drop verschieben oder kopieren und einfügen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden Benutzer dazu aufgefordert, auszuwählen, ob sie Dateien aus dieser Zone ziehen oder kopieren möchten.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer software when signature is invalid** (Software bei ungültiger Signatur in Internet Explorer)  
  Mit dieser Richtlinie können Sie verwalten, ob Software, z.B. ActiveX-Steuerelemente und Dateidownloads, von Benutzern installiert oder ausgeführt werden können, wenn die Signatur ungültig ist. Eine ungültige Signatur kann darauf hindeuten, dass die Datei manipuliert wurde. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Benutzer zum Installieren oder Ausführen von Dateien mit einer ungültigen Signatur aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer Dateien mit ungültiger Signatur weder ausführen noch installieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer entscheiden, ob sie Dateien mit ungültiger Signatur ausführen oder installieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone copy and paste via script** (Kopieren und Einfügen in einer eingeschränkten Zone mithilfe eines Skripts in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, ob Skripts in einer angegebenen Region Zwischenablagevorgänge (z.B. Ausschneiden, Kopieren und Einfügen) durchführen dürfen. Wenn Sie diese Richtlinieneinstellung aktivieren, können Skripts Zwischenablagevorgänge durchführen. Wenn Sie „Bestätigen“ im Dropdownfeld auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob Zwischenablagevorgänge ausgeführt werden dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Skripts keine Zwischenablagevorgänge durchführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Skripts keine Zwischenablagevorgänge durchführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone drag content from different domains across windows** (Ziehen von Inhalten aus verschiedenen Domänen zwischen Fenstern in einer eingeschränkten Zone in Internet Explorer)  
  Diese Richtlinieneinstellung erlaubt es Ihnen, Optionen zum Ziehen von Inhalten von einer Domäne in eine andere festzulegen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Aktivieren“ klicken, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung aktiveren und auf „Deaktivieren“ klicken, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 10 deaktivieren oder nicht konfigurieren, können die Benutzer keine Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Die Benutzer können diese Einstellung im Dialogfeld „Internetoptionen“ ändern. Wenn Sie diese Richtlinieneinstellung in Internet Explorer 9 oder einer früheren Version deaktivieren oder nicht konfigurieren, können die Benutzer Inhalte von einer Domäne in eine andere ziehen, wenn sich Quelle und Ziel in unterschiedlichen Fenstern befinden. Benutzer können diese Einstellung nicht ändern.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Standard**: Deaktiviert  
  
- **Internet Explorer users adding sites** (Internet Explorer-Benutzer dürfen keine Sites hinzufügen)  
  Durch diese Einstellung wird verhindert, dass Benutzer Sites zu Sicherheitszonen hinzufügen oder aus diesen entfernen. Bei einer Sicherheitszone handelt es sich um Websites, die die gleiche Sicherheitsstufe aufweisen. Wenn Sie diese Richtlinie aktivieren, werden die Verwaltungseinstellungen für Sites für Sicherheitszonen deaktiviert. (Sie können die Verwaltungseinstellungen für Sites für Sicherheitszonen aufrufen, indem Sie im Dialogfeld „Internetoptionen“ auf die Registerkarte „Sicherheit“ und dann auf die Schaltfläche „Sites“ klicken.) Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können Benutzer Websites hinzufügen oder aus den Zonen für vertrauenswürdige oder eingeschränkte Sites entfernen oder die Einstellungen für das lokale Intranet bearbeiten. Durch diese Richtlinie wird verhindert, dass Benutzer die Verwaltungseinstellungen für Sites für Sicherheitszonen ändern, die vom Administrator eingerichtet wurden. Hinweis: Die Richtlinie „Sicherheitsseite deaktivieren“ (unter \Benutzerkonfiguration\Administrative Vorlagen\Windows-Komponenten\Internet Explorer\Internetsystemsteuerung) entfernt die Registerkarte „Sicherheit“ aus der Benutzeroberfläche und hat somit Vorrang vor dieser Richtlinie. Ist sie aktiviert, wird diese Richtlinie ignoriert. Weitere Informationen finden Sie im Abschnitt zur Richtlinie „Sicherheitszonen: Nur Computereinstellungen verwenden“.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone script initiated windows** (Durch Skripts geöffnete Fenster für die Internetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie die Einschränkungen zu durch Skripts geöffneten Popupfenstern und Fenstern mit Titel und Leisten verwalten. Wenn Sie diese Richtlinieneinstellung aktivieren, gilt das Sicherheitsfeature für Fenstereinschränkungen in dieser Zone nicht. Die Sicherheitszone wird also ohne die Sicherheitsebene ausgeführt, die von diesem Feature bereitgestellt wird. Wenn Sie diese Richtlinieneinstellung deaktivieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können potenziell schädliche Aktionen aus durch Skripts initiierten Popupfenstern und Fenstern mit Titeln und Leisten nicht ausgeführt werden. Dieses Sicherheitsfeature von Internet Explorer wird in der Zone so verwendet, wie es im Sicherheitsfeature für durch Skripts geöffnete Fenster für den Prozess festgelegt ist.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer – Sicherheitszonen: Nur Computereinstellungen verwenden**  
  Mit dieser Einstellung werden Informationen zu Sicherheitszonen für alle Benutzer desselben Computers angewendet. Bei einer Sicherheitszone handelt es sich um Websites, die die gleiche Sicherheitsstufe aufweisen. Wenn Sie diese Richtlinie aktivieren, werden die Änderungen, die ein Benutzer an einer Sicherheitszone vornimmt, für alle Benutzer dieses Computers übernommen. Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können die Benutzer des Computers eigene Einstellungen für Sicherheitszonen einrichten. Verwenden Sie diese Richtlinie, um sicherzustellen, dass die Einstellungen für Sicherheitszonen einheitlich auf einen Benutzer angewendet werden und sich nicht von Benutzer zu Benutzer unterscheiden. Weitere Informationen finden Sie im Abschnitt zur Richtlinie „Sicherheitszonen: Benutzer können keine Einstellungen ändern“.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer locked down local machine zone java permissions** (Java-Berechtigungen für gesperrte Zonen mit lokalen Computern in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Standard**: Java deaktivieren 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**  (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode** (Mit Authenticode signierte .NET Framework-Komponenten in der eingeschränkten Zone von Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob .NET Framework-Komponenten, die mit Authenticode signiert wurden, von Internet Explorer ausgeführt werden können. Dazu zählen verwaltete Steuerelemente, auf die über Objekttags verwiesen wird, sowie verwaltete ausführbare Dateien, auf die über einen Link verwiesen wird. Wenn Sie diese Richtlinieneinstellung aktivieren, führt Internet Explorer signierte verwaltete Komponenten aus. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, fordert Internet Explorer den Benutzer dazu auf, zu entscheiden, ob signierte verwaltete Komponenten ausgeführt werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, führt Internet Explorer signierte verwaltete Komponenten nicht aus.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer restricted zone access to data sources** (Zugriff auf Datenquellen in eingeschränkten Zonen in Internet Explorer)  
  Durch diese Richtlinieneinstellung können Sie festlegen, ob Internet Explorer mithilfe von Microsoft XML Parser (MSXML) oder ActiveX Data Objects (ADO) auf Daten aus anderen Sicherheitszonen zugreifen kann. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer eine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie im Dropdownfeld „Prompt“ (Bestätigen) auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob eine Seite in der Zone geladen werden soll, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer keine Seite in die Zone laden, die MSXML oder ADO verwendet, um auf Daten in einer anderen Site in der Zone zuzugreifen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Standard**: Deaktivieren 
  
- **Internet Explorer internet zone don't run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in Internetzonen in Internet Explorer ausführen)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob von Internet Explorer Antischadsoftwareprogramme für ActiveX-Steuerelemente ausgeführt werden, um zu überprüfen, ob sie sicher auf Seiten geladen werden können. Wenn Sie diese Richtlinieneinstellung aktivieren, prüft Internet Explorer nicht anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung deaktivieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, prüft Internet Explorer immer anhand des Antischadsoftwareprogramms, ob das Erstellen einer Instanz des ActiveX-Steuerelements sicher ist. Benutzer können diese Option über die Sicherheitseinstellungen von Internet Explorer aktivieren und deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone copy and paste via script** (Kopieren und Einfügen in einer Internetzone mithilfe eines Skripts in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, ob Skripts in einer angegebenen Region Zwischenablagevorgänge (z.B. Ausschneiden, Kopieren und Einfügen) durchführen dürfen. Wenn Sie diese Richtlinieneinstellung aktivieren, können Skripts Zwischenablagevorgänge durchführen. Wenn Sie „Bestätigen“ im Dropdownfeld auswählen, werden die Benutzer zur Bestätigung aufgefordert, ob Zwischenablagevorgänge ausgeführt werden dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Skripts keine Zwischenablagevorgänge durchführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Skripts Zwischenablagevorgänge durchführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer use Active X installer service** (ActiveX-Installationsdienst in Internet Explorer verwenden)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, wie ActiveX-Steuerelemente installiert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente nur installiert, wenn der ActiveX-Installationsdienst vorhanden ist und dafür konfiguriert wurde, die Installation von ActiveX-Steuerelementen zuzulassen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden ActiveX-Steuerelemente (einschließlich Benutzersteuerelemente) über den Standardinstallationsvorgang installiert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Standard**: Aktiviert  
  
- **Internet Explorer processes protection from zone elevation** (Schutz vor Erhöhung der Rechte von Prozessen für Zonen in Internet Explorer)  
  Internet Explorer wendet auf jede Website, die geöffnet wird, Einschränkungen an. Diese hängen vom Speicherort der Webseite ab (z.B. Internet, Intranet, lokaler Computer). Für Webseiten, die sich auf lokalen Computern befinden, gelten beispielsweise die niedrigsten Sicherheitseinschränkungen. Sie befinden sich in der Zone „Lokaler Computer“, sodass diese in der Regel das Primärziel von Angreifern darstellt. Wenn Sie diese Richtlinieneinstellung aktivieren, kann jede Zone gegen die Erhöhung der Rechte durch alle Prozesse geschützt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, ist kein Schutz vor Prozessen vorhanden, die nicht Internet Explorer oder die in der Prozessliste aufgeführten Prozesse darstellen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer internet zone download unsigned Active X controls**  (Herunterladen nicht signierter ActiveX-Steuerelemente in Internetzonen in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzer nicht signierte ActiveX-Steuerelemente aus der Zone herunterladen können. Insbesondere, wenn Code aus einer nicht vertrauenswürdigen Zone stammt, kann er potenziell schädlich sein. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer nicht signierte Steuerelemente ohne Benutzereingriff ausführen. Wenn Sie die Option „Bestätigen“ im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob die Ausführung von nicht signierten Steuerelementen zugelassen werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer nicht signierte Steuerelemente nicht ausführen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer nicht signierte Steuerelemente nicht ausführen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**  (Windows und Frames von verschiedenen Domänen öffnen – Internetzone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, wie Fenster und Frames geöffnet werden, und den Zugriff auf Anwendungen über verschiedene Domänen regeln. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer Fenster und Frames von anderen Domänen öffnen und auf Anwendungen von anderen Domänen zugreifen. Wenn Sie im Dropdownfeld „Bestätigen“ auswählen, werden Benutzer dazu aufgefordert, zu entscheiden, ob Fenster und Frames auf Anwendungen von anderen Domänen zugreifen dürfen. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer keine Fenster und Frames für den Zugriff auf Anwendungen von anderen Domänen öffnen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer Fenster und Frames von anderen Domänen öffnen und auf Anwendungen von anderen Domänen zugreifen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer internet zone updates to status bar via script** (Skriptgesteuerte Updates für die Statusleiste in der Internetzone von Internet Explorer)  
  Über diese Richtlinieneinstellung können Sie festlegen, ob die Statusleiste in der Zone durch Skripts aktualisiert werden darf. Wenn Sie diese Richtlinieneinstellung aktivieren, kann die Statusleiste durch Skripts aktualisiert werden. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, kann die Statusleiste nicht über Skripts aktualisiert werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone include local path when uploading files to server** (Informationen zu lokalen Pfaden beim Hochladen von Dateien auf Server einfügen – eingeschränkte Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie festlegen, ob Informationen zu lokalen Pfaden beim Hochladen einer Datei über ein HTML-Formular übermittelt werden. Wenn die Informationen zu lokalen Pfaden übermittelt werden, kann es vorkommen, dass einige davon versehentlich für den Server offengelegt werden. Dabei kann es sich beispielsweise um Dateien vom Desktop des Benutzers handeln, die den Benutzernamen im Pfad enthalten. Wenn Sie diese Richtlinieneinstellung aktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular entfernt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer entscheiden, ob Pfadinformationen beim Hochladen einer Datei über ein HTML-Formular übermittelt werden sollen. Die Pfadinformationen werden standardmäßig gesendet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer processes restrict file download**  (Dateidownloads für Prozesse in Internet Explorer einschränken)  
  Diese Richtlinieneinstellung ermöglicht es Anwendungen, die das WebBrowser-Steuerelement hosten, die automatische Eingabeaufforderung für nicht vom Benutzer initiierte Dateidownloads zu blockieren. Wenn Sie diese Richtlinieneinstellung aktivieren, blockiert das WebBrowser-Steuerelement die automatische Eingabeaufforderung für nicht vom Benutzer initiierte Dateidownloads für alle Prozesse. Wenn Sie diese Richtlinieneinstellung deaktivieren, blockiert das WebBrowser-Steuerelement die automatische Eingabeaufforderung für nicht vom Benutzer initiierte Dateidownloads für alle Prozesse nicht.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**  (Nur genehmigte Domänen können das ActiveX-Steuerelement in eingeschränkten Zonen in Internet Explorer verwenden)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer dazu aufgefordert werden, zuzulassen, dass ActiveX-Steuerelemente auf Websites ausgeführt werden, die nicht die Website sind, auf der das ActiveX-Steuerelement installiert wurde. Wenn Sie diese Richtlinieneinstellung aktivieren, werden Benutzer zur Bestätigung aufgefordert, bevor die ActiveX-Steuerelemente von Websites in dieser Zone ausgeführt werden können. Der Benutzer kann die Ausführung des Steuerelements wahlweise für die aktuelle Website oder für alle Websites zulassen. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden die Benutzer nicht pro Website zum Zulassen von ActiveX aufgefordert, und ActiveX-Steuerelemente dürfen für alle Websites in dieser Zone ausgeführt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe** (ActiveX-Steuerelemente in eingeschränkten Zonen in Internet Explorer initialisieren und ausführen, die als unsicher gekennzeichnet sind)  
  Mit dieser Richtlinieneinstellung können Sie ActiveX-Steuerelemente verwalten, die als unsicher gekennzeichnet sind. Wenn Sie diese Richtlinieneinstellung aktivieren, werden ActiveX-Steuerelemente ausgeführt und mit Parametern geladen, und das Skript wird ohne Festlegen der Objektsicherheit für nicht vertrauenswürdige Daten oder Skripts erstellt. Von dieser Einstellung wird abgeraten, es sei denn, es handelt sich um sichere und verwaltete Zonen. Mit dieser Einstellung werden sowohl unsichere als auch sichere Steuerelemente initialisiert und Skripte für diese erstellt, ohne dabei die Option „ActiveX-Steuerelemente ausführen, die für Skripting sicher sind“ zu beachten. Wenn Sie diese Richtlinieneinstellung aktivieren und die Option „Prompt“ (Bestätigen) im Dropdownfeld auswählen, werden Benutzer dazu aufgefordert, auszuwählen, ob das Steuerelement mit Parametern geladen oder ein Skript erstellt werden soll. Wenn Sie diese Richtlinieneinstellung deaktivieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden ActiveX-Steuerelemente, die nicht als sicher gekennzeichnet werden können, nicht geladen, und es wird kein Skript erstellt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Standard**: Deaktivieren  
  
- **Internet Explorer users changing policies** (Ändern von Einstellungen durch Benutzer in Internet Explorer)  
  Durch diese Einstellung wird verhindert, dass Benutzer die Einstellungen für Sicherheitszonen ändern können. Bei einer Sicherheitszone handelt es sich um Websites, die die gleiche Sicherheitsstufe aufweisen. Wenn Sie diese Richtlinie aktivieren, werden die Schaltfläche „Custom Level“ (Stufe anpassen) und der Schieberegler „Sicherheitsstufe“ auf der Registerkarte „Sicherheit“ im Dialogfeld „Internetoptionen“ deaktiviert. Wenn Sie diese Richtlinie deaktivieren oder nicht konfigurieren, können Benutzer die Einstellungen für Sicherheitszonen bearbeiten. Durch diese Richtlinie wird verhindert, dass Benutzer die Einstellungen für Sicherheitszonen ändern, die vom Administrator eingerichtet wurden. Hinweis: Die Richtlinie „Sicherheitsseite deaktivieren“ (unter \Benutzerkonfiguration\Administrative Vorlagen\Windows-Komponenten\Internet Explorer\Internetsystemsteuerung) entfernt die Registerkarte „Sicherheit“ aus Internet Explorer in der Systemsteuerung und hat somit Vorrang vor dieser Richtlinie. Ist sie aktiviert, wird diese Richtlinie ignoriert. Weitere Informationen finden Sie im Abschnitt zur Richtlinie „Sicherheitszonen: Nur Computereinstellungen verwenden“.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone protected mode** (Popupblocker in der eingeschränkten Zone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie den geschützten Modus aktivieren. Im geschützten Modus wird Internet Explorer vor der Ausnutzung von Schwachstellen geschützt. Hierbei wird die Anzahl der Speicherorte in der Registrierung und im Dateisystem verringert, in die Internet Explorer schreiben kann. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der geschützte Modus aktiviert. Benutzer können den geschützten Modus nicht deaktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der geschützte Modus deaktiviert. Benutzer können den geschützten Modus nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer den geschützten Modus aktivieren oder deaktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Standard**: Aktivieren  
  
- **Internet Explorer internet zone user data persistence** (Speichern von Benutzerdaten in der Internetzone von Internet Explorer)  
  Über diese Richtlinieneinstellung können Sie die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite regeln. Wenn ein Benutzer eine gespeicherte Seite erneut besucht, kann der Zustand der Seite wiederhergestellt werden, wenn Sie diese Richtlinieneinstellung entsprechend konfiguriert haben. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite aktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite aktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer internet zone scripting of web browser controls** (Anwenden von Skripts auf WebBrowser-Steuerelemente in der Internetzone von Internet Explorer)  
 
  Diese Richtlinieneinstellung bestimmt, ob eine Seite eingebettete WebBrowser-Steuerelemente per Skript steuern kann. Wenn Sie diese Richtlinieneinstellung aktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement möglich. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist der Skriptzugriff auf das WebBrowser-Steuerelement nicht möglich. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, kann der Benutzer den Skriptzugriff auf das WebBrowser-Steuerelement aktivieren oder deaktivieren. Standardmäßig ist der Skriptzugriff auf das WebBrowser-Steuerelement nur auf dem lokalen Computer und in Intranetzonen möglich.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone user data persistence** (Speichern von Benutzerdaten in der eingeschränkten Zone von Internet Explorer)  
  Über diese Richtlinieneinstellung können Sie die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite regeln. Wenn ein Benutzer eine gespeicherte Seite erneut besucht, kann der Zustand der Seite wiederhergestellt werden, wenn Sie diese Richtlinieneinstellung entsprechend konfiguriert haben. Wenn Sie diese Richtlinieneinstellung aktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite aktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite nicht aktivieren. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Benutzer die Speicherung von Informationen im Verlauf, in den Favoriten und im XML-Speicher des Browsers bzw. in einer auf einem Datenträger gespeicherten Webseite nicht aktivieren.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer locked down intranet zone java permissions** (Java-Berechtigungen für die gesperrte Intranetzone von Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie Berechtigungen für Java-Applets verwalten. Durch das Aktivieren dieser Richtlinieneinstellung können Sie Optionen aus dem Dropdownfeld auswählen. Wählen Sie „Benutzerdefiniert“ aus, um Berechtigungseinstellungen einzeln zu bestimmen. Wählen Sie „Niedrige Sicherheit“ aus, um Applets die Ausführung aller Vorgänge zu ermöglichen. Wählen Sie „Mittlere Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox (ein Bereich im Speicher, außerhalb dessen das Programm keine Aufrufe ausführen kann) sowie Funktionen wie den sicheren Speicherbereich (ein geschützter und sicherer Speicherbereich auf dem Clientcomputer) und die benutzergesteuerte Datei-E/A zu ermöglichen. Wählen Sie „Hohe Sicherheit“ aus, um Applets die Ausführung in der zugehörigen Sandbox zu ermöglichen. Deaktivieren Sie Java, um zu verhindern, dass Applets ausgeführt werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Java-Applets nicht ausgeführt werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, sind Java-Applets deaktiviert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Standard**: Java deaktivieren  
  
- **Internet Explorer enhanced protected mode** (Erweiterter geschützter Modus in Internet Explorer)  
  Der erweiterte geschützte Modus bietet einen zusätzlichen Schutz gegen Websites mit Schadsoftware, indem er bei 64-Bit-Versionen von Windows 64-Bit-Prozesse verwendet. Bei Computern mit Windows 8 oder höher beschränkt der erweiterte geschützte Modus außerdem die Speicherorte von Internet Explorer in der Registrierung und im Dateisystem. Wenn Sie diese Richtlinieneinstellung aktivieren, wird der erweiterte geschützte Modus aktiviert. In allen Zonen mit aktiviertem geschützten Modus wird der erweiterte geschützte Modus verwendet. Die Benutzer können den erweiterten geschützten Modus nicht deaktivieren. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der erweiterte geschützte Modus deaktiviert. In allen Zonen mit aktiviertem geschützten Modus wird die Version des geschützten Modus verwendet, die mit Internet Explorer 7 für Windows Vista eingeführt wurde. Wenn Sie diese Richtlinie nicht konfigurieren, können die Benutzer den erweiterten geschützten Modus über die Registerkarte „Erweitert“ im Dialogfeld „Internetoptionen“ ein oder ausschalten.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Standard**: Aktiviert  
  
- **Internet Explorer bypass smart screen warnings** (SmartScreen-Warnungen in Internet Explorer umgehen)  
  Mit dieser Richtlinieneinstellung wird bestimmt, ob Benutzer Warnungen des SmartScreen-Filters umgehen können. Der SmartScreen-Filter warnt Benutzer vor ausführbaren Dateien im Internet, die selten von Benutzern heruntergeladen werden. Wenn Sie diese Richtlinieneinstellung aktivieren, hindern die Warnungen des SmartScreen-Filters Benutzer am Herunterladen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, können Benutzer die Warnungen des SmartScreen-Filters umgehen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Standard**: Deaktiviert  
  
- **Internet Explorer restricted zone meta refresh** (Meta Refresh-Tag in einer eingeschränkten Zone in Internet Explorer)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Benutzerbrowser auf eine andere Webseite umgeleitet werden können, wenn der Autor der Webseite die Einstellung „Meta Refresh“ (Tag) verwendet, um Browser auf eine andere Webseite umzuleiten. Wenn Sie diese Richtlinieneinstellung aktivieren, können Browser, die eine Seite mit einer aktiven Meta Refresh-Einstellung laden, auf andere Webseiten umgeleitet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Browser, die eine Seite mit einer aktiven Meta Refresh-Einstellung laden, nicht auf andere Webseiten umgeleitet werden. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, können Browser, die eine Seite mit einer aktiven Meta Refresh-Einstellung laden, nicht auf andere Webseiten umgeleitet werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Standard**: Deaktiviert  
  
## <a name="local-policies-security-options"></a>Sicherheitsoptionen für lokale Richtlinien
Weitere Informationen finden Sie unter [Policy CSP – LocalPoliciesSecurityOptions (Richtlinien-Konfigurationsdienstanbieter: LocalPoliciesSecurityOptions)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in der Windows-Dokumentation. 

- **Restrict anonymous access to named pipes and shares** (Anonymen Zugriff auf Named Pipes und Freigaben einschränken)  
  Wenn diese Sicherheitseinstellung aktiviert ist, wird der anonyme Zugriff auf Freigaben und Pipes für folgende Einstellungen eingeschränkt: (1) Named Pipes, auf die anonym zugegriffen werden kann; (2) Freigaben, auf die anonym zugegriffen werden kann  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Standard**: Ja  
  
- **Minimum session security for NTLM SSP based servers** (Minimale Sitzungssicherheit für NTLM-basierte SSP-Server)  
  Mit dieser Sicherheitseinstellung kann die Aushandlung der 128-Bit-Verschlüsselung und bzw. oder der NTLMv2-Sitzungssicherheit für einen Server als erforderlich festgelegt werden. Diese Werte hängen vom Wert des Sicherheitseinstellungswerts für die LAN Manager-Authentifizierungsebene ab. Die Optionen sind: „NTLMv2-Sitzungssicherheit erfordern: Die Verbindung schlägt fehl, wenn die Nachrichtenintegrität nicht ausgehandelt wird“. 128-Bit-Verschlüsselung erfordern: Die Verbindung schlägt fehl, wenn die keine starke Verschlüsselung (128-Bit) ausgehandelt wird.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Standard**: NTLMv2- und 128-Bit-Verschlüsselung verlangen  
  
- **Minutes of lock screen inactivity until screen saver activates** (Inaktivität in Minuten für Anmeldebildschirm bis zur Aktivierung des Bildschirmschoners)  
  Windows bemerkt die Inaktivität einer Anmeldesitzung, führt den Bildschirmschoner aus und sperrt die Sitzung, wenn der Zeitraum der Inaktivität die jeweilige Obergrenze überschreitet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Standard**: 15
  
- **Require client to always digitally sign communications** (Digitale Signierung der Kommunikation immer vom Client erfordern) Diese Sicherheitseinstellung bestimmt, ob von Domänenmitgliedern gestarteter Datenverkehr über den sicheren Kanal signiert oder verschlüsselt sein muss. Wenn ein Computer einer Domäne beitritt, wird ein Computerkonto erstellt. Daraufhin wird das Kennwort des Computerkontos beim Starten des Systems zum Erstellen eines sicheren Kanals mit einem Domänencontroller als Domäne verwendet. Dieser sichere Kanal wird verwendet, um Vorgänge wie die NTLM-Pass-Through-Authentifizierung, LSA SID/Namenlookups usw. durchzuführen. Diese Einstellung bestimmt, ob jeglicher Datenverkehr über den sicheren Kanal, der von Domänenmitgliedern gestartet wird, den Mindestanforderungen für die Sicherheit entspricht. Insbesondere bestimmt sie, ob von Domänenmitgliedern gestarteter Datenverkehr über den sicheren Kanal signiert oder verschlüsselt sein muss. Wenn diese Richtlinie aktiviert ist, wird der sichere Kanal nicht erstellt, es sei denn, die Signierung oder Verschlüsselung des gesamten Datenverkehrs über den sicheren Kanal wird ausgehandelt. Wenn diese Richtlinie deaktiviert ist, wird die Verschlüsselung und Signierung des gesamten Datenverkehrs über den sicheren Kanal mit dem Domänencontroller ausgehandelt. In diesem Fall sind die Signierung und Verschlüsselung von der Version des Domänencontrollers und den Einstellungen der beiden folgenden Richtlinien abhängig: „Domänenmitglied: Daten des sicheren Kanals digital verschlüsseln (wenn möglich)“; „Domänenmitglied: Daten des sicheren Kanals digital signieren (wenn möglich)“.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Standard**: Ja
  
- **Authentifizierungsebene**  
  Mit dieser Sicherheitseinstellung wird festgelegt, welches Abfrage/Antwort-Authentifizierungsprotokoll für Netzwerkanmeldungen verwendet wird. Diese Auswahl wirkt sich wie folgt auf das von Clients verwendete Authentifizierungsprotokoll, die ausgehandelte Sitzungssicherheit und die von Servern akzeptierte Authentifizierung aus:  
  - *LM- und NTLM-Antworten senden*: Clients verwenden die NTLM-Authentifizierung und nie die NTLMv2-Sitzungssicherheit. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Send LM and NTLM - NTLMv2 if negotiated* (LM- und NTLM-Antworten senden – NTLMv2, wenn ausgehandelt): Clients verwenden die LM- und NTLM-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Nur NTLM-Antworten senden*: Clients verwenden ausschließlich die NTLM-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Nur NTLMv2-Antworten senden*: Clients verwenden ausschließlich die NTLMv2-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller akzeptieren die LM-, NTLM- und NTLMv2-Authentifizierungen. 
  - *Nur NTLMv2-Antworten senden. LM ablehnen*: Clients verwenden ausschließlich die NTLMv2-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller lehnen die LM-Authentifizierung ab (sie akzeptieren nur die NTLM- und NTLMv2-Authentifizierungen). 
  - *Nur NTLMv2-Antworten senden. LM und NTLM ablehnen*: Clients verwenden ausschließlich die NTLMv2-Authentifizierung sowie die NTLMv2-Sitzungssicherheit, wenn der Server diese unterstützt. Domänencontroller lehnen die LM- und NTLM-Authentifizierung ab (sie akzeptieren nur die NTLMv2-Authentifizierung).  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Standard**: Nur NTLMv2-Antworten senden. LM und NTLM ablehnen.
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers** (Senden von unverschlüsselten Kennwörtern von Clients an SMB-Server von Drittanbietern verhindern)  
  Wenn diese Sicherheitseinstellung aktiviert ist, darf der SMB-Redirector (Server Message Block) Klartextkennwörter an Nicht-Microsoft-SMB-Server senden, die keine Kennwortverschlüsselung während der Authentifizierung unterstützen. Das Senden unverschlüsselter Kennwörter ist ein Sicherheitsrisiko.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Standard**: Ja
  
- **Require server digitally signing communications always** (Digitale Signierung durch Server für die Kommunikation immer erforderlich)  
  Mit dieser Sicherheitseinstellung wird festgelegt, ob der SMB-Client versucht, die SMB-Paketsignierung auszuhandeln. Das SMB-Protokoll (Server Message Block) stellt die Grundlage für Microsoft-Dateien und die Druckfreigabe sowie viele andere Netzwerkvorgänge, z.B. die Windows-Remoteverwaltung. Das SMB-Protokoll unterstützt das digitale Signieren von SMB-Paketen, um Man-in-the-Middle-Angriffe zu vermeiden, die SMB-Pakete während der Übermittlung ändern. Mit dieser Richtlinieneinstellung wird festgelegt, ob die SMB-Clientkomponente versucht, die Signierung von SMB-Paketen auszuhandeln, wenn eine Verbindung mit einem SMB-Server hergestellt wird. Wenn diese Einstellung aktiviert wird, fordert der Microsoft-Netzwerkclient den Server dazu auf, die SMB-Paketsignatur bei der Einrichtung der Sitzung durchzuführen. Wenn die Paketsignatur auf dem Server aktiviert wurde, wird die Paketsignatur ausgehandelt. Wenn diese Richtlinie deaktiviert ist, handelt der SMB-Client nie die SMB-Paketsignatur aus.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Standard**: Ja
  
- **Administrator elevation prompt behavior** (Verhalten für Administratoren bei der Eingabeaufforderung für erhöhte Rechte)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Administratoren bestimmen. Folgende Optionen sind verfügbar: 
  - *Erhöhte Rechte ohne Eingabeaufforderung*: Ermöglicht mit Rechten versehenen Konten das Ausführen eines Vorgangs, für den erhöhte Rechte erforderlich sind, ohne dass dafür Zustimmung oder Anmeldeinformationen erforderlich sind. Hinweis: Verwenden Sie diese Option nur in Umgebungen, die besonders starken Beschränkungen unterliegen. 
  - *Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop zur Eingabe eines entsprechenden Benutzernamens und Kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt. 
  - *Eingabeaufforderung zur Zustimmung auf dem sicheren Desktop*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop zur Auswahl von „Zulassen“ oder „Verweigern“ aufgefordert. Wenn der Benutzer „Zulassen“ auswählt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt. 
  - *Eingabeaufforderung zu Anmeldeinformationen*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer zur Eingabe eines Administratorbenutzernamens und -kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt. 
  - *Eingabeaufforderung zur Zustimmung*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wählen Sie entweder „Zulassen“ oder „Verweigern“ aus. Wenn der Benutzer „Zulassen“ auswählt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt.  
  - *Eingabeaufforderung zur Zustimmung für Nicht-Windows-Binärdateien*: Wenn für einen Vorgang für eine nicht von Microsoft stammende Anwendung erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop aufgefordert, entweder „Zulassen“ oder „Verweigern“ auszuwählen. Wenn der Benutzer „Zulassen“ auswählt, wird der Vorgang mit dem höchsten verfügbaren Recht des Benutzers fortgesetzt. 
  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Standard**: Zustimmungsaufforderung für sicheren Desktop
  
- **Minimum session security for NTLM SSP based clients** (Minimale Sitzungssicherheit für NTLM-basierte SSP-Clients)  
  Mit dieser Sicherheitseinstellung kann die Aushandlung der 128-Bit-Verschlüsselung und bzw. oder der NTLMv2-Sitzungssicherheit für einen Client als erforderlich festgelegt werden. Diese Werte hängen vom Wert des Sicherheitseinstellungswerts für die LAN Manager-Authentifizierungsebene ab. Folgende Optionen sind verfügbar:
  - *NTLMv2-Sitzungssicherheit erfordern*: Die Verbindung schlägt fehl, wenn das NTLMv2-Protokoll nicht ausgehandelt wird. 
  - *128-Bit-Verschlüsselung erfordern*: Die Verbindung schlägt fehl, wenn keine starke Verschlüsselung (128-Bit) ausgehandelt wird.
  - *NTLMv2- und 128-Bit-Verschlüsselung erfordern*.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Standard**: NTLMv2- und 128-Bit-Verschlüsselung erfordern
  
- **Smart card removal behavior** (Verhalten beim Entfernen von Smartcards)  
  Diese Sicherheitseinstellung legt fest, was geschieht, wenn die Smartcard für einen angemeldeten Benutzer aus dem Smartcardleser entfernt wird. Folgende Optionen sind verfügbar:
  - *Keine Aktion*. 
  - *Arbeitsstation sperren* – Die Arbeitsstation wird beim Entfernen der Smartcard gesperrt, sodass Benutzer den Arbeitsbereich verlassen, die Smartcard mitnehmen und dennoch eine geschützte Sitzung aufrechterhalten können.
  - *Abmeldung erzwingen*: Der Benutzer wird automatisch abgemeldet, wenn die Smartcard entfernt wird.
  - *Disconnect Remote Desktop session* (Remotedesktopsitzung beenden): Das Entfernen der Smartcard beendet die Sitzung, ohne den Benutzer abzumelden. Dies ermöglicht es Benutzern, die Smartcard einzulegen und die Sitzung später oder auf einem anderen Computer mit Smartcard-Leser fortzusetzen, ohne sich erneut anmelden zu müssen. Wenn die Sitzung lokal stattfindet, funktioniert diese Richtlinie genau wie „Arbeitsstation sperren“.
  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Standard**: Arbeitsstation sperren
  
- **Block anonymous enumeration of SAM accounts and shares** (Anonyme Aufzählung von SAM-Konten und Freigaben blockieren)  
  Diese Sicherheitseinstellung legt fest, ob die anonyme Aufzählung von SAM-Konten und Freigaben zugelassen wird. Windows erlaubt anonymen Benutzern bestimmte Aktionen, z.B. das Aufzählen der Namen von Domänenkonten und Netzwerkfreigaben. Das kann z. B. besonders nützlich sein, wenn ein Administrator Benutzern in einer vertrauenswürdigen Domäne Zugriffsberechtigungen gewähren möchte, die diese Vertrauensstellung nicht erwidert. Wenn Sie die anonyme Aufzählung von SAM-Konten und Freigaben nicht zulassen möchten, legen Sie für diese Richtlinie *Ja* fest.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Standard**: Ja
  
- **Block remote logon with blank password** (Remoteanmeldung mit leerem Kennwort blockieren)  
  Diese Sicherheitseinstellung legt fest, ob lokale Konten, die nicht kennwortgeschützt sind, zum Anmelden an anderen Orten als der Konsole des physischen Computers verwendet werden können. Wenn diese Einstellung aktiviert ist, können lokale Konten ohne Kennwortschutz nur über die Computertastatur angemeldet werden. 

  *Warnung*: Für Computer, die sich nicht an physisch sicheren Orten befinden, sollten immer strikte Kennwortrichtlinien für alle Benutzerkonten verwendet werden. Ansonsten kann sich jeder mit physischem Zugang zu dem Computer mit einem Benutzerkonto ohne Kennwort anmelden. Dies gilt besonders für tragbare Computer. 

  Wenn Sie diese Sicherheitsrichtlinie auf die Gruppe „Alle“ anwenden, kann sich niemand über Remotedesktopdienste anmelden. Diese Einstellung wirkt sich nicht auf Anmeldungen mit Domänenkonten aus. Anwendungen mit interaktiven Remoteanmeldungen können diese Einstellung umgehen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Standard**: Ja
  
- **Standard user elevation prompt behavior** (Verhalten für Standardbenutzer bei der Eingabeaufforderung für erhöhte Rechte)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten der Eingabeaufforderung für erhöhte Rechte für Standardbenutzer bestimmen. 
  - *Anforderungen für erhöhte Rechte automatisch ablehnen*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird eine konfigurierbare Fehlermeldung für verweigerten Zugriff angezeigt. Ein Unternehmen, in dem Desktops mit Standardbenutzerrechten ausgeführt werden, kann diese Einstellung auswählen, um die Anzahl der Anrufe beim Helpdesk zu verringern. 
  - *Eingabeaufforderung zu Anmeldeinformationen auf dem sicheren Desktop*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer auf dem sicheren Desktop zur Eingabe eines anderen Benutzernamens und Kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt. 
  - *Eingabeaufforderung zu Anmeldeinformationen*: Wenn für einen Vorgang erhöhte Rechte erforderlich sind, wird der Benutzer zur Eingabe eines Administratorbenutzernamens und -kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Standard**: Anforderungen für erhöhte Rechte automatisch ablehnen
  
- **Require admin approval mode for administrators** (Administratorgenehmigungsmodus für Administratoren erfordern)  
  Mit dieser Richtlinieneinstellung wird das Verhalten aller UAC-Richtlinieneinstellungen (User Account Control, Benutzerkontensteuerung) für den Computer bestimmt. Wenn Sie diese Richtlinieneinstellung ändern, muss der Computer neu gestartet werden. Folgende Optionen sind verfügbar:   
  - *Nicht konfiguriert*: Der Administratorgenehmigungsmodus und alle verwandten UAC-Richtlinieneinstellungen sind deaktiviert. Hinweis: Wenn diese Richtlinieneinstellung deaktiviert ist, werden Sie vom Sicherheitscenter benachrichtigt, dass die allgemeine Sicherheit des Betriebssystems eingeschränkt ist. 
  - *Ja*: Der Administratorgenehmigungsmodus ist aktiviert. Diese Richtlinieneinstellung muss aktiviert und verwandte UAC-Richtlinieneinstellungen müssen entsprechend festgelegt werden, damit das integrierte Administratorkonto und alle anderen Benutzerkonten, die Mitglieder der Administratorgruppe sind, im Administratorgenehmigungsmodus ausgeführt werden können.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Standard**: Ja
  
- **Prevent anonymous enumeration of SAM accounts** (Anonyme Enumerationen von SAM-Konten verhindern)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, welche zusätzlichen Berechtigungen für anonyme Verbindungen mit dem Computer gewährt werden. Windows erlaubt anonymen Benutzern bestimmte Aktionen, z.B. das Aufzählen der Namen von Domänenkonten und Netzwerkfreigaben. Das kann z. B. besonders nützlich sein, wenn ein Administrator Benutzern in einer vertrauenswürdigen Domäne Zugriffsberechtigungen gewähren möchte, die diese Vertrauensstellung nicht erwidert. Mit dieser Sicherheitseinstellung können die folgenden zusätzlichen Einschränkungen für anonyme Verbindungen vorgenommen werden: 
  - *Ja*: Enumeration von SAM-Konten nicht zulassen. Diese Option ersetzt die Option „Everyone with Authenticated Users“ (Jeder mit authentifizierten Benutzern) in den Sicherheitsberechtigungen für Ressourcen.
  - *Nicht konfiguriert*: Keine zusätzlichen Einschränkungen. Es gelten die Standardberechtigungen.  
  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Standard**: Ja
  
- **Allow remote calls to security accounts manager** (Remoteaufrufe vom Sicherheitskonto-Manager zulassen)  
  Mit dieser Richtlinieneinstellung können Sie RPC-Verbindungen mit dem SAM einschränken. Wenn diese Einstellung nicht festgelegt wurde, wird die Standardsicherheitsbeschreibung verwendet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Standard**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode** (Administratorgenehmigungsmodus verwenden)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten des Administratorgenehmigungsmodus für das integriertes Administratorkonto bestimmen. Folgende Optionen sind verfügbar: 
  - *Ja*: Für das integrierte Administratorkonto wird der Administratorgenehmigungsmodus verwendet. Standardmäßig wird der Benutzer bei jedem Vorgang, der die Höherstufung von Rechten erfordert, zur Genehmigung aufgefordert. 
  - *Nicht konfiguriert*: Mit dem integrierten Administratorkonto werden alle Anwendungen mit vollständigen Administratorrechten ausgeführt. 

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Standard**: Ja
  
- **Allow UI access applications for secure locations** (Anwendungen für Benutzeroberflächenbedienungshilfe für sichere Standorte zulassen)  
  Mit dieser Sicherheitseinstellung können Sie bestimmen, ob Programme für Bedienungshilfen für die Benutzeroberfläche (UIAccess oder UIA) automatisch den sicheren Desktop für Eingabeaufforderungen mit erhöhten Rechten eines Standardbenutzers deaktivieren kann. 
  - *Ja*: UIA-Programme, darunter Windows-Remoteunterstützung, deaktivieren automatisch den sicheren Desktop für Eingabeaufforderungen für erhöhte Rechte. Wenn die Richtlinieneinstellung „Benutzerkontensteuerung: Bei Benutzeraufforderung nach erhöhten Rechten zum sicheren Desktop wechseln“ nicht deaktiviert wird, werden die Eingabeaufforderungen auf dem Desktop des interaktiven Benutzers und nicht auf dem sicheren Desktop angezeigt. 
  - *Nicht konfiguriert*: Der sichere Desktop kann nur vom Benutzer des interaktiven Desktops oder durch Deaktivieren der Richtlinieneinstellung „Benutzerkontensteuerung: Bei Benutzeraufforderung nach erhöhten Rechten zum sicheren Desktop wechseln“ deaktiviert werden.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Standard**: Ja

- **Detect application installations and prompt for elevation** (Anwendungsinstallationen erkennen und erhöhte Rechte anfordern)  
  Mit dieser Richtlinieneinstellung können Sie das Verhalten bei der Erkennung einer Anwendungsinstallation auf dem Computer bestimmen. Folgende Optionen sind verfügbar: 
  - *Aktiviert*: Wenn ein Anwendungsinstallationspaket erkannt wird, das erhöhte Rechte erfordert, wird der Benutzer zur Eingabe eines Administratorbenutzernamens und -kennworts aufgefordert. Wenn der Benutzer gültige Anmeldeinformationen eingibt, wird der Vorgang mit dem entsprechenden Recht fortgesetzt. 
  - *Deaktiviert*: Anwendungsinstallationspakete werden nicht erkannt, und es wird keine Eingabeaufforderung für erhöhte Rechte angezeigt. Unternehmen, die Standardbenutzerdesktops und delegierte Installationstechnologien wie Gruppenrichtlinien-Softwareinstallation oder Systems Management Server (SMS) verwenden, sollten diese Richtlinieneinstellung deaktivieren. In diesem Fall ist keine Installationserkennung erforderlich.  
  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Standard**: Ja
  
- **Prevent storing LAN manager hash value on next password change** (Speicher des Hashwerts des LAN-Managers bei der nächsten Kennwortänderung verhindern)  
  Mit dieser Sicherheitseinstellung können Sie bestimmen, ob der Hashwert des LAN-Managers (LM) bei der nächsten Kennwortänderung für das neue Kennwort gespeichert werden soll. Der LM-Hashwert ist im Vergleich zum kryptografisch stärkeren Windows NT-Hashwert relativ schwach und angreifbar. Da der LM-Hashwert auf dem lokalen Computer in der Sicherheitsdatenbank gespeichert wird, können die Kennwörter gefährdet sein, wenn die Sicherheitsdatenbank angegriffen wird.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Standard**: Ja

- **Virtualize file and registry write failures to per user locations** (Fehler bei Schreibvorgängen für Dateien und Registrierung pro Benutzer virtualisieren)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob Fehler bei Anwendungsschreibvorgängen an definierte Registrierungs- und Dateisystemspeicherorte weitergeleitet werden. Mit dieser Richtlinieneinstellung werden Anwendungen, die mit Administratorrechten ausgeführt werden und die Laufzeitanwendungsdaten schreiben, zum folgenden Verzeichnis migriert: *%Programme%* , *%Windir%* , *%Windir%\system32* oder *HKLM\Software*.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Standard**: Ja

## <a name="ms-security-guide"></a>MSSecurityGuide  
Weitere Informationen finden Sie unter [Policy CSP - MSSecurityGuide (Richtlinien-CSP: MSSecurityGuide)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in der Windows-Dokumentation.  

- **Apply UAC restrictions to local accounts on network logon** (UAC-Einschränkungen auf lokale Konten bei der Netzwerkanmeldung anwenden)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Standard**: Aktiviert
  
- **SMB v1 client driver start configuration** (Startkonfiguration den SMB v1-Clienttreibers)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Standard**: Treiber deaktiviert
  
- **SMB v1 server** (SMB v1-Server)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Standard**: Deaktiviert
  
- **Digest authentication** (Digestauthentifizierung)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Standard**: Deaktiviert
  
- **Structured exception handling overwrite protection** (Überschreibungsschutz bei der Behandlung strukturierter Ausnahmen)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Standard**: Aktiviert
  
## <a name="mss-legacy"></a>MSS Legacy  
Weitere Informationen finden Sie unter [Policy CSP - MSSLegacy (Richtlinen-CSP: MSSLegacy)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in der Windows-Dokumentation.  

- **Network IP source routing protection level** (Schutzebene für das Quellrouting von Netzwerk-IP-Adressen)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Standard**: Höchster Schutz  
  
- **Network ignore NetBIOS name release requests except from WINS servers** (Das Netzwerk ignoriert Namensanforderungen von NetBIOS, es sei denn, sie stammen von WINS-Servern)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Standard**: Aktiviert
  
- **Network IPv6 source routing protection level** (Schutzebene für das Quellrouting von Netzwerk-IPv6-Adressen)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Standard**: Höchster Schutz

- **Network ICMP redirects to override OSPF generated routes** (Umleitungen durch das Netzwerk-ICMP zum Überschreiben von Routen, die vom OSPF generiert wurden)  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Standard**: Deaktiviert
  
## <a name="power"></a>Power  
Weitere Informationen finden Sie unter [Policy CSP - Power (Richtlinien-CSP: Power)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in der Windows-Dokumentation.  

- **Require password on wake while plugged in** (Kennwort bei Reaktivierung im Netzbetrieb anfordern)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Benutzer zur Eingabe eines Kennworts aufgefordert wird, wenn das System aus dem Energiesparmodus reaktiviert wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, wird der Benutzer beim Verlassen des Energiesparmodus zur Eingabe eines Kennworts aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der Benutzer beim Verlassen des Energiesparmodus nicht zur Eingabe eines Kennworts aufgefordert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Standard**: Aktiviert
  
- **Standby states when sleeping while on battery** (Standbyzustände im Energiesparmodus im Akkubetrieb)  
  Diese Richtlinieneinstellung legt fest, ob Windows Standbyzustände verwenden kann, wenn der Computer in den Energiesparmodus versetzt wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, verwendet Windows Standbyzustände, um den Computer in den Energiesparmodus zu versetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren, sind Standbyzustände (S1–S3) nicht zulässig.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Standard**: Deaktiviert
  
- **Standby states when sleeping while plugged in** (Standbyzustände im Energiesparmodus im Netzbetrieb)  
  Diese Richtlinieneinstellung legt fest, ob Windows Standbyzustände verwenden kann, wenn der Computer in den Energiesparmodus versetzt wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, verwendet Windows Standbyzustände, um den Computer in den Energiesparmodus zu versetzen. Wenn Sie diese Richtlinieneinstellung deaktivieren, sind Standbyzustände (S1–S3) nicht zulässig.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Standard**: Deaktiviert
  
- **Require password on wake while on battery** (Kennwort bei Reaktivierung im Akkubetrieb anfordern)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Benutzer zur Eingabe eines Kennworts aufgefordert wird, wenn das System aus dem Energiesparmodus reaktiviert wird. Wenn Sie diese Richtlinieneinstellung aktivieren oder nicht konfigurieren, wird der Benutzer beim Verlassen des Energiesparmodus zur Eingabe eines Kennworts aufgefordert. Wenn Sie diese Richtlinieneinstellung deaktivieren, wird der Benutzer beim Verlassen des Energiesparmodus nicht zur Eingabe eines Kennworts aufgefordert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Standard**: Aktiviert

## <a name="remote-assistance"></a>Remoteunterstützung
- **Remote Unterstützung angefordert**  
  Mit dieser Richtlinien Einstellung können Sie die angeforderte (Fragen) Remote Unterstützung auf diesem Computer aktivieren bzw. deaktivieren. 
  - *Wenn Sie diese Richtlinien Einstellung aktivieren*, können Benutzer auf diesem Computer per e-Mail oder über die Dateiübertragung Hilfe anfordern. Außerdem können Benutzer Instant Messaging-Programme verwenden, um Verbindungen mit diesem Computer zuzulassen, und Sie können zusätzliche Remote Unterstützungs Einstellungen konfigurieren. 
  - *Wenn Sie diese Richtlinien Einstellung deaktivieren*, können Benutzer auf diesem Computer keine e-Mail oder Dateiübertragung verwenden, um Hilfe zu bitten. Außerdem können Benutzer keine Instant Messaging-Programme verwenden, um Verbindungen mit diesem Computer zuzulassen. 
  - *Wenn Sie diese Richtlinien Einstellung nicht konfigurieren*, können Benutzer die angeforderte Remote Unterstützung selbst in den System Eigenschaften in der Systemsteuerung aktivieren bzw. deaktivieren. Benutzer können auch Remote Unterstützungs Einstellungen konfigurieren. 

  Wenn Sie diese Richtlinien Einstellung aktivieren, stehen Ihnen zwei Möglichkeiten zur Verfügung, die Bereitstellung von Remote Unterstützung durch Hilfsprogramme zuzulassen: "hilfsobjedansichten nur den Computer anzeigen" oder "Hilfsquellen die Remote Steuerung des Computers erlauben". Die Richtlinien Einstellung "maximale Ticket Zeit" legt fest, wie lange eine mit e-Mail oder Dateiübertragung erstellte Remote Unterstützungs Einladung geöffnet bleiben kann. Die Einstellung "Methode zum Senden von e-Mail-Einladungen auswählen" gibt an, welcher e-Mail-Standard zum Senden von Remote Unterstützungs Einladungen verwendet werden soll Abhängig von Ihrem e-Mail-Programm können Sie entweder den mailto-Standard verwenden (der Einladungs Empfänger stellt eine Verbindung über einen Internet Link her) oder den smapi-Standard (Simple MAPI) (die Einladung ist an Ihre e-Mail-Nachricht angefügt). Diese Richtlinien Einstellung ist in Windows Vista nicht verfügbar, da smapi die einzige unterstützte Methode ist. Wenn Sie diese Richtlinien Einstellung aktivieren, sollten Sie auch entsprechende Firewallausnahmen aktivieren, um die Kommunikation mit Remote Unterstützung zuzulassen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Standard**: Remote Unterstützung deaktivieren

  Wenn Sie aktivieren, um *Remote Unterstützung zu aktivieren*, konfigurieren Sie die folgenden zusätzlichen Einstellungen:  
  - **Berechtigung zur Remote Unterstützung angefordert**  
    **Standard**: Anzeigen  

  - **Maximaler Zeitwert des Tickets**  
    **Standard**: *Nicht konfiguriert*  

  - **Maximaler Ticketzeitraum**  
    **Standard**: Minuten    

  - **Einladungs Methode für E-Mail**  
    **Standard**: Simple MAPI

  
## <a name="remote-desktop-services"></a>Remotedesktopdienste  
Weitere Informationen finden Sie unter [Policy CSP – RemoteDesktopServices (Richtlinien-Konfigurationsdienstanbieter: RemoteDesktopServices)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in der Windows-Dokumentation.  

- **Block password saving** (Speichern von Kennwörtern blockieren)  
  Diese Richtlinieneinstellung steuert, ob Kennwörter auf diesem Computer über die Remotedesktopverbindung gespeichert werden können. Wenn Sie diese Einstellung aktivieren, wird das Kontrollkästchen für die Kennwortspeicherung in der Remotedesktopverbindung deaktiviert, und Benutzer können Kennwörter nicht mehr speichern. Wenn ein Benutzer eine RDP-Datei über die Remotedesktopverbindung öffnet und seine Einstellungen speichert, werden alle zuvor in der RDP-Datei vorhandenen Kennwörter gelöscht. Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, kann der Benutzer Kennwörter über die Remotedesktopverbindung speichern.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Standard**: Aktiviert
  
- **Secure RPC communication** (RPC-Kommunikation sichern)  
  Diese Richtlinieneinstellung legt fest, ob für einen Remotedesktopsitzungs-Hostserver die sichere RPC-Kommunikation mit allen Clients erforderlich bzw. ob die unsichere Kommunikation zulässig ist. Mit dieser Einstellung können Sie die Sicherheit der RPC-Kommunikation mit Clients verbessern, indem Sie nur authentifizierte und verschlüsselte Anforderungen zulassen. Wenn die Einstellung aktiviert ist, akzeptieren Remotedesktopdienste Anforderungen von RPC-Clients, die sichere Anforderungen unterstützen, und unterstützen keine unsichere Kommunikation mit nicht vertrauenswürdigen Clients. Wenn die Einstellung deaktiviert ist, muss der gesamte RPC-Datenverkehr für Remotedesktopdienste immer sicher sein. Für RPC-Clients, die nicht auf die Anforderung reagieren, ist jedoch eine unsichere Kommunikation zulässig. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, ist die unsichere Kommunikation zulässig. Hinweis: Die RPC-Schnittstelle wird zum Verwalten und Konfigurieren der Remotedesktopdienste verwendet.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Standard**: Aktiviert
  
- **Block drive redirection** (Laufwerkumleitung blockieren)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob die Zuordnung von Clientlaufwerken während einer Remotedesktopdienst-Sitzung (Laufwerkumleitung) verhindert werden soll. Remotedesktopdienst-Hostserver ordnen Clientlaufwerke standardmäßig beim Herstellen der Verbindung automatisch zu. Zugeordnete Laufwerke werden in der Sitzungsordnerstruktur im Datei-Explorer oder unter Computer mit dem Format *\<Laufwerkbuchstabe>* auf *\<Computername>* angezeigt. Mit dieser Richtlinieneinstellung können Sie dieses Verhalten überschreiben. Wenn Sie diese Richtlinieneinstellung aktivieren, ist die Umleitung von Clientlaufwerken in Remotedesktopdienst-Sitzungen nicht zulässig, und die Zwischenablageumleitung beim Kopieren von Dateien ist auf Computern unter Windows Server 2003, Windows 8 und Windows XP nicht zulässig. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist die Umleitung von Clientlaufwerken immer zulässig. Außerdem ist die Zwischenablageumleitung beim Kopieren von Dateien immer zulässig, wenn die Zwischenablageumleitung zulässig ist. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, werden die Umleitung von Clientlaufwerken und die Zwischenablageumleitung beim Kopieren von Dateien nicht auf Gruppenrichtlinienebene festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Standard**: Aktiviert
  
- **Prompt for password upon connection** (Kennwort bei der Herstellung einer Verbindung anfordern)  
  Diese Richtlinieneinstellung legt fest, ob Remotedesktopdienste beim Herstellen einer Verbindung immer ein Kennwort vom Client anfordern. Mit dieser Einstellung können Sie erzwingen, dass Benutzer, die sich bei Remotedesktopdiensten anmelden, selbst dann zur Eingabe eines Kennworts aufgefordert werden, wenn sie das Kennwort bereits im Remotedesktopverbindungs-Client angegeben haben. Remotedesktopdienste lassen standardmäßig zu, dass Benutzer sich automatisch anmelden, indem sie ein Kennwort im Remotedesktopverbindungs-Client eingeben. Wenn Sie diese Richtlinieneinstellung aktivieren, können sich Benutzer nicht automatisch bei Remotedesktopdiensten anmelden, indem sie ihr Kennwort im Remotedesktopverbindungs-Client eingeben. Sie müssen bei der Anmeldung ein Kennwort eingeben. Wenn Sie diese Richtlinieneinstellung deaktivieren, können Benutzer sich immer automatisch bei Remotedesktopdiensten anmelden, indem sie ihr Kennwort im Remotedesktopverbindungs-Client eingeben. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, wird die automatische Anmeldung nicht auf Gruppenrichtlinienebene festgelegt.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Standard**: Aktiviert
  
- **Remote desktop services client connection encryption level** (Verschlüsselungsstufe der Verbindung des Remotedesktopdienst-Clients)  
  Mit dieser Richtlinieneinstellung wird festgelegt, ob eine bestimmte Verschlüsselungsstufe zum Schutz der Kommunikation zwischen Clientcomputern und RD-Sitzungshostservern während RDP-Verbindungen (Remotedesktopprotokoll) erforderlich ist. Diese Richtlinie gilt nur, wenn Sie die native RDP-Verschlüsselung verwenden. Allerdings wird von der Verwendung der nativen RDP-Verschlüsselung (im Gegensatz zur SSL-Verschlüsselung) abgeraten. Diese Richtlinie gilt nicht für die SSL-Verschlüsselung. Wenn Sie diese Richtlinieneinstellung aktivieren, muss für die gesamte Kommunikation zwischen Clients und RD-Sitzungshostservern während Remoteverbindungen die in dieser Einstellung festgelegte Verschlüsselungsmethode verwendet werden. Die Verschlüsselungsstufe ist standardmäßig auf „Hoch“ festgelegt. Die folgenden Verschlüsselungsmethoden stehen zur Verfügung:  
  - *Hoch*: Mit der Einstellung „Hoch“ werden zwischen dem Client und dem Server gesendete Daten mit einer starken 128-Bit-Verschlüsselung verschlüsselt. Verwenden Sie diese Verschlüsselungsstufe in Umgebungen, die nur 128-Bit-Clients enthalten (z.B. Clients mit Remotedesktopverbindung). Clients, die diese Verschlüsselungsstufe nicht unterstützen, können keine Verbindung mit RD-Sitzungshostservern herstellen.  
  - *Clientkompatibel*: Mit der Einstellung „Clientkompatibel“ werden zwischen dem Client und dem Server gesendete Daten mit der vom Client unterstützten maximalen Schlüsselstärke verschlüsselt. Verwenden Sie diese Verschlüsselungsstufe für Umgebungen mit Clients, die keine 128-Bit-Verschlüsselung unterstützen.  
  - *Niedrig*: Mit der Einstellung „Niedrig“ werden nur vom Client an den Server gesendete Daten mithilfe der 56-Bit-Verschlüsselung verschlüsselt.  
  
  Wenn Sie diese Einstellung deaktivieren oder nicht konfigurieren, wird die für Remoteverbindungen mit RD-Sitzungshostservern zu verwendende Verschlüsselungsstufe nicht über Gruppenrichtlinien erzwungen. Wichtig: die FIPS-Konformität (Federal Information Processing Standard) kann mithilfe der Systemkryptografie konfiguriert werden. Verwenden Sie FIPS-konforme Algorithmen für die Verschlüsselung, das Hashing und das Signieren von Einstellungen in der Gruppenrichtlinie (unter Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options). Mit der FIPS-konformen Einstellung werden Daten, die vom Client an den Server und vom Server an den Client gesendet werden, mit Verschlüsselungsalgorithmen gemäß FIPS 140 mithilfe von kryptografischen Modulen von Microsoft verschlüsselt und entschlüsselt. Verwenden Sie diese Verschlüsselungsstufe, wenn die Kommunikation zwischen Clients und RD-Sitzungshostservern die höchste Verschlüsselungsstufe erfordert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Standard**: Hoch
  
## <a name="remote-management"></a>Remoteverwaltung  
Weitere Informationen finden Sie unter [Policy CSP – RemoteManagement (Richtlinien-Konfigurationsdienstanbieter: RemoteManagement)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in der Windows-Dokumentation.  

- **Block storing run as credentials** (Speichern von Anmeldeinformationen für „Ausführen als“ blockieren)  
  Standardclientauthentifizierung.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Standard**: Aktiviert
  
- **Standardauthentifizierung**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Windows-Remoteverwaltungsdienst (Windows Remote Management, WinRM) die Standardauthentifizierung von einem Remoteclient akzeptiert. Wenn Sie diese Richtlinieneinstellung aktivieren, akzeptiert der WinRM-Dienst die Standardauthentifizierung von einem Remoteclient. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, akzeptiert der WinRM-Dienst keine Standardauthentifizierung von einem Remoteclient.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Standard**: Deaktiviert
  
- **Client unencrypted traffic** (Unverschlüsselter Clientdatenverkehr)  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der Windows-Remoteverwaltungsclient die Digestauthentifizierung verwendet. Wenn Sie diese Richtlinieneinstellung aktivieren, verwendet der WinRM-Client keine Digestauthentifizierung. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, verwendet der WinRM-Client die Digestauthentifizierung.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Standard**: Aktiviert
  
- **Unverschlüsselter Datenverkehr**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der WinRM-Dienst unverschlüsselte Nachrichten über das Netzwerk sendet und empfängt. Wenn Sie diese Richtlinieneinstellung aktivieren, sendet und empfängt der WinRM-Client unverschlüsselte Nachrichten über das Netzwerk. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, sendet und empfängt der WinRM-Client nur verschlüsselte Nachrichten über das Netzwerk.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Standard**: Deaktiviert
  
- **Unverschlüsselter Clientdatenverkehr**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der WinRM-Client unverschlüsselte Nachrichten über das Netzwerk sendet und empfängt. Wenn Sie diese Richtlinieneinstellung aktivieren, sendet und empfängt der WinRM-Client unverschlüsselte Nachrichten über das Netzwerk. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, sendet und empfängt der WinRM-Client nur verschlüsselte Nachrichten über das Netzwerk.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Standard**: Deaktiviert
  
- **Standardclientauthentifizierung**  
  Mit dieser Richtlinieneinstellung können Sie bestimmen, ob der WinRM-Client die Standardauthentifizierung verwendet. Wenn Sie diese Richtlinieneinstellung aktivieren, verwendet der WinRM-Client die Standardauthentifizierung. Wenn WinRM für die Verwendung des HTTP-Transports konfiguriert ist, werden der Benutzername und das Kennwort unverschlüsselt über das Netzwerk übertragen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, verwendet der WinRM-Client die Standardauthentifizierung nicht.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Standard**: Deaktiviert
  
## <a name="remote-procedure-call"></a>Remoteprozeduraufruf  
Weitere Informationen finden Sie unter [Policy CSP – RemoteProcedureCall (Richtlinien-Konfigurationsdienstanbieter: RemoteProcedureCall)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in der Windows-Dokumentation.  

- **RPC unauthenticated client options** (Nicht authentifizierte RPC-Clientoptionen)  
  Diese Richtlinieneinstellung steuert, wie die RPC-Server-Runtime nicht authentifizierte RPC-Clients behandelt, die sich mit RPC-Servern verbinden. Diese Richtlinieneinstellung betrifft alle RPC-Anwendungen. Verwenden Sie diese Richtlinieneinstellung in einer Domänenumgebung mit Vorsicht, da sie eine Vielzahl von Funktionen, darunter auch die Gruppenrichtlinienverarbeitung selbst, beeinträchtigen kann. Um nach einer Änderung die Richtlinieneinstellung wiederherzustellen, kann ein manueller Eingriff auf jedem betroffenen Computer erforderlich sein. Diese Richtlinieneinstellung sollte niemals auf einen Domänencontroller angewendet werden. Wenn Sie diese Richtlinieneinstellung deaktivieren, verwendet die RPC-Server-Runtime den Wert für „Authenticated“ (Authentifiziert) auf dem Windows-Client und den Wert für „None“ (Keine Authentifizierung) auf Windows-Server-Versionen, die diese Richtlinieneinstellung unterstützen. Wenn Sie diese Richtlinieneinstellung nicht konfigurieren, bleibt sie deaktiviert. Die RPC-Server-Runtime verhält sich so, als wäre sie aktiviert mit dem für Windows-Clients verwendeten Wert für „Authenticated“ (Authentifiziert) und dem für Server-SKUs verwendeten Wert für „None“ (Keine Authentifizierung), die diese Richtlinieneinstellung unterstützen. Wenn Sie diese Richtlinieneinstellung aktivieren, wird die RPC-Server-Runtime angewiesen, nicht authentifizierte RPC-Clients, die sich mit RPC-Servern verbinden, welche auf einem Computer ausgeführt werden, einzuschränken. Ein Client gilt als authentifizierter Client, wenn er für die Kommunikation mit dem Server eine benannte Pipe verwendet, oder wenn er RPC-Sicherheit verwendet. RPC-Schnittstellen, die speziell den Zugriff durch nicht authentifizierte Clients angefordert haben, können von dieser Einschränkung ausgenommen werden, abhängig von dem für diese Richtlinieneinstellung gewählten Wert.  
  - Durch *None* (Keine Authentifzierung) wird allen RPC-Clients gestattet, sich mit RPC-Servern zu verbinden, die auf dem Computer ausgeführt werden, auf den die Richtlinieneinstellung angewandt wird. 
  - Durch *Authenticated* (Authentifiziert) wird nur authentifizierten RPC-Clients (per oben stehender Definition) gestattet, sich mit RPC-Servern zu verbinden, die auf dem Computer ausgeführt werden, auf den die Richtlinieneinstellung angewandt wird. Ausnahmen werden für Schnittstellen gewährt, die solche angefordert haben. 
  - Durch *Authenticated without exceptions* (Authentifiziert ohne Ausnahmen) wird nur authentifizierten RPC-Clients (per oben stehender Definition) gestattet, sich mit RPC-Servern zu verbinden, die auf dem Computer ausgeführt werden, auf den die Richtlinieneinstellung angewandt wird. Ausnahmen sind nicht zulässig. Hinweis: Diese Richtlinieneinstellung wird erst angewendet, wenn das System neu gestartet wird.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Standard**: Authentifiziert

## <a name="search"></a>Suchen 
Weitere Informationen finden Sie unter [Policy CSP - Search (Richtlinien-Konfigurationsdienstanbieter: Search)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in Ihrer Windows-Dokumentation.  

- **Indizierung verschlüsselter Elemente deaktivieren**  
  Hiermit wird die Indizierung von Elementen zugelassen oder verweigert. Diese Option ist für die Windows Search-Indexerstellung bestimmt und steuert, ob verschlüsselte Elemente wie beispielsweise WIP-geschützte Dateien (Windows Information Protection) indiziert werden. Wenn die Richtlinie aktiviert ist, werden WIP-geschützte Elemente indiziert und die zugehörigen Metadaten werden an einem nicht verschlüsselten Speicherort gespeichert. Die Metadaten umfassen beispielsweise den Dateipfad und das Änderungsdatum. Wenn die Richtlinie deaktiviert ist, werden WIP-geschützte Elemente nicht indiziert und sie werden nicht in den Ergebnissen in Cortana oder im Datei-Explorer angezeigt. Ferner sind bei Fotos und Groove-Apps Leistungseinbußen möglich, wenn sich auf dem Gerät große Mengen an WIP-geschützten Mediendateien befinden.  
  [Erfahren Sie mehr]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Standard**: Ja
  
## <a name="smart-screen"></a>SmartScreen  
Weitere Informationen finden Sie unter [Policy CSP - SmartScreen (Richtlinien-Konfigurationsdienstanbieter: SmartScreen)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in Ihrer Windows-Dokumentation.  

- **Ausführen nicht überprüfter Dateien blockieren**  
  Hindern Sie Benutzer am Ausführen von nicht überprüften Dateien. 
  - *Nicht konfiguriert*: Mitarbeiter können SmartScreen-Warnungen ignorieren und schädliche Dateien ausführen. 
  - *Ja*: Mitarbeiter können SmartScreen-Warnungen nicht ignorieren und keine schädlichen Dateien ausführen.

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Standard**: Ja

- **SmartScreen für Apps und Dateien anfordern**  
  Ermöglicht IT-Administratoren das Konfigurieren von SmartScreen für Windows.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Standard**: Ja
  
## <a name="system"></a>System  
Weitere Informationen finden Sie unter [Policy CSP - System (Richtlinien-Konfigurationsdienstanbieter: System)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in Ihrer Windows-Dokumentation.  

- **Starttreiberinitialisierung für Systemstart**  
  Mit dieser Richtlinieneinstellung können Sie angeben, welche Bootstarttreiber initialisiert werden. Dies geschieht basierend auf einer durch den Bootstarttreiber für den Antischadsoftware-Frühstart festgelegten Klassifizierung. Der Bootstarttreiber für den Antischadsoftware-Frühstart kann die folgenden Klassifizierungen für die einzelnen Bootstarttreiber zurückgeben: 
  - *Gut*: Der Treiber wurde signiert und nicht manipuliert.  
  - *Schlecht:* Der Treiber wurde als Schadsoftware identifiziert. Wir empfehlen, die Initialisierung von bekannten schlechten Treibern nicht zuzulassen. 
  - *Schlecht, doch für den Bootvorgang erforderlich*: Der Treiber wurde als Schadsoftware identifiziert, doch der Computer kann nicht erfolgreich gestartet werden, ohne diesen Treiber zu laden. 
  - *Unbekannt*: Dieser Treiber wurde von Ihrer Anwendung zur Erkennung von Schadsoftware nicht bestätigt und vom Bootstarttreiber für den Antischadsoftware-Frühstart nicht klassifiziert.  

  Wenn Sie diese Richtlinieneinstellung aktivieren, können Sie auswählen, welche Bootstarttreiber beim nächsten Start des Computers initialisiert werden sollen. Wenn Sie diese Richtlinieneinstellung deaktivieren oder nicht konfigurieren, werden die guten, unbekannten oder schlechten, aber für den Bootvorgang erforderlichen Bootstarttreiber initialisiert. Die Initialisierung von schlechten Treibern wird übersprungen. Falls Ihre Anwendung für die Erkennung von Schadsoftware keinen Bootstarttreiber für den Antischadsoftware-Frühstart enthält oder dieser Treiber deaktiviert wurde, ist diese Richtlinieneinstellung wirkungslos, und alle Bootstarttreiber werden initialisiert.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Standard**: Gut, unbekannt und schlecht, aber erforderlich


## <a name="wi-fi"></a>WLAN  
Weitere Informationen finden Sie unter [Policy CSP - Wifi (Richtlinien-Konfigurationsdienstanbieter: Wifi)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in Ihrer Windows-Dokumentation.  

- **Internetfreigabe blockieren**  
  Gibt an, ob die Internetfreigabe auf dem Gerät möglich ist.   
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Standard**: Ja  

- **Automatisches Verbinden mit WLAN-Hotspots blockieren**  
  Gestattet oder verweigert das automatische Verbinden des Geräts mit WLAN-Hotspots.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Standard**: Ja  
  
## <a name="windows-connection-manager"></a>Windows-Verbindungs-Manager  
Weitere Informationen finden Sie unter [Policy CSP - WindowsConnectionManager (Richtlinien-Konfigurationsdienstanbieter: WindowsConnectionManager)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in Ihrer Windows-Dokumentation.  

- **Verbindung zu Nicht-Domänennetzwerken blockieren**  
  Diese Richtlinieneinstellung verhindert, dass Computer gleichzeitig eine Verbindung zu einem domänenbasierten Netzwerk und zu einem nicht-domänenbasierten Netzwerk herstellen. Wenn diese Richtlinieneinstellung aktiviert ist, reagiert der Computer, abhängig von den folgenden Situationen, wie folgt auf automatische und manuelle Versuche, eine Netzwerkverbindung herzustellen: 
  - Automatische Verbindungsversuche: Wenn der Computer bereits mit einem domänenbasierten Netzwerk verbunden ist, werden alle automatischen Verbindungsversuche zu nicht-domänenbasierten Netzwerken blockiert. Wenn der Computer bereits mit einem nicht-domänenbasierten Netzwerk verbunden ist, werden automatische Verbindungsversuche zu domänenbasierten Netzwerken blockiert. 
  - Manuelle Verbindungsversuche: Wenn der Computer bereits mit einem nicht-domänenbasierten Netzwerk oder einem domänenbasierten Netzwerk über andere Medien als Ethernet verbunden ist, und ein Benutzer versucht, entgegen dieser Richtlinieneinstellung eine manuelle Verbindung zu einem zusätzlichen Netzwerk herzustellen, wird die bestehende Netzwerkverbindung abgebrochen und die manuelle Verbindung gestattet. Wenn der Computer bereits mit einem nicht-domänenbasierten Netzwerk oder einem domänenbasierten Netzwerk über Ethernet verbunden ist, und ein Benutzer versucht, entgegen dieser Richtlinieneinstellung eine manuelle Verbindung zu einem zusätzlichen Netzwerk herzustellen, wird die bestehende Ethernet-Verbindung gehalten und der manuelle Verbindungsversuch wird blockiert.  

  Wenn diese Richtlinieneinstellung nicht konfiguriert oder deaktiviert wird, ist es zulässig, dass Computer gleichzeitig eine Verbindung mit einem Domänen- und einem Nicht-Domänennetzwerk herstellen.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Standard**: Aktiviert
  
## <a name="microsoft-defender"></a>Microsoft Defender  
Weitere Informationen finden Sie unter [Policy CSP - Defender (Richtlinien-Konfigurationsdienstanbieter: Defender)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in Ihrer Windows-Dokumentation.  

- **Eingehende E-Mail überprüfen**  
  Gestattet oder verweigert das Überprüfen von E-Mails.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Standard**: Ja  

- **Office apps launch child process type** (Untergeordnete Prozesse in Office-Apps starten)  
  Das Erstellen von untergeordneten Prozessen mit Office-Apps ist nicht gestattet. Dazu zählen Microsoft Word, Excel, PowerPoint, OneNote und Access. Dies ist ein typisches Verhalten für eine Schadsoftware, besonders für makrobasierte Angriffe, mit denen versucht wird, Office-Apps zum Starten oder Herunterladen ausführbarer schädlicher Dateien zu verwenden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Standard**: Blockieren
  
- **Defender sample submission consent type** (Zustimmungstyp für die Übermittlung von Beispielen in Windows Defender)  
  Diese Einstellung sucht nach der Benutzerzustimmungsebene in Microsoft Defender, um Daten zu senden. Wenn die erforderliche Zustimmung bereits erteilt wurde, sendet Microsoft Defender die Daten. Wenn nicht (und wenn der Benutzer angegeben hat, nie zu fragen), wird die Benutzeroberfläche gestartet, um nach der Benutzerzustimmung zu fragen (wenn Defender/AllowCloudProtection gestattet ist), bevor Daten gesendet werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Standard**: Sichere Beispiele automatisch senden 
  
- **Signature update interval (in hours)** (Intervall für das Aktualisieren von Signaturen (in Stunden))  
  Intervall zum Aktualisieren von Signaturen in Windows Defender in Stunden
  
  **Standard**: 4
  
- **Ausführungstyp für heruntergeladene Nutzlast für Skript**  
  Ausführungstyp für heruntergeladene Nutzlast für Skript in Defender
  
  **Standard**: Blockieren
  
- **Diebstahl von Anmeldeinformationen verhindern**  
  Microsoft Defender Credential Guard nutzt auf Virtualisierung basierende Sicherheitsverfahren, um Geheimnisse zu isolieren, sodass nur privilegierte Systemsoftware auf diese Daten zugreifen kann. Ein nicht autorisierter Zugriff auf diese geheimen Daten kann Angriffe zum Diebstahl von Anmeldeinformationen zur Folge haben (z. B. Pass-the-Hash- oder Pass-the-Ticket-Angriffe). Microsoft Defender Credential Guard verhindert diese Angriffe durch den Schutz von NTLM-Kennworthashes, Kerberos Ticket-Granting Tickets und Anmeldeinformationen, die von Anwendungen als Domänenanmeldeinformationen gespeichert werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Standard**: Aktivieren

- **Ausführungstyp für E-Mail-Inhalt**  
  Diese Regel verhindert die Ausführung oder das Starten der folgenden Dateitypen aus einer E-Mail, die in Microsoft Outlook oder einem webbasierten E-Mail-Dienst (z.B. Gmail.com oder Outlook.com) angezeigt wird: ausführbare Dateien (z.B. EXE, DLL oder SCR), Skriptdateien (z.B. PS PowerShell, VBS VisualBasic oder JS JavaScript) und Skriptarchivdateien.  
  [Erfahren Sie mehr](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail) 
  
  **Standard**: Blockieren

- **Adobe Reader launch in a child process** (Adobe Reader in einem untergeordneten Prozess starten)  

  **Standard**: Aktivieren

- **Netzwerkschutztyp**  
  Mit dieser Richtlinieneinstellung können Sie den Netzwerkschutz in Microsoft Defender Exploit Guard aktivieren (blockieren/überwachen) oder deaktivieren. Der Netzwerkschutz ist ein Feature von Microsoft Defender Exploit Guard, das Arbeitnehmer beim Verwenden von Apps vor dem Zugriff auf Phishingwebsites, Websites mit Exploits und schädliche Inhalte im Internet schützt. Dabei wird auch verhindert, dass Browser von Drittanbietern Verbindungen zu gefährlichen Websites herstellen. Der Werttyp ist Integer. Wenn Sie diese Einstellung aktivieren, wird der Netzwerkschutz aktiviert, und Arbeitnehmer können ihn nicht mehr deaktivieren. Sein Verhalten kann mit den folgenden Optionen gesteuert werden: „Blockieren“ und „Überwachen“. Wenn Sie diese Richtlinie mit der Option „Blockieren“ aktivieren, können Benutzer und Anwendungen keine Verbindungen zu gefährlichen Domänen herstellen. Diese Aktivität wird im Microsoft Defender Security Center angezeigt. Wenn Sie diese Richtlinie mit der Option „Überwachen“ aktivieren, können Benutzer/Anwendungen Verbindungen zu gefährlichen Domänen herstellen. Diese Aktivität wird jedoch trotzdem im Microsoft Defender Security Center angezeigt. Wenn Sie diese Richtlinie deaktivieren, können Benutzer/Anwendungen Verbindungen zu gefährlichen Domänen herstellen. Im Microsoft Defender Security Center werden keine Netzwerkaktivitäten angezeigt. Wenn Sie diese Richtlinie nicht konfigurieren, wird die Blockierung des Netzwerks standardmäßig deaktiviert.  
  [Erfahren Sie mehr](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)  
  
  **Standard**: Aktivieren
  
- **Defender-Überprüfungstag planen**  
  Defender-Überprüfungstag planen.
  
  **Standard**: Täglich
  
- **Schutz über die Cloud**  
  Um Ihren PC bestmöglich zu schützen, sendet Microsoft Defender Informationen zu jedem entdeckten Problem an Microsoft. Microsoft analysiert diese Informationen, erfährt mehr über die Probleme, die Sie und andere Kunden betreffen, und bietet verbesserte Lösungen an.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Standard**: Ja  

- **Potenziell unerwünschte App-Aktion in Defender**  
  Das Feature zum Schutz vor potenziell unerwünschten Anwendungen (Potentially Unwanted Applications, PUAs) in Microsoft Defender Antivirus kann solche Anwendungen identifizieren und verhindern, dass diese auf Endpunkte in ihrem Netzwerk heruntergeladen und dort installiert werden. Bei diesen Anwendungen handelt es sich nicht um Viren, Schadsoftware oder andere Arten von Bedrohungen. Diese Anwendungen können Aktionen auf Endpunkten ausführen, die deren Leistung oder Verwendung beeinträchtigen. Mit PUAs können auch Anwendungen gemeint sein, die einen schlechten Ruf haben. Typisches PUA-Verhalten umfasst: Verschiedene Arten von Softwarebündelungen; Einschleusung von Werbung in Webbrowser; Treiber- und Registrierungsoptimierungen, die Probleme erkennen, eine Zahlung zur Fehlerbehebung anfordern, aber auf dem Endpunkt verbleiben und weder Änderungen noch Optimierungen vornehmen (auch bekannt als „Rogue-Sicherheitssoftware“). Diese Anwendungen können das Risiko einer Infektion mit Schadsoftware für Ihr Netzwerk erhöhen, das Identifizieren von Infektionen erschweren und unnötig IT-Ressourcen zum Bereinigen der Anwendungen belegen.  
  [Erfahren Sie mehr](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Standard**: Blockieren  

- **Verborgener Makrocodetyp von Skripten**  
  Schadsoftware und andere Bedrohungen versuchen möglicherweise ihren schädlichen Code in einigen Skriptdateien zu verbergen oder auszublenden. Mit dieser Regel wird verhindert, dass verborgen scheinende Skripts ausgeführt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Standard**: Blockieren
  
- **Bei einer vollständigen Überprüfung Wechseldatenträger überprüfen**  
  Ermöglicht es Microsoft Defender, Wechseldatenträger (z. B. Flashlaufwerke) während einer vollständigen Überprüfung auf schädliche und unerwünschte Software zu untersuchen. Microsoft Defender Antivirus überprüft alle Dateien auf USB-Geräten, bevor die Dateien ausgeführt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Standard**: Ja  
  
- **Archivdateien überprüfen**  
  Archivdateien überprüfen in Defender.
  
  **Standard**: Ja
  
- **Verhaltensüberwachung**  
  Ermöglicht oder verweigert die Microsoft Defender-Verhaltens Überwachungsfunktionen. Eingebettet in Windows 10, sammeln und verarbeiten diese Sensoren von Signale zum Verhalten des Betriebssystems und senden diese Sensordaten an Ihre private, isolierte Cloudinstanz von Microsoft Defender ATP.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Standard**: Ja

- **Über Netzwerkordner geöffnete Dateien überprüfen**  
  Wenn Dateien schreibgeschützt sind, können Benutzer entdeckte Schadsoftware nicht entfernen.
  
  **Standard**: Ja

- **Nicht vertrauenswürdiger USB-Prozesstyp**  
  Mit dieser Regel können Administratoren verhindern, dass nicht signierte oder nicht vertrauenswürdige ausführbare Dateien von USB-Wechseldatenträgern, einschließlich SD-Karten, ausgeführt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Standard**: Blockieren
  
- **Injectionstyp für andere Prozesse in Office-Apps**  
  Office-Apps, einschließlich Word, Excel, PowerPoint und OneNote, können keinen Code in andere Prozesse einfügen. Dieses Verfahren zum Ausführen von schädlichem Code ist typisch für Schadsoftware bei dem Versuch, die Aktivität vor Antivirusprogrammen zu verstecken.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Standard**: Blockieren
  
- **Win32-Importtyp aus Office-Makrocode gestatten**  
  Schadsoftware kann Makrocode in Office-Dateien verwenden, um Win32-DLLs zu importieren und zu laden, mit denen dann API-Aufrufe möglich sind, um eine Infektion des gesamten Systems zu ermöglichen. Mit dieser Regel wird versucht, Office-Dateien zu blockieren, die Makrocode enthalten, in den Win32-DLLs importiert werden können. Dazu zählen Microsoft Word, Excel, PowerPoint und OneNote.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Standard**: Blockieren  
  
- **Defender-Cloud-Block-Level**  
  Defender-Cloud-Block-Level.
  
  **Standard**: Nicht konfiguriert

- **Echtzeitüberwachung**  
  Für Defender ist eine Echtzeitüberwachung erforderlich.
  
  **Standard**: Ja
 
- **Office communication apps launch in a child process** (Office-Kommunikations-Apps in einem untergeordneten Prozess starten)  

  **Standard**: Aktivieren

- **Mit Office-Apps ausführbare Inhaltserstellung oder Starttypen**  
  Diese Regel zielt auf typische Verhalten von verdächtigen und schädlichen Add-Ons und Skripts (Erweiterungen) ab, die ausführbare Dateien erstellen oder starten. Dies ist ein typisches Verfahren von Schadsoftware. Die Verwendung von Erweiterungen durch Office-Apps wird blockiert. Typischerweise verwenden diese Erweiterungen den Windows Scripting Host (WSH-Dateien), um Skripts auszuführen, die bestimmte Aufgaben automatisieren oder von Benutzern erstellte Add-On-Features bieten.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Standard**: Blockieren

## <a name="microsoft-defender-firewall"></a>Microsoft Defender Firewall  
Weitere Informationen finden Sie unter [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) in der Dokumentation zu Windows-Protokollen.  

- **Firewall-Profil Domäne**  
  Gibt die Profile an, zu denen die Regel gehört: „Domäne“, „Privat“, „Öffentlich“. Dieser Wert stellt das Profil für Netzwerke dar, die mit Domänen verbunden sind.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Eingehende Verbindungen blockiert**  
    **Standard**: Ja

  - **Ausgehende Verbindungen erforderlich**  
    **Standard**: Ja 

  - **Eingehende Benachrichtigungen blockiert**  
    **Standard**: Ja

  - **Firewall aktiviert**  
    **Standard**: Zulässig

- **Firewallprofil öffentlich**  
  Gibt die Profile an, zu denen die Regel gehört: „Domäne“, „Privat“, „Öffentlich“. Dieser Wert stellt das Profil für öffentliche Netzwerke dar. Diese Netzwerke werden von den Administratoren des Serverhosts als „öffentlich“ klassifiziert. Die Klassifizierung erfolgt, wenn sich der Host zum ersten Mal mit dem Netzwerk verbindet. In der Regel sind diese Netzwerke an Flughäfen, in Cafés und an anderen öffentlichen Orten zu finden, an denen die Peers im Netzwerk oder der Netzwerkadministrator nicht vertrauenswürdig sind.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Eingehende Verbindungen blockiert**  
    **Standard**: Ja

  - **Ausgehende Verbindungen erforderlich**  
    **Standard**: Ja 

  - **Eingehende Benachrichtigungen blockiert**  
    **Standard**: Ja

  - **Firewall aktiviert**  
    **Standard**: Zulässig

  - **Verbindungssicherheitsregeln aus Gruppenrichtlinie nicht zusammengeführt**  
    **Standard**: Ja

  - **Richtlinienregeln aus Gruppenrichtlinie nicht zusammengeführt**  
    **Standard**: Ja

- **Firewallprofil privat**  
  Gibt die Profile an, zu denen die Regel gehört: „Domäne“, „Privat“, „Öffentlich“. Dieser Wert stellt das Profil für private Netzwerke dar.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Eingehende Verbindungen blockiert**  
    **Standard**: Ja

  - **Ausgehende Verbindungen erforderlich**  
    **Standard**: Ja 

  - **Eingehende Benachrichtigungen blockiert**  
    **Standard**: Ja

  - **Firewall aktiviert**  
    **Standard**: Zulässig

## <a name="windows-hello-for-business"></a>Windows Hello for Business  
- **Erweitertes Antispoofing erfordern, falls verfügbar**:  
  Wenn dies der Fall ist, verwenden Geräte das erweiterte Antispoofing, sofern verfügbar. Wenn dies nicht der Fall ist, wird das Antispoofing blockiert. Nicht konfiguriert berücksichtigt Konfigurationen, die auf dem Client ausgeführt werden.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Standard**: Ja

- **Konfigurieren von Windows Hello for Business**   
    Windows Hello for Business ist eine alternative Methode zum Anmelden bei Windows durch Ersetzen von Kennwörtern, Smartcards und virtuellen Smartcards.  

  - Wenn Sie auf *Ja*festgelegt ist, aktivieren Sie diese Richtlinie, und das Gerät stellt Windows Hello for Business bereit.  
  - Wenn diese Einstellung auf *nicht konfiguriert*festgelegt ist, wirkt sich die Baseline nicht auf die Richtlinien Einstellung des Geräts aus. Dies bedeutet Folgendes: Wenn Windows Hello for Business auf einem Gerät deaktiviert ist, bleibt es deaktiviert. Wenn Sie aktiviert ist, bleibt sie aktiviert. 

  Sie können Windows Hello for Business über diese Baseline nicht deaktivieren. Sie können Windows Hello for Business deaktivieren, wenn Sie die [Windows](windows-hello.md)-Registrierung konfigurieren, oder als Teil eines Geräte Konfigurations Profils für [Identity Protection](identity-protection-configure.md).  

  **Standard**: Ja

- **Kleinbuchstaben in PIN vorschreiben**  
  Falls erforderlich, muss die Benutzer-PIN mindestens einen Kleinbuchstaben enthalten.

  **Standard**: Zulässig

- **Sonderzeichen in PIN vorschreiben**  
  Falls erforderlich, muss die Benutzer-PIN mindestens ein Sonderzeichen enthalten.

  **Standard**: Zulässig

- **PIN-Mindestlänge**  
  Die minimale PIN-Länge muss zwischen 4 und 127 liegen.

  **Standard**: 6

- **Großbuchstaben in PIN vorschreiben**  
  Falls erforderlich, muss die Benutzer-PIN mindestens einen Großbuchstaben enthalten.

  **Standard**: Zulässig

## <a name="windows-ink-workspace"></a>Windows Ink-Arbeitsbereich  
Weitere Informationen finden Sie unter [Policy CSP - WindowsInkWorkspace (Richtlinien-Konfigurationsdienstanbieter - WindowsInkWorkspace)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in Ihrer Windows-Dokumentation.  

- **Ink-Arbeitsbereich**  
  Gibt an, ob der Benutzer auf den Ink-Arbeitsbereich zugreifen darf. 
  - *Deaktiviert*: Der Zugriff auf den Ink-Arbeitsbereich ist deaktiviert. Die Funktion ist deaktiviert.
  - *Aktiviert*: Der Ink-Arbeitsbereich ist aktiviert, aber der Benutzer kann nicht über den Sperrbildschirm darauf zugreifen.
  - *Nicht konfiguriert* – Der Ink-Arbeitsbereich ist aktiviert, und der Benutzer kann über den Sperrbildschirm darauf zugreifen.  

  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Standard**: Aktiviert
 
## <a name="windows-powershell"></a>Windows PowerShell  
Weitere Informationen finden Sie unter [Policy CSP - WindowsPowerShell (Richtlinien-Konfigurationsdienstanbieter - WindowsPowerShell)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in Ihrer Windows-Dokumentation.  

- **PowerShell-Shellskriptblock-Protokollierung**  
  Mit dieser Richtlinieneinstellung können alle PowerShell-Skript-Eingaben im Microsoft-Windows-PowerShell/Operational-Ereignisprotokoll protokolliert werden. Wenn Sie diese Richtlinieneinstellung aktivieren, protokolliert Windows PowerShell die Verarbeitung von Befehlen, Skriptblöcken, Funktionen und Skripts, unabhängig davon, ob diese interaktiv oder automatisch aufgerufen wurden. Wenn Sie diese Richtlinieneinstellung deaktivieren, ist das Protokollieren von PowerShell-Skript-Eingaben deaktiviert. Wenn Sie die Protokollierung von Skriptblockaufrufen aktivieren, protokolliert PowerShell zusätzlich Protokollereignisse, wenn ein Befehl, ein Skriptblock, eine Funktion oder Skriptstarts oder -stops aufgerufen werden. Das Aktivieren der Protokollierung von Aufrufen führt zu einer großen Anzahl von Ereignisprotokollen. Hinweis: Diese Richtlinieneinstellung ist sowohl unter„Computerkonfiguration“ als auch unter „Benutzerkonfiguration“ im Editor für Gruppenrichtlinien vorhanden. Die Richtlinieneinstellung in der Computerkonfiguration hat Vorrang vor der Richtlinieneinstellung in der Benutzerkonfiguration.  
  [Erfahren Sie mehr](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Standard**: Aktiviert

## <a name="whats-changed-in-the-new-template"></a>Geänderte Änderungen in der neuen Vorlage
Die *MDM-Sicherheitsbaseline für* die Vorlage "Mai 2019" weist die folgenden Änderungen in der *Vorschau* Vorlage auf.

### <a name="changes-to-the-baseline-settings"></a>Änderungen an den Baseline-Einstellungen
Die folgenden Einstellungen sind entweder:
- *Neu* in der aktuellen Version der Baseline.
- Aus dieser neuesten Baselineversion *entfernt* , aber in der vorherigen Version vorhanden.
- Es wurde auf irgendeine Weise *überarbeitet* , wie die Einstellungen in der vorherigen Version auftraten. 

*[Neu]* [**oberhalb der Sperre**](#above-lock):
- **Sprachaktivierung von Apps über Sperrbildschirm**    

*[Neu]* [**Anwendungsverwaltung**](#application-management): 
- **Benutzersteuerung für Installationen blockieren**  
- **Blockieren von MSI-App-Installationen mit erhöhten Rechten**  

*[Entfernt]* [**BitLocker**](#bitlocker):  
- BitLocker-Wechsel Laufwerks Richtlinie > **Verschlüsselungsmethode**
- **BitLocker-Richtlinie für Festplattenlaufwerke** *(alle Einstellungen)*
- **BitLocker-Richtlinie für System Laufwerke** *(alle Einstellungen)*

*[Neu]* [**Konnektivität**](#connectivity):
- **Sicheren Zugriff auf UNC-Pfade konfigurieren**

*[Neu]* [**Device Guard**](#device-guard):
- **Virtualisierungsbasierte Sicherheit**


*[New]* [**DMA Guard**](#dma-guard):
- **Aufzählung externer Geräte, die mit Kernel-DMA-Schutz nicht kompatibel sind**  

*[Neu]* [**Internet Explorer**](#internet-explorer):
- **Explorer internet zone updates to status bar via script** (Skriptgesteuerte Updates für die Statusleiste in der Internetzone von Explorer)
- **Internet Explorer internet zone drag and drop or copy and paste files** (Drag & Drop oder Kopieren und Einfügen von Dateien in einer Internetzone in Internet Explorer)  
- **Internet Explorer restricted zone .NET Framework reliant components** (.NET Framework-Komponenten in eingeschränkten Zonen von Internet Explorer)  
- **Internet Explorer local machine zone do not run antimalware against Active X controls** (Keine Antischadsoftwareprogramme für ActiveX-Steuerelemente in lokaler Computerzone in Internet Explorer ausführen)
- **Unterstützung der Internet Explorer-Verschlüsselung**  

*[Überarbeitet]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer Internet-Zone automatische Aufforderung zum Herunterladen von Dateien** > der Standardwert ist jetzt **deaktiviert**. In der Vorschau war dies auf Aktiviert festgelegt.

*[Neu]* [**Remoteunterstützung**](#remote-assistance):  
- **Remote Unterstützung angefordert** 
  - **Berechtigung zur Remote Unterstützung angefordert**
  - **Maximaler Zeitwert des Tickets**  
  - **Maximaler Ticketzeitraum**  
  - **Einladungs Methode für E-Mail**


*[Neu]* [**Microsoft Defender**](#microsoft-defender):
- **Adobe Reader launch in a child process** (Adobe Reader in einem untergeordneten Prozess starten)  
- **Office communication apps launch in a child process** (Office-Kommunikations-Apps in einem untergeordneten Prozess starten) 

*[Neu]* [ **Microsoft Defender Firewall**](#microsoft-defender-firewall)
- **Firewall-Profil Domäne**  
  - **Eingehende Verbindungen blockiert**  
  - **Ausgehende Verbindungen erforderlich**  
  - **Eingehende Benachrichtigungen blockiert**  
  - **Firewall aktiviert**  
- **Firewallprofil öffentlich**  
  - **Eingehende Verbindungen blockiert**  
  - **Ausgehende Verbindungen erforderlich**  
  - **Eingehende Benachrichtigungen blockiert**  
  - **Firewall aktiviert** 
  - **Verbindungssicherheitsregeln aus Gruppenrichtlinie nicht zusammengeführt**   
  - **Richtlinienregeln aus Gruppenrichtlinie nicht zusammengeführt**  
- **Firewallprofil privat**  
  - **Eingehende Verbindungen blockiert**  
  - **Ausgehende Verbindungen erforderlich**  
  - **Eingehende Benachrichtigungen blockiert**  
  - **Firewall aktiviert**  

*[Neu]* [**Windows Hello for Business**](#windows-hello-for-business):  
- **Erweitertes Antispoofing erfordern, falls verfügbar**:  
- **Konfigurieren von Windows Hello for Business**  
- **Kleinbuchstaben in PIN vorschreiben** 
- **Sonderzeichen in PIN vorschreiben** 
- **PIN-Mindestlänge**  
- **Großbuchstaben in PIN vorschreiben** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Microsoft Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Microsoft Defender SmartScreen. Enabling this policy turns off Microsoft Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Microsoft defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Microsoft Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Microsoft Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Microsoft Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in WinMMicrosofticrosoftdows Defender to send data. If the required consent has already been granted, Microsoft Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Microsoft Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Microsoft Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Microsoft Defender Exploit Guard. Network protection is a feature of Microsoft Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Microsoft Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Microsoft Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Microsoft Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Microsoft Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Microsoft Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Microsoft Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Microsoft Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Microsoft Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
