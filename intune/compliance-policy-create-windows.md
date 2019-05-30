---
title: Windows 10-Konformitätseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Windows 10-, Windows Holographic- und Surface Hub-Geräte in Microsoft Intune festzulegen. Überprüfen Sie die Konformität mit der minimalen und maximalen Betriebssystemversion, legen Sie Kennwortbeschränkungen und -länge fest, prüfen Sie auf Antivirenlösungen (AV) von Partnern, aktivieren Sie die Verschlüsselung der Datenspeicherung und vieles mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d956526d483a74ca5929180a48ea2dcd8b3eab7
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423627"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Einstellungen für Windows 10 und höher, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für Geräte mit Windows 10 und höher festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) verwenden Sie diese Einstellungen, um u.a. BitLocker anzufordern, eine minimale und maximale Betriebssystemversion festzulegen und eine Risikostufe mit Windows Defender Advanced Threat Protection (ATP) zu bestimmen.

Diese Funktion gilt für:

- Windows 10 und höher
- Windows Holographic for Business
- Surface Hub

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie unter **Plattform** die Option **Windows 10 und höher** aus.

## <a name="device-health"></a>Device health

- **BitLocker erforderlich**: Bei Festlegung auf **Anfordern** kann das Gerät Daten, die auf dem Laufwerk gespeichert sind, vor unbefugtem Zugriff schützen, wenn das System ausgeschaltet ist oder sich im Ruhezustand befindet. Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet das TPM zum Schutz des Windows-Betriebssystems und der Benutzerdaten. TPM stellt auch sicher, dass ein Computer auch dann nicht manipuliert wird, wenn er unbeaufsichtigt gelassen, verloren oder gestohlen wird. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann erst auf die Schlüssel zugegriffen werden, nachdem das TPM den Zustand des Computers überprüft hat.

  In der Standardeinstellung **Nicht konfiguriert** wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

- **Sicherer Start muss auf dem Gerät aktiviert sein**: Bei Festlegung auf **Anfordern** wird das System gezwungen, in einem vom Hersteller als vertrauenswürdig eingestuften Zustand zu starten. Falls aktiviert, müssen die zum Starten des Computers verwendeten Kernkomponenten zudem über die richtigen kryptografischen Signaturen verfügen, denen der Hersteller des Geräts vertraut. Die Signatur wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien derart manipuliert werden, dass ihre Signatur beschädigt wird, wird das System nicht gestartet.

  In der Standardeinstellung **Nicht konfiguriert** wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

  > [!NOTE]
  > Die Einstellung **Sicherer Start muss auf dem Gerät aktiviert sein** wird von einigen TPM 1.2- und TPM 2.0-Geräten unterstützt. Für Geräte, die TPM 2.0 oder höher nicht unterstützen, wird der Richtlinienstatus in Intune als **Nicht konform** angezeigt. Weitere Informationen zu unterstützten Versionen finden Sie unter [Integritätsnachweis für Geräte](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Codeintegrität erforderlich**: Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird. Bei Festlegung auf **Anfordern**, erkennt die Codeintegrität, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird. Sie erkennt auch, ob eine Systemdatei durch Schadsoftware geändert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.

  In der Standardeinstellung **Nicht konfiguriert** wird diese Einstellung nicht für die Konformitätsprüfung ausgewertet.

Weitere Ressourcen:

- Informationen zur Funktionsweise des HAS-Diensts finden Sie unter [Integritätsnachweis-CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Tipps zur Unterstützung: Verwenden der Einstellungen für den Integritätsnachweis für Geräte im Rahmen Ihrer Intune-Konformitätsrichtlinie](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Geräteeigenschaften

- **Minimale Version des Betriebssystems:** Geben Sie die minimal zulässige Version im Zahlenformat **Hauptversion.Nebenversion.Build.CU** ein. Um den richtigen Wert abzurufen, öffnen Sie eine Eingabeaufforderung und geben `ver` ein. Der Befehl `ver` gibt die Version im folgenden Format zurück:

  `Microsoft Windows [Version 10.0.17134.1]`

  Wenn ein Gerät eine frühere Version als die von Ihnen eingegebene Betriebssystemversion aufweist, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren. Nach dem Upgrade kann er auf Unternehmensressourcen zugreifen.

- **Maximale Version des Betriebssystems:** Geben Sie die maximal zulässige Version im Zahlenformat **Hauptversion.Nebenversion.Build.Revision** ein. Um den richtigen Wert abzurufen, öffnen Sie eine Eingabeaufforderung und geben `ver` ein. Der Befehl `ver` gibt die Version im folgenden Format zurück:

  `Microsoft Windows [Version 10.0.17134.1]`

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Organisationsressourcen gesperrt. Der Endbenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Minimale Version des Betriebssystems für mobile Geräte**: Geben Sie die minimal zulässige Version im Zahlenformat „Hauptversion.Nebenversion.Build“ ein.

  Wenn ein Gerät eine frühere Version als die von Ihnen eingegebene Betriebssystemversion aufweist, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann sein Gerät aktualisieren. Nach dem Upgrade kann er auf Unternehmensressourcen zugreifen.

- **Maximale Version des Betriebssystems für mobile Geräte**: Geben Sie die maximal zulässige Version im Zahlenformat „Hauptversion.Nebenversion.Build“ ein.

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Organisationsressourcen gesperrt. Der Endbenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Gültige Betriebssystembuilds**: Geben Sie einen Bereich für die zulässigen Betriebssystemversionen ein, einschließlich eines Minimums und eines Maximums. Sie können auch eine Dateiliste der durch Trennzeichen getrennten Werte (comma-separated values, CSV) der zulässigen Buildnummern des Betriebssystems **exportieren**.

## <a name="configuration-manager-compliance"></a>Konformität mit Configuration Manager

Gilt nur für gemeinsam verwaltete Geräte mit Windows 10 und höher. Ausschließliche Intune-Geräte geben einen „Nicht verfügbar“-Status zurück.

- **Gerätekonformität von System Center Configuration Manager erforderlich**: Wählen Sie **Anfordern** aus, um zu erzwingen, dass alle Einstellungen (Konfigurationselemente) in System Center Configuration Manager konform sind. 

  Beispielsweise sollen alle Softwareupdates auf Geräten installiert werden. Im Configuration Manager hat diese Anforderung den Zustand „Installiert“. Falls sich Programme auf dem Gerät in einem unbekannten Zustand befinden, so ist das Gerät in Intune nicht konform.
  
  Bei **Nicht konfiguriert** prüft Intune keine der Configuration Manager-Einstellungen auf Konformität.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Einfache Kennwörter:** Legen Sie **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie **1234** oder **1111** erstellen können. Wenn Sie diese Option auf **Nicht konfiguriert** setzen, können Benutzer Kennwörter wie **1234** oder **1111** erstellen.
- **Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus **numerischen** Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).

  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
    - Kleinbuchstaben
    - Großbuchstaben
    - Symbole
    - Zahlen

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen.

- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.
- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl der bereits verwendeten Kennwörtern an, die nicht erneut verwendet werden dürfen.
- **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt (Mobile und Holographic)**: Erzwingen Sie die Eingabe des Kennworts, wenn das Gerät aus dem Leerlaufzustand zurückkehrt.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln.

  > [!NOTE]
  > Die Einstellung **Encryption of data storage on a device** (Verschlüsselung des Datenspeichers auf einem Gerät) überprüft allgemein, ob das Gerät über Verschlüsselung verfügt. Für eine stabilere Verschlüsselungseinstellung sollten Sie **BitLocker erforderlich** in Betracht ziehen. Dabei wird der Windows-Integritätsnachweis für Geräte genutzt, um den BitLocker-Status auf Ebene des TPM (Trusted Platform Module) zu überprüfen.

### <a name="device-security"></a>Gerätesicherheit

- **Antivirus**: Bei Festlegung auf **Erforderlich** können Sie die Konformität mit Antivirenlösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim [Windows-Sicherheitscenter](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) registriert sind. Wenn sie **nicht konfiguriert** ist, prüft Intune nicht nach Antiviruslösungen, die auf dem Gerät installiert sind.
- **Antispyware**: Bei Festlegung auf **Erforderlich** können Sie die Konformität mit Antispyware-Lösungen (beispielsweise Symantec und Windows Defender) überprüfen, die beim [Windows-Sicherheitscenter](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/) registriert sind. Wenn sie **nicht konfiguriert** ist, prüft Intune nicht nach Antispyware-Lösungen, die auf dem Gerät installiert sind.

## <a name="windows-defender-atp"></a>Windows Defender ATP

- **Anfordern, dass das Gerät höchstens das angegebene Computerrisiko aufweist:** Verwenden Sie diese Einstellung, um die Risikobewertung Ihrer Dienste zur Verteidigung gegen Bedrohungen als Konformitätsvoraussetzung zu fordern. Wählen Sie die maximal zulässige Bedrohungsstufe:

  - **Clear** (Löschen): Diese Option ist die sicherste, da auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät vorhandenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.
  
  Informationen zum Einrichten von Windows Defender ATP (Advanced Threat Protection) als Bedrohungsschutzdienst finden Sie unter [Aktivieren von Windows Defender ATP mit bedingtem Zugriff](advanced-threat-protection.md).

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business verwendet die Plattform **Windows 10 und höher**. Windows Holographic for Business unterstützt die folgende Einstellung:

- **Systemsicherheit** > **Verschlüsselung** > **Verschlüsselung des Datenspeichers auf dem Gerät**.

Informationen zur Überprüfung der Geräteverschlüsselung unter Microsoft HoloLens finden Sie unter [Überprüfen der Geräteverschlüsselung](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub verwendet die Plattform **Windows 10 und höher**. Surface Hub-Geräte werden sowohl für Konformität als auch für bedingten Zugriff unterstützt. Um diese Funktionen auf Surface Hub-Geräten zu aktivieren, wird empfohlen, die [automatische Registrierung von Windows 10](windows-enroll.md) in Intune zu aktivieren (erfordert Azure Active Directory [Azure AD]) und die Surface Hub-Geräte als Gerätegruppen zu behandeln. Surface Hub-Geräte müssen mit Azure AD verbunden sein, um die Konformität und den bedingten Zugriff zu gewährleisten.

Eine Anleitung finden Sie unter [Registrierung von Windows-Geräten](windows-enroll.md).

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für Windows 8.1](compliance-policy-create-windows-8-1.md)-Geräte.