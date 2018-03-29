---
title: Erstellen einer Konformitätsrichtlinie für Windows-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen einer Konformitätsrichtlinie für Windows-Geräte in Microsoft Intune, damit Sie die Anforderungen angeben können, die ein Gerät für die Konformität erfüllen muss.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 211b3c94dd7172d1755e3c12bb4d90dbcf28750d
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-windows-devices-in-intune"></a>Erstellen einer Gerätekonformitätsrichtlinie für Windows-Geräte in Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Eine Intune-Konformitätsrichtlinie für Windows-Geräte gibt die Regeln und Einstellungen an, die Windows-Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können diese Richtlinien mit bedingtem Zugriff verwenden, um Zugriff auf Unternehmensressourcen zu gewähren oder zu blockieren. Sie können auch Berichte zu Geräten abrufen und Maßnahmen gegen die Nichtkonformität vornehmen. Erstellen Sie Gerätekonformitätsrichtlinien für jede Plattform im Intune Azure-Portal. Weitere Informationen über Konformitätsrichtlinien und die Voraussetzungen, die vor dem Erstellen einer Konformitätsrichtlinie erfüllt werden müssen, finden Sie unter [Erste Schritte mit den Microsoft Intune-Gerätekonformitätsrichtlinien](device-compliance-get-started.md).

In der folgenden Tabelle wird beschrieben, wie nicht konforme Einstellungen verwaltet werden, wenn eine Konformitätsrichtlinie mit einer Richtlinie für bedingten Zugriff verwendet wird.

---------------------------

| **Richtlinieneinstellung** | **Windows 8.1 und höher** | **Windows Phone 8.1 und höher** |
|----| ----| --- |
| **PIN- oder Kennwortkonfiguration** | Wiederhergestellt | Wiederhergestellt |   
| **Geräteverschlüsselung** | Nicht verfügbar | Wiederhergestellt |   
| **Per Jailbreak oder Rootzugriff manipuliertes Gerät** | Nicht verfügbar | Nicht verfügbar |  
| **E-Mail-Profil** | Nicht verfügbar | Nicht verfügbar |   
| **Minimale Version des Betriebssystems** | Isoliert | Isoliert |   
| **Maximale Version des Betriebssystems** | Isoliert | Isoliert |   
| **Windows-Integritätsnachweis** | Isoliert: Windows 10 und Windows 10 Mobile|Nicht verfügbar: Windows 8.1 |

-------------------------------

**Wiederhergestellt** = Das Betriebssystem des Geräts erzwingt die Kompatibilität. (Beispiel: Der Benutzer ist gezwungen, eine PIN festzulegen.)

**Isoliert** = Das Betriebssystem des Geräts erzwingt keine Kompatibilität. (Beispiel: Android-Geräte zwingen den Benutzer nicht, das Gerät zu verschlüsseln.) Wenn das Gerät nicht kompatibel ist, erfolgen die folgenden Aktionen:

- Das Gerät wird blockiert, wenn eine Richtlinie für bedingten Zugriff für den Benutzer gilt.
- Das Unternehmensportal benachrichtigt den Benutzer über Kompatibilitätsprobleme.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Erstellen einer Konformitätsrichtlinie im Azure-Portal

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Klicken Sie auf **Alle Dienste** > **Intune**. Intune befindet sich im Abschnitt **Überwachung + Verwaltung**.
1. Klicken Sie im Bereich **Intune** auf die Option **Gerätekonformität**. Klicken Sie unter **Verwalten** auf **Richtlinien** > **Richtlinie erstellen**.
2. Geben Sie einen Namen und eine Beschreibung ein, und wählen Sie die Plattform aus, auf die Sie diese Richtlinie anwenden möchten.
3. Klicken Sie auf **Einstellungen konfigurieren**, um die Einstellungen zur **Systemsicherheit**, **Device Health** (Integrität für Geräte) und **Geräteeigenschaften** anzugeben. Wählen Sie abschließend **OK** aus.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Zuweisen von Benutzergruppen

Wählen Sie zum Zuweisen einer Konformitätsrichtlinie zu Benutzern eine Richtlinie aus, die Sie konfiguriert haben. Vorhandene Richtlinien finden Sie im Bereich **Gerätekompatibilität > Richtlinien**.

1. Wählen Sie die Richtlinie, die Sie Benutzern zuweisen möchten, und abschließend **Zuweisungen** aus. Damit öffnen Sie den Bereich, in dem Sie **Azure Active Directory-Sicherheitsgruppen** auswählen und der Richtlinie zuweisen können.
2. Klicken Sie auf **Ausgewählte Gruppen**, um den Bereich mit den Azure AD-Sicherheitsgruppen zu öffnen.  Die Auswahl von **Speichern** bewirkt die Bereitstellung der Richtlinie für Benutzer.

Sie haben die Richtlinie auf Benutzer angewendet. Die von den Benutzern, denen die Richtlinie zugewiesen wurde, verwendeten Geräte werden auf Konformität überprüft.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte erforderlich:** Legen Sie für diese Einstellung **Ja** fest, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Einfache Kennwörter zulassen**: Legen Sie **Ja** fest, damit Benutzer einfache Kennwörter wie „**1234**“ oder „**1111**“ erstellen können.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.
- **Erforderlicher Kennworttyp:** Geben Sie an, ob Benutzer ein **alphanumerisches** oder ein **numerisches** Kennwort erstellen müssen.

Für Geräte unter Windows, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie nicht richtig ausgewertet, wenn die minimale Kennwortlänge größer als acht Zeichen oder die minimale Anzahl von Zeichensätzen größer als zwei ist.

- **Minimale Anzahl von Zeichensätzen:** Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
  - Kleinbuchstaben
  - Großbuchstaben
  - Symbole
  - Zahlen

Wenn Sie eine höhere Zahl für diese Einstellung festlegen, müssen Benutzer komplexere Kennwörter erstellen. Für Geräte unter Windows, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie nicht richtig ausgewertet, wenn die minimale Kennwortlänge größer als acht Zeichen oder die minimale Anzahl von Zeichensätzen größer als zwei ist.

- **Minuten der Inaktivität, bevor ein Kennwort erforderlich ist:** Gibt die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage)**: Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort des Benutzers abläuft und er ein neues erstellen muss.
- **Kennwortverlauf speichern:** Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.
- **Wiederverwendung vorheriger Kennwörter verhindern:** Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.
- **Kennworteingabe verlangen, wenn das Gerät aus dem Leerlauf zurückkehrt:** Diese Einstellung sollte zusammen mit der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** verwendet werden. Die Endbenutzer werden zur Eingabe eines Kennworts aufgefordert, um auf ein Gerät zugreifen zu können, das für die in der Einstellung **Minuten Inaktivität vor erneuter Anforderung des Kennworts** angegebene Zeit inaktiv war.

**Diese Einstellung gilt nur für Windows 10 Mobile-Geräte.**

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung auf mobilen Geräten vorschreiben:** Legen Sie diese Einstellung auf **Ja** fest, damit das Gerät verschlüsselt werden muss, um eine Verbindung mit Ressourcen herzustellen.



## <a name="device-health-settings"></a>Einstellungen für die Geräteintegrität

- **Geräte müssen als fehlerfrei gemeldet werden:** Sie können eine Regel festlegen, die erfordert, dass **Windows 10 Mobile**-Geräte in neuen oder vorhandenen Kompatibilitätsrichtlinien als fehlerfrei gemeldet werden. Wenn diese Einstellung aktiviert ist, werden Windows 10-Geräte über den Integritätsnachweisdienst (Health Attestation Service, HAS) für die folgenden Datenpunkte ausgewertet:
  - **BitLocker ist aktiviert:** Wenn BitLocker aktiviert ist, kann das Gerät auf dem Laufwerk gespeicherte Daten vor unbefugtem Zugriff schützen, wenn das System ausgeschaltet wird oder in den Ruhezustand wechselt. Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet TPM zum Schutz des Windows-Betriebssystems und der Benutzerdaten und stellt damit sicher, dass ein Computer nicht manipuliert wird, selbst wenn dieser unbeaufsichtigt ist, verloren geht oder gestohlen wird. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann auf die Schlüssel nicht zugegriffen werden, bis das TPM den Zustand des Computers überprüft hat.
  - **Codeintegrität ist aktiviert:** Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird. Die Codeintegrität erkennt, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird, oder ob eine Systemdatei durch böswillige Software manipuliert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
  - **Sicherer Start ist aktiviert:** Wenn der sichere Start aktiviert ist, wird das System gezwungen, in einem vertrauenswürdigen Zustand zu starten. Wenn der sichere Start aktiviert ist, müssen die zum Starten des Computers verwendeten Kernkomponenten zudem über die richtigen kryptografischen Signaturen verfügen, denen das Unternehmen vertraut, das das Gerät hergestellt hat. Dies wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien manipuliert wurden und dadurch die Signatur ungültig ist, wird das System nicht gestartet.

Informationen zur Funktionsweise des HAS-Diensts finden Sie unter [Integritätsnachweis-CSP](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimal erforderliches Betriebssystem:** Wenn ein Gerät die Anforderungen für die minimal erforderliche Betriebssystemversion nicht erfüllt, wird es als nicht kompatibel gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Die Endbenutzer können ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion:** Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

<!---## Compliance policy settings for Windows PCs--->

## <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

### <a name="password"></a>Kennwort

- **Minimale Kennwortlänge:** Wird unter Windows 8.1 unterstützt.

Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Benutzerkennwort enthalten muss.

Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitätsrichtlinie nicht richtig ausgewertet, wenn **Minimale Kennwortlänge** größer als acht Zeichen oder **Minimale Anzahl von Zeichensätzen** größer als zwei Zeichensätze ist.

- **Erforderlicher Kennworttyp:** Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

Geben Sie an, ob Benutzer ein **alphanumerisches** oder ein **numerisches** Kennwort erstellen müssen.

- **Minimale Anzahl von Zeichensätzen:** Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt. Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl an Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
  - Kleinbuchstaben
  - Großbuchstaben
  - Symbole
  - Zahlen: Wenn Sie eine höhere Zahl für diese Einstellung festlegen, müssen Benutzer komplexere Kennwörter erstellen.

Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitätsrichtlinie nicht richtig ausgewertet, wenn **Minimale Kennwortlänge** größer als acht Zeichen oder **Minimale Anzahl von Zeichensätzen** größer als zwei Zeichensätze ist.

- **Minuten Inaktivität vor erneuter Anforderung des Kennworts:** Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):** Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

Wählen Sie die Anzahl der Tage, bevor das Kennwort des Benutzers abläuft und er ein neues erstellen muss.

- **Kennwortverlauf speichern:** Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

Verwenden Sie diese Einstellung in Verbindung mit **Wiederverwendung vorheriger Kennwörter verhindern**, um zu verhindern, dass der Benutzer zuvor bereits verwendete Kennwörter erstellt.

- **Wiederverwendung vorheriger Kennwörter verhindern:** Wird unter Windows RT, Windows RT 8.1 und Windows 8.1 unterstützt.

Wenn **Kennwortverlauf speichern** aktiviert ist, geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden dürfen.


## <a name="device-health-settings"></a>Einstellungen für die Geräteintegrität

- **Geräte müssen als fehlerfrei gemeldet werden:** Wird auf Windows 10-Geräten unterstützt. Sie können eine Regel festlegen, die erfordert, dass Windows 10-Geräte in neuen oder vorhandenen Konformitätsrichtlinien als fehlerfrei gemeldet werden. Wenn diese Einstellung aktiviert ist, werden Windows 10-Geräte über den Integritätsnachweisdienst (Health Attestation Service, HAS) für die folgenden Datenpunkte ausgewertet:
  - **BitLocker ist aktiviert:** Wenn BitLocker aktiviert ist, kann das Gerät auf dem Laufwerk gespeicherte Daten vor unbefugtem Zugriff schützen, wenn das System ausgeschaltet wird oder in den Ruhezustand wechselt. Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet TPM zum Schutz des Windows-Betriebssystems und der Benutzerdaten und stellt damit sicher, dass ein Computer nicht manipuliert wird, selbst wenn dieser unbeaufsichtigt ist, verloren geht oder gestohlen wird. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann auf die Schlüssel nicht zugegriffen werden, bis das TPM den Zustand des Computers überprüft hat.
  - **Codeintegrität ist aktiviert:** Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird. Die Codeintegrität erkennt, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird, oder ob eine Systemdatei durch böswillige Software manipuliert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
  - **Sicherer Start ist aktiviert:** Wenn der sichere Start aktiviert ist, wird das System gezwungen, in einem vertrauenswürdigen Zustand zu starten. Wenn der sichere Start aktiviert ist, müssen die zum Starten des Computers verwendeten Kernkomponenten zudem über die richtigen kryptografischen Signaturen verfügen, denen das Unternehmen vertraut, das das Gerät hergestellt hat. Dies wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien manipuliert wurden und dadurch die Signatur ungültig ist, wird das System nicht gestartet.
  - **Antischadsoftware-Frühstart ist aktiviert:** Der Antischadsoftware-Frühstart (Early Launch Anti-Malware, ELAM) bietet für die Computer im Netzwerk den entsprechenden Schutz beim Start, bevor Treiber von Drittanbietern gestartet werden können.

Informationen zur Funktionsweise des HAS-Diensts finden Sie unter [Integritätsnachweis-CSP](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Einstellungen für Geräteeigenschaften

- **Minimal erforderliches Betriebssystem:** Wird unter Windows 8.1 und Windows 10 unterstützt.

Geben Sie hier die Hauptversion, Nebenversion, Buildnummer und das kumulative Update an. Die Versionsnummer muss derjenigen entsprechen, die durch den Befehl ```winver``` zurückgegeben wird.

Wenn ein Gerät eine frühere Version als die angegebene Betriebssystemversion aufweist, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Die Endbenutzer können ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion:** Wird unter Windows 8.1 und Windows 10 unterstützt.

Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

Um die Betriebssystemversion für die Einstellungen **Minimal erforderliches Betriebssystem** und **Maximal zulässige Betriebssystemversion** zu finden, führen Sie den **winver**-Befehl an der Eingabeaufforderung aus. Der winver-Befehl gibt die gemeldete Version des Betriebssystems zurück.

- Windows 8.1-PCs geben die Version **3** zurück. Wenn die Regel für die Betriebssystemversion für Windows auf Windows 8.1 festgelegt ist, wird das betreffende Gerät als nicht kompatibel gemeldet, selbst wenn auf ihm Windows 8.1 installiert ist.
- Bei PCs unter Windows 10 muss die Version auf „10.0“ plus Buildnummer des Betriebssystems festgelegt werden, die vom winver-Befehl zurückgegeben wird.

## <a name="windows-holographic-for-business-support"></a>Unterstützung durch Windows Holographic for Business

Windows Holographic for Business unterstützt die folgende Einstellung:

- Systemsicherheit/Verschlüsselung

  **Verschlüsselung des Datenspeichers auf dem Gerät**.

Informationen zur Überprüfung der Geräteverschlüsselung unter Microsoft HoloLens finden Sie unter [Überprüfen der Geräteverschlüsselung](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="next-steps"></a>Nächste Schritte

Über den folgenden Link erhalten Sie Informationen zum Überwachen der Gerätekonformität:

- [Überwachen der Gerätekonformität](device-compliance-monitor.md)
