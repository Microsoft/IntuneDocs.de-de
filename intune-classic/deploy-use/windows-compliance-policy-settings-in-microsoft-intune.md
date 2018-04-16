---
title: "Einstellungen für Kompatibilitätsrichtlinien für Windows-Geräte"
description: "In diesem Thema werden die Regeln und Einstellungen beschrieben, die Sie für eine Konformitätsrichtlinie für Windows-Geräte konfigurieren können."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6a54943873a6af158badb92cef4610e54fc8889b
ms.sourcegitcommit: 2459bfda07a2afd2cfcd94a1972a3fb2e565ce8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="compliance-policy-settings-for-windows-devices-in-microsoft-intune"></a>Einstellungen für Kompatibilitätsrichtlinien für Windows Geräte in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Die in diesem Thema beschriebenen Richtlinieneinstellungen gelten für Geräte mit dem Windows-Betriebssystem. In den folgenden Abschnitten werden die unterstützten Windows-Versionen beschrieben.

Wenn Sie Informationen zu anderen Plattformen suchen, wählen Sie eine dieser Plattformen:
> [!div class="op_single_selector"]
> - [Einstellungen für Kompatibilitätsrichtlinien für iOS-Geräte](ios-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Android-Geräte](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Einstellungen für Kompatibilitätsrichtlinien für Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="compliance-policy-settings-for-windows-phone-devices"></a>Einstellungen für Kompatibilitätsrichtlinien für Windows Phone-Geräte
Die in diesem Abschnitt aufgeführten Einstellungen werden unter Windows Phone 8.1 und höher unterstützt.

### <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit
#### <a name="password"></a>Kennwort
- **Kennwort zum Entsperren mobiler Geräte erforderlich**: Legen Sie für diese Einstellung **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.

- **Einfache Kennwörter zulassen**: Legen Sie für diese Einstellung **Ja** fest, damit Benutzer einfache Kennwörter wie **1234** oder **1111** erstellen können.

-  **Minimale Kennwortlänge:** Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Erforderlicher Kennworttyp**: Geben Sie an, ob der Benutzer ein **alphanumerisches** oder ein **numerisches** Kennwort erstellen muss.

  Für Geräte unter Windows, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitätsrichtlinie nicht richtig ausgewertet, wenn die minimale Kennwortlänge größer als acht Zeichen oder die minimale Anzahl von Zeichensätzen größer als zwei ist.

- **Minimale Anzahl von Zeichensätzen:** Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
  -   Kleinbuchstaben
  -   Großbuchstaben
  -   Symbole
  -   Zahlen

  Wenn Sie eine höhere Anzahl für diese Einstellung festlegen, muss der Benutzer ein komplexeres Kennwort erstellen. Für Geräte unter Windows, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitätsrichtlinie nicht richtig ausgewertet, wenn die minimale Kennwortlänge größer als acht Zeichen oder die minimale Anzahl von Zeichensätzen größer als zwei ist.

- **Minuten der Inaktivität, bevor ein Kennwort erforderlich ist:** Diese Einstellung gibt die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft, und er ein neues erstellen muss.

- **Kennwortverlauf speichern**: Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.

- **Wiederverwendung vorheriger Kennwörter verhindern:** Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.
- **Kennworteingabe verlangen, wenn das Gerät aus dem Leerlauf zurückkehrt:** Verwenden Sie diese Einstellung zusammen mit der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts**. Der Benutzer wird zur Eingabe eines Kennworts aufgefordert, um auf ein Gerät zugreifen zu können, das für die in der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** angegebene Zeit inaktiv war.

  > [!NOTE]
  > Diese Einstellung gilt nur für Windows 10 Mobile-Geräte.

#### <a name="encryption"></a>Verschlüsselung
- **Verschlüsselung auf mobilen Geräten vorschreiben:** Legen Sie diese Einstellung auf **Ja** fest, damit das Gerät verschlüsselt werden muss, um eine Verbindung mit Ressourcen herzustellen.

### <a name="device-health-settings"></a>Einstellungen für die Geräteintegrität
- **Geräte müssen als fehlerfrei gemeldet werden:** Sie können eine Regel festlegen, die erfordert, dass **Windows 10 Mobile**-Geräte in neuen oder vorhandenen Kompatibilitätsrichtlinien als fehlerfrei gemeldet werden.  Wenn diese Einstellung aktiviert ist, werden Windows 10-Geräte über den Integritätsnachweisdienst (Health Attestation Service, HAS) für diese Datenpunkte ausgewertet:
  -  **BitLocker ist aktiviert:** Wenn BitLocker aktiviert ist, kann das Gerät auf dem Laufwerk gespeicherte Daten vor unbefugtem Zugriff schützen, wenn das System ausgeschaltet wird, oder in den Ruhezustand wechselt. Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet das TPM zum Schutz des Windows-Betriebssystems und der Benutzerdaten. BitLocker stellt auch sicher, dass ein Computer nicht manipuliert wird, selbst wenn dieser unbeaufsichtigt ist, verloren gegangen ist, oder gestohlen wurde. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann auf die Schlüssel nicht zugegriffen werden, bis das TPM den Zustand des Computers überprüft hat.
  -  **Codeintegrität ist aktiviert:** Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird. Die Codeintegrität erkennt, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird. Sie erkennt auch, ob eine Systemdatei durch böswillige Software manipuliert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
  - **Sicherer Start ist aktiviert**: Wenn der sichere Start aktiviert ist, wird das System gezwungen, in einem vertrauenswürdigen Zustand zu starten. Wenn der sichere Start aktiviert ist, müssen die zum Starten des Computers verwendeten Kernkomponenten zudem über die richtigen kryptografischen Signaturen verfügen, denen das Unternehmen vertraut, das das Gerät hergestellt hat. Dies wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien manipuliert wurden und dadurch die Signatur ungültig ist, wird das System nicht gestartet.

  > [!IMPORTANT]
  > Windows-Geräte unterstützen keine Software für **Antischadstoff-Frühstarts** (Early Launch Anti Malware, ELAM) von Drittanbietern, die im Rahmen des Nachweises der Geräteintegrität installiert wurden.

  Informationen zur Funktionsweise des HAS-Diensts finden Sie unter [Integritätsnachweis-CSP](https://msdn.microsoft.com/library/dn934876.aspx).
  ###  <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften
- **Minimal erforderliches Betriebssystem**: Wenn ein Gerät die Anforderungen an die erforderliche Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht kompatibel gemeldet.
    Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Benutzer kann ein Upgrade des Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion**: Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.


## <a name="compliance-policy-settings-for-windows-pcs"></a>Einstellungen für Kompatibilitätsrichtlinien für Windows-PCs
Die in diesem Abschnitt aufgeführten Einstellungen werden auf Windows-PCs unterstützt.
### <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit
#### <a name="password"></a>Kennwort
- **Minimale Kennwortlänge**: Wird unter Windows 8.1 unterstützt.

  Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.

  Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitätsrichtlinie nicht richtig ausgewertet, wenn **Minimale Kennwortlänge** größer als acht Zeichen oder **Minimale Anzahl von Zeichensätzen** größer als zwei Zeichensätze ist.

- **Erforderlicher Kennworttyp**: Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Geben Sie an, ob der Benutzer ein **alphanumerisches** oder ein **numerisches** Kennwort erstellen muss.

- **Minimale Anzahl von Zeichensätzen**: Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl an Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
  -   Kleinbuchstaben
  -   Großbuchstaben
  -   Symbole
  -   Zahlen     

  Wenn Sie eine höhere Anzahl für diese Einstellung festlegen, muss der Benutzer ein komplexeres Kennwort erstellen. Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitätsrichtlinie nicht richtig ausgewertet, wenn **Minimale Kennwortlänge** größer als acht Zeichen oder **Minimale Anzahl von Zeichensätzen** größer als zwei Zeichensätze ist.

- **Minuten Inaktivität vor erneuter Anforderung des Kennworts**: Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage)**: Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Wählen Sie die Anzahl der Tage aus, bevor das Kennwort des Benutzers abläuft, und er ein neues erstellen muss.

- **Kennwortverlauf speichern**: Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.

- **Wiederverwendung vorheriger Kennwörter verhindern**: Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

  Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.

### <a name="device-health-settings"></a>Einstellungen für die Geräteintegrität
- **Geräte müssen als fehlerfrei gemeldet werden**: Wird auf Windows 10-Geräten unterstützt.
Sie können eine Regel festlegen, die erfordert, dass Windows 10-Geräte in neuen oder vorhandenen Konformitätsrichtlinien als fehlerfrei gemeldet werden. Wenn diese Einstellung aktiviert ist, werden Windows 10-Geräte über den Integritätsnachweisdienst (Health Attestation Service, HAS) für die folgenden Datenpunkte ausgewertet:
  -  **BitLocker ist aktiviert:** Wenn BitLocker aktiviert ist, kann das Gerät auf dem Laufwerk gespeicherte Daten vor unbefugtem Zugriff schützen, wenn das System ausgeschaltet wird, oder in den Ruhezustand wechselt. Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet das TPM zum Schutz des Windows-Betriebssystems und der Benutzerdaten. BitLocker stellt auch sicher, dass ein Computer nicht manipuliert wird, selbst wenn dieser unbeaufsichtigt ist, verloren gegangen ist, oder gestohlen wurde. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann auf die Schlüssel nicht zugegriffen werden, bis das TPM den Zustand des Computers überprüft hat.
  -  **Codeintegrität ist aktiviert:** Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird. Die Codeintegrität erkennt, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird. Sie erkennt auch, ob eine Systemdatei durch böswillige Software manipuliert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
  - **Sicherer Start ist aktiviert**: Wenn der sichere Start aktiviert ist, wird das System gezwungen, in einem vertrauenswürdigen Zustand zu starten. Wenn der sichere Start aktiviert ist, müssen die zum Starten des Computers verwendeten Kernkomponenten zudem über die richtigen kryptografischen Signaturen verfügen, denen das Unternehmen vertraut, das das Gerät hergestellt hat. Dies wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien manipuliert wurden und dadurch die Signatur ungültig ist, wird das System nicht gestartet.
  - **Antischadsoftware-Frühstart ist aktiviert**: Der Antischadsoftware-Frühstart (Early Launch Anti-Malware, ELAM) bietet für die Computer im Netzwerk den entsprechenden Schutz beim Start, bevor Treiber von Drittanbietern gestartet werden können.

  Informationen zur Funktionsweise des HAS-Diensts finden Sie unter [Integritätsnachweis-CSP](https://msdn.microsoft.com/library/dn934876.aspx).

### <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften
- **Minimal erforderliches Betriebssystem**: Wird unter Windows 8.1 und Windows 10 unterstützt.

  Geben Sie hier die Hauptversion.Nebenversion.Buildnummer an. Die Versionsnummer muss derjenigen entsprechen, die durch den **winver**-Befehl zurückgegeben wird.

  Wenn ein Gerät eine frühere Version als die angegebene Betriebssystemversion aufweist, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Benutzer kann ein Upgrade des Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion**: Wird unter Windows 8.1 und Windows 10 unterstützt.

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

Um die Betriebssystemversion für die Einstellungen **Minimal erforderliches Betriebssystem** und **Maximal zulässige Betriebssystemversion** zu finden, führen Sie den **winver**-Befehl an der Eingabeaufforderung aus. Der **winver**-Befehl gibt die gemeldete Version des Betriebssystems zurück.

- Windows 8.1-PCs geben die Version **6.3** zurück. Wenn die Regel für die Betriebssystemversion für Windows auf Windows 8.1 festgelegt ist, wird das betreffende Gerät als nicht kompatibel gemeldet, selbst wenn auf ihm Windows 8.1 installiert ist.

- Bei PCs unter Windows 10 muss die Version auf **10.0** plus Buildnummer des Betriebssystems festgelegt werden, die vom **winver**-Befehl zurückgegeben wird. Beispiel: 10.0.10586.
  > ![Die Buildversion des Betriebssystems wird im Dialogfeld „Info“ markiert](./media/ca_win10-os-version.png)
