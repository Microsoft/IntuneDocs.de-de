---
title: Windows 10-Konformitätseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Windows 10-, Windows Holographic- und Surface Hub-Geräte in Microsoft Intune festzulegen. Überprüfen Sie die Konformität mit der minimalen und maximalen Betriebssystemversion, legen Sie Kennwortbeschränkungen und -länge fest, prüfen Sie auf Antivirenlösungen (AV) von Partnern, aktivieren Sie die Verschlüsselung der Datenspeicherung und vieles mehr.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3c6c029a5c5864eda46a68832b2f9f655553846
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889535"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Einstellungen für Windows 10 und höher, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für Geräte mit Windows 10 und höher festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwenden Sie diese Einstellungen, um u. a. BitLocker anzufordern, eine mindestens erforderliche und eine maximal zulässige Betriebssystemversion festzulegen und eine Risikostufe mit Microsoft Defender Advanced Threat Protection (ATP) zu bestimmen.

Diese Funktion gilt für:

- Windows 10 und höher
- Windows Holographic for Business
- Surface Hub

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.

## <a name="device-health"></a>Geräteintegrität

### <a name="windows-health-attestation-service-evaluation-rules"></a>Evaluierungs Regeln für den Windows Health Attestation-Dienst

- **BitLocker erforderlich**:  
   Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet die Trusted Platform Module (TPM) zum Schutz des Windows-Betriebssystems und der Benutzerdaten. TPM stellt auch sicher, dass ein Computer auch dann nicht manipuliert wird, wenn er unbeaufsichtigt gelassen, verloren oder gestohlen wird. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann erst auf die Schlüssel zugegriffen werden, nachdem das TPM den Zustand des Computers überprüft hat.  

   - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
   - **Erforderlich**: Das Gerät kann Daten, die auf dem Laufwerk gespeichert sind, vor unbefugtem Zugriff schützen, wenn das System ausgeschaltet ist oder sich im Ruhezustand befindet.  


- **Sicherer Start muss auf dem Gerät aktiviert sein**:  
    - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
    - **Erforderlich** : das System ist gezwungen, den vertrauenswürdigen Zustand einer Factory zu starten. Die zum Starten des Computers verwendeten Kernkomponenten müssen zudem über die richtigen kryptografischen Signaturen verfügen, denen der Hersteller des Geräts vertraut. Die Signatur wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien derart manipuliert werden, dass ihre Signatur beschädigt wird, wird das System nicht gestartet.

  > [!NOTE]
  > Die Einstellung **Sicherer Start muss auf dem Gerät aktiviert sein** wird von einigen TPM 1.2- und TPM 2.0-Geräten unterstützt. Für Geräte, die TPM 2.0 oder höher nicht unterstützen, wird der Richtlinienstatus in Intune als **Nicht konform** angezeigt. Weitere Informationen zu unterstützten Versionen finden Sie unter [Integritätsnachweis für Geräte](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Codeintegrität erforderlich**:  
  Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird.
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  -  **Erforderlich**: Erzwingt Codeintegrität, wodurch erkannt wird, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird. Zudem wird erkannt, ob eine Systemdatei durch Schadsoftware geändert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.

Weitere Ressourcen:

- Ausführliche Informationen zur Funktionsweise des Health Attestation-Dienstanbieters finden Sie unter [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Tipp zur Unterstützung: Verwenden der Einstellungen für den Integritätsnachweis für Geräte im Rahmen Ihrer Intune-Konformitätsrichtlinie](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643).

## <a name="device-properties"></a>Geräteeigenschaften

### <a name="operating-system-version"></a>Version des Betriebssystems

- **Mindestversion des Betriebssystems**:  
  Geben Sie die minimal zulässige Version im Zahlenformat **Hauptversion.Nebenversion.Build.CU** ein. Um den richtigen Wert abzurufen, öffnen Sie eine Eingabeaufforderung und geben `ver` ein. Der Befehl `ver` gibt die Version im folgenden Format zurück:

  `Microsoft Windows [Version 10.0.17134.1]`

  Wenn ein Gerät eine frühere Version als die von Ihnen eingegebene Betriebssystemversion aufweist, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren. Nach dem Upgrade kann er auf Unternehmensressourcen zugreifen.

- **Maximale Version des Betriebssystems**:  
  Geben Sie die maximal zulässige Version im Zahlenformat **Hauptversion.Nebenversion.Build.Revision** ein. Um den richtigen Wert abzurufen, öffnen Sie eine Eingabeaufforderung und geben `ver` ein. Der Befehl `ver` gibt die Version im folgenden Format zurück:

  `Microsoft Windows [Version 10.0.17134.1]`

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Organisationsressourcen gesperrt. Der Endbenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Minimal erforderliches Betriebssystem für mobile Geräte**:  
  Geben Sie die minimal zulässige Version im Zahlenformat „Hauptversion.Nebenversion.Build“ ein.

  Wenn ein Gerät eine frühere Version als die von Ihnen eingegebene Betriebssystemversion aufweist, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren. Nach dem Upgrade kann er auf Unternehmensressourcen zugreifen.

- **Maximal erforderliches Betriebssystem für mobile Geräte**:  
  Geben Sie die maximal zulässige Version im Zahlenformat „Hauptversion.Nebenversion.Build“ ein.

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Organisationsressourcen gesperrt. Der Endbenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Gültige Betriebssystembuilds**:  
  Geben Sie einen Bereich für die zulässigen Betriebssystemversionen ein, einschließlich eines Minimums und eines Maximums. Sie können auch eine Dateiliste der durch Trennzeichen getrennten Werte (comma-separated values, CSV) der zulässigen Buildnummern des Betriebssystems **exportieren**.

## <a name="configuration-manager-compliance"></a>Konformität mit Configuration Manager

Gilt nur für gemeinsam verwaltete Geräte mit Windows 10 und höher. Ausschließliche Intune-Geräte geben einen „Nicht verfügbar“-Status zurück.

- **Gerätekonformität von System Center Configuration Manager erforderlich**:  
  - **Nicht konfiguriert** (*Standardeinstellung*): Intune prüft keine der Configuration Manager-Einstellungen auf Konformität.
  - **Erforderlich**: Erzwingt, dass alle Einstellungen (Konfigurationselemente) in System Center Configuration Manager konform sind.  

    Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Benutzer müssen ein Kennwort eingeben, bevor sie auf ihr Gerät zugreifen können. 

- **Einfache Kennwörter:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Benutzer können einfache Kenn Wörter erstellen, z. b. **1234** oder **1111**.
  - **Blockieren**: Benutzer können kein einfaches Kennwort wie **1234** oder **1111** erstellen.

- **Kennworttyp**:  
  Wählen Sie den erforderlichen Kennwort- oder PIN-Typ aus. Folgende Optionen sind verfügbar:
  - **Standard des Geräts** (*Standard*): erfordert ein Kennwort, eine numerische PIN oder eine alphanumerische PIN.
  - **Numerisch** : erfordert ein Kennwort oder eine numerische PIN.
  - **Alphanumerisch** : erfordert ein Kennwort oder eine alphanumerische PIN.  
  
  Wenn *alphanumerisch*festgelegt ist, sind die folgenden Einstellungen verfügbar:  
  - **Kennwortkomplexität**:  
    Folgende Optionen sind verfügbar: 
    - **Ziffern und Kleinbuchstaben erfordern** (*Standard*)
    - **Ziffern, Kleinbuchstaben und Großbuchstaben erforderlich**
    - **Ziffern, Kleinbuchstaben, Großbuchstaben und Sonderzeichen erforderlich**

    > [!TIP]
    > Die alphanumerischen Kenn Wort Richtlinien können komplex sein. Wir empfehlen Administratoren, die CSPs zu lesen, um weitere Informationen zu erhalten:
    >
    > - [DeviceLock/Alpha anumericgeräte-Manager-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Minimale Kennwortlänge:**  
  Geben Sie die Mindestanzahl an Ziffern oder Zeichen ein, die das Kennwort enthalten muss.

- **Minuten der Inaktivität vor Anforderung des Kennworts:**  
  Geben Sie die Leerlaufzeit ein, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):**  
  Geben Sie die Anzahl der Tage ein, nach der das Kennwort abläuft und ein neues erstellt werden muss (1–730).

- **Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung:**  
  Geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden können.

- **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt (Mobile und Holographic)** :  
  - **Nicht konfiguriert** (*Standardeinstellung*)
  - **Erforderlich**: Fordert den Gerätebenutzer jedes Mal auf, das Kennwort einzugeben, wenn das Gerät aus dem Leerlauf zurückkehrt.

  > [!IMPORTANT]
  > Wenn die Kennwortanforderung auf einem Windows-Desktop geändert wird, wirkt sich das auf die nächste Anmeldung der Benutzer aus, da das Gerät in diesem Moment aus dem Leerlauf in den aktiven Zustand wechselt. Benutzer mit Kennwörtern, die die Anforderungen erfüllen, werden trotzdem aufgefordert, ihre Kennwörter ändern.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**:  
  - **Nicht konfiguriert** (*Standardeinstellung*)
  - **Erforderlich**: Verwenden Sie diese Einstellung, um die Datenspeicher auf Ihren Geräten zu verschlüsseln.

  > [!NOTE]
  > Die Einstellung **Encryption of data storage on a device** (Verschlüsselung des Datenspeichers auf einem Gerät) überprüft allgemein, ob das Gerät über Verschlüsselung verfügt. Für eine stabilere Verschlüsselungseinstellung sollten Sie **BitLocker erforderlich** in Betracht ziehen. Dabei wird der Windows-Integritätsnachweis für Geräte genutzt, um den BitLocker-Status auf Ebene des TPM (Trusted Platform Module) zu überprüfen.

### <a name="device-security"></a>Gerätesicherheit  

- **Firewall:**  
  - **Nicht konfiguriert** (*Standard*): InTune steuert weder die Microsoft Defender Firewall noch die vorhandenen Einstellungen.
  - **Fordern** Sie die Microsoft Defender Firewall an, und verhindern Sie, dass Benutzer Sie deaktivieren.  

  [Firewall-CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Wenn das Gerät nach einem Neustart sofort synchronisiert wird oder die Wake-in-the-down-Datei sofort synchronisiert, wird diese Einstellung möglicherweise als **Fehler**gemeldet. Dieses Szenario wirkt sich möglicherweise nicht auf den Gesamtstatus der Geräte Konformität aus. Zum erneuten Auswerten des Konformitäts Status müssen Sie [das Gerät manuell synchronisieren](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Trusted Platform Module (TPM)** :  
  - **Nicht konfiguriert** (*Standardeinstellung*): InTune überprüft das Gerät nicht auf eine TPM-Chip Version.
  - **Erforderlich** : InTune überprüft die TPM-Chip Version auf Konformität. Das Gerät ist kompatibel, wenn die TPM-Chip Version größer als **0** (null) ist. Das Gerät ist nicht kompatibel, wenn auf dem Gerät keine TPM-Version vorhanden ist.  

  [DeviceStatus-CSP-DeviceStatus/TPM/SpecificationVersion-Knoten](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Intune überprüft das Gerät nicht auf installierte Antivirenlösungen. 
  - **Erforderlich**: Überprüfen Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec und Microsoft Defender), die beim [Windows-Sicherheitscenter](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) registriert sind.

- **Antispyware**:  
  - **Nicht konfiguriert** (*Standardeinstellung*): Intune überprüft das Gerät nicht auf installierte Antispywarelösungen.
  - **Erforderlich**: Überprüfen Sie die Konformität mit Antispywarelösungen (beispielsweise Symantec und Microsoft Defender), die beim [Windows-Sicherheitscenter](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) registriert sind.  

### <a name="defender"></a>Defender

*Die folgenden Kompatibilitäts Einstellungen werden von Windows 10 Desktop unterstützt.*

- **Microsoft Defender-Antischadsoftware**:  
  - **Nicht konfiguriert** (*Standard*): InTune steuert weder den Dienst noch die vorhandenen Einstellungen.
  - **Erforderlich** : Aktivieren Sie den Microsoft Defender-antischadsoftwaredienst, und verhindern Sie, dass Benutzer ihn ausschalten. 

- **Microsoft Defender Antimalware-Mindestversion**:  
  Geben Sie die zulässige Mindestversion des Microsoft Defender Anti-Malware-Diensts ein. Geben Sie beispielsweise `4.11.0.0` ein. Wenn das Feld leer gelassen wird, kann eine beliebige Version des Microsoft Defender Anti-Malware-Diensts verwendet werden.  

  *Standardmäßig ist keine Version konfiguriert*.

- **Microsoft Defender Antimalware-Sicherheits Intelligenz auf dem neuesten Stand**:  
  Steuert die Windows-Sicherheits Viren und-Schutz Updates auf den Geräten.  
  - **Nicht konfiguriert** (*Standardeinstellung*): InTune erzwingt keine Anforderungen.
  - **Erforderlich** : erzwingen Sie, dass Microsoft Defender Security Intelligence auf dem neuesten Stand ist. 

  Weitere Informationen finden Sie unter [Security Intelligence Updates für Microsoft Defender Antivirus und andere Antischadsoftware von Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).

- **Echtzeitschutz**:  
  - **Nicht konfiguriert** (*Standard*): InTune steuert diese Funktion nicht und ändert vorhandene Einstellungen nicht.
  - **Erforderlich** : Aktivieren Sie den Echtzeitschutz, der auf Schadsoftware, Spyware und andere unerwünschte Software scannt.  

  [Defender/allowrealtimemonitoring-CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Microsoft Defender Advanced Threat Protection-Regeln

- **Anfordern, dass das Gerät höchstens das angegebene Computerrisiko aufweist**:  
  Verwenden Sie diese Einstellung, um die Risikobewertung Ihrer Dienste zur Verteidigung gegen Bedrohungen als Konformitätsvoraussetzung zu fordern. Wählen Sie die maximal zulässige Bedrohungsstufe:
  - **Nicht konfiguriert** (*Standardeinstellung*)  
  - **Löschen**: Diese Option ist die sicherste, da auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als konform bewertet, wenn nur Bedrohungen auf niedrigen Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät vorhandenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.
  
  Informationen zum Einrichten von Microsoft Defender ATP (Advanced Threat Protection) als Bedrohungsschutzdienst finden Sie unter [Aktivieren von Microsoft Defender ATP mit bedingtem Zugriff](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business verwendet die Plattform **Windows 10 und höher**. Windows Holographic for Business unterstützt die folgende Einstellung:

- **Systemsicherheit** > **Verschlüsselung** > **Verschlüsselung des Datenspeichers auf dem Gerät**.

Informationen zur Überprüfung der Geräteverschlüsselung unter Microsoft HoloLens finden Sie unter [Überprüfen der Geräteverschlüsselung](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub verwendet die Plattform **Windows 10 und höher**. Surface Hub-Geräte werden sowohl für Konformität als auch für bedingten Zugriff unterstützt. Um diese Funktionen auf Surface Hub-Geräten zu aktivieren, wird empfohlen, die [automatische Registrierung von Windows 10](../enrollment/windows-enroll.md) in Intune zu aktivieren (erfordert Azure Active Directory [Azure AD]) und die Surface Hub-Geräte als Gerätegruppen zu behandeln. Surface Hub-Geräte müssen mit Azure AD verbunden sein, um die Konformität und den bedingten Zugriff zu gewährleisten.

Eine Anleitung finden Sie unter [Registrierung von Windows-Geräten](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für Windows 8.1](compliance-policy-create-windows-8-1.md)-Geräte.
