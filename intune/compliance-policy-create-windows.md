---
title: Erstellen einer Konformitätsrichtlinie für Windows-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen oder konfigurieren Sie eine Microsoft Intune-Gerätekonformitätsrichtlinie für Windows Phone 8.1, Windows 8.1 und höher sowie Windows 10 und höher. Überprüfen Sie die Konformität des minimalen und maximalen Betriebssystems, legen Sie Kennwortbeschränkungen und -längen fest, fordern Sie BitLocker an, stellen Sie die akzeptable Bedrohungsstufe ein, und aktivieren Sie die Datenspeicherung, einschließlich Surface Hub und Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bb79a6c18ff8b6eec20f4ce8813d8dea188215e7
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Hinzufügen einer Gerätekonformitätsrichtlinie für Windows-Geräte in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Eine Intune-Konformitätsrichtlinie für Windows-Geräte gibt die Regeln und Einstellungen an, die Windows-Geräte erfüllen müssen, um als konform angesehen zu werden. Sie können diese Richtlinien mit bedingtem Zugriff verwenden, um den Zugriff auf Unternehmensressourcen zuzulassen oder zu blockieren. Außerdem können Sie Geräteberichte abrufen und bei Nichtkonformität Aktionen durchführen. Erstellen Sie Gerätekonformitätsrichtlinien für jede Plattform im Intune Azure-Portal. Weitere Informationen über Konformitätsrichtlinien und alle Voraussetzungen finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

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

## <a name="create-a-device-compliance-policy"></a>Erstellen einer Gerätekonformitätsrichtlinie

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Wählen Sie als **Plattform** die Option **Windows Phone 8.1**, **Windows 8.1 und höher** oder **Windows 10 und höher** aus.
6. Wählen Sie **Einstellungen konfigurieren**, um die Einstellungen zu **Geräteintegrität**, **Geräteeigenschaften** und **Systemsicherheit** anzugeben. Wenn Sie fertig sind, wählen Sie **OK** und dann **Erstellen**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Richtlinieneinstellungen für Windows 8.1-Geräte

Diese Richtlinieneinstellungen gelten für Geräte mit den folgenden Plattformen:

- Windows Phone 8.1
- Windows 8.1 und höher

### <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliches Betriebssystem:** Wenn ein Gerät die Anforderungen für die minimal erforderliche Betriebssystemversion nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximal zulässige Betriebssystemversion**: Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

Windows 8.1-PCs geben die Version **3** zurück. Wenn die Regel für die Betriebssystemversion für Windows auf Windows 8.1 festgelegt ist, wird das betreffende Gerät als nicht kompatibel gemeldet, selbst wenn auf ihm Windows 8.1 installiert ist.

### <a name="system-security"></a>Systemsicherheit

#### <a name="password"></a>Kennwort

- **Kennwort zum Entsperren mobiler Geräte anfordern:** Klicken Sie auf **Erforderlich**, damit Benutzer ein Kennwort eingeben müssen, um auf ihre Geräte zugreifen zu können.
- **Einfache Kennwörter:** Legen Sie **Blockieren** fest, damit Benutzer kein einfaches Kennwort wie **1234** oder **1111** erstellen können. Wenn Sie diese Option auf **Nicht konfiguriert** setzen, können Benutzer Kennwörter wie **1234** oder **1111** erstellen.
- **Minimale Kennwortlänge**: Geben Sie die Mindestanzahl an Ziffern oder Zeichen an, die das Kennwort enthalten muss.

  Für Geräte, die unter Windows laufen und auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie in diesem Fällen nicht korrekt ausgewertet:
  - Wenn die minimale Kennwortlänge mehr als acht Zeichen umfasst.
  - Oder, wenn die minimale Anzahl von Zeichensätzen mehr als zwei ist.

- **Kennworttyp**: Wählen Sie diese Option, wenn ein Kennwort nur aus **numerischen** Zeichen bestehen soll, oder wenn eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).
  
  - **Anzahl nicht alphanumerischer Zeichen im Kennwort**: Wenn **Erforderlicher Kennworttyp** auf **Alphanumerisch** festgelegt ist, gibt diese Einstellung die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Es gibt vier Zeichensätze:
    - Kleinbuchstaben
    - Großbuchstaben
    - Symbole
    - Zahlen

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen. Für Geräte unter Windows, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie nicht richtig ausgewertet, wenn die minimale Kennwortlänge größer als acht Zeichen oder die minimale Anzahl von Zeichensätzen größer als zwei ist.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen.

#### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung auf mobilem Gerät anfordern**: Sie können **Erforderlich** festlegen, sodass das Gerät verschlüsselt sein muss, um eine Verbindung mit Datenspeicherressourcen herstellen zu können.

## <a name="windows-10-and-later-policy-settings"></a>Richtlinieneinstellungen für Windows 10 und höher

### <a name="device-health"></a>Device health

- **BitLocker erforderlich**: Wenn BitLocker aktiviert ist, kann das Gerät Daten, die auf dem Laufwerk gespeichert sind, vor unbefugtem Zugriff schützen, wenn das Gerät ausgeschaltet wird oder in den Ruhezustand wechselt. Die Windows BitLocker-Laufwerksverschlüsselung verschlüsselt alle auf einem Volume mit Windows-Betriebssystem gespeicherten Daten. BitLocker verwendet das TPM zum Schutz des Windows-Betriebssystems und der Benutzerdaten. Zudem stellt TPM sicher, dass ein Computer auch dann nicht manipuliert wird, wenn er unbeaufsichtigt gelassen, verloren oder gestohlen wird. Wenn der Computer mit einem kompatiblen TPM ausgestattet ist, verwendet BitLocker das TPM zum Sperren der Verschlüsselungsschlüssel, die die Daten schützen. Daher kann auf die Schlüssel nicht zugegriffen werden, bis das TPM den Zustand des Computers überprüft hat.
- **Sicherer Start muss auf dem Gerät aktiviert sein**: Wenn der sichere Start aktiviert ist, wird das System gezwungen, in einem vertrauenswürdigen Zustand zu starten. Wenn der sichere Start aktiviert ist, müssen die zum Starten des Computers verwendeten Kernkomponenten zudem über die richtigen kryptografischen Signaturen verfügen, denen das Unternehmen vertraut, das das Gerät hergestellt hat. Die Signatur wird von der UEFI-Firmware überprüft, bevor der Computer gestartet werden kann. Wenn Dateien manipuliert wurden und dadurch die Signatur ungültig ist, wird das System nicht gestartet.
- **Codeintegrität erforderlich**: Die Codeintegrität ist ein Feature, das die Integrität eines Treibers oder einer Systemdatei jedes Mal überprüft, wenn diese(r) in den Speicher geladen wird. Die Codeintegrität erkennt, ob ein nicht signierter Treiber oder eine Systemdatei in den Kernel geladen wird. Oder, ob eine Systemdatei durch böswillige Software manipuliert wurde, die von einem Benutzerkonto mit Administratorrechten ausgeführt wird.
- **Anfordern, dass das Gerät höchstens der angegebenen Gerätebedrohungsstufe entspricht**: Verwenden Sie diese Einstellung, um die Risikobewertung Ihrer Dienste zur Verteidigung gegen Bedrohungen als Konformitätsvoraussetzung zu fordern. Wählen Sie die maximal zulässige Bedrohungsstufe:
  - **Gesichert**: Diese Option ist die sicherste, da auf dem Gerät keine Bedrohungen vorhanden sein können. Wenn auf dem Gerät Bedrohungen jeglicher Stufen erkannt werden, wird es als nicht konform bewertet.
  - **Niedrig**: Das Gerät wird als kompatibel bewertet, wenn nur Bedrohungen niedriger Stufen vorliegen. Durch Bedrohungen höherer Stufen wird das Gerät in einen nicht kompatiblen Status versetzt.
  - **Mittel**: Das Gerät wird als kompatibel bewertet, wenn die auf dem Gerät vorhandenen Bedrohungen niedriger oder mittlerer Stufe sind. Wenn auf dem Gerät Bedrohungen hoher Stufen erkannt werden, wird es als nicht kompatibel bewertet.
  - **Hoch**: Dies ist die am wenigsten sichere Option, die alle Bedrohungsebenen zulässt. Es ist möglicherweise hilfreich, diese Lösung nur zu Berichtszwecken zu verwenden.

Informationen zur Funktionsweise des HAS-Diensts finden Sie unter [Integritätsnachweis-CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).

### <a name="device-properties"></a>Geräteeigenschaften

- **Minimal erforderliches Betriebssystem**: Geben Sie die Zahl für major.minor.build.CU ein. Die build.CU-Nummer muss der Version entsprechen, die durch den Befehl `ver` oder `winver` zurückgegeben wird.

  Wenn ein Gerät eine frühere Version als die angegebene Betriebssystemversion aufweist, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Die Endbenutzer können ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal zulässige Betriebssystemversion**: Geben Sie die Zahl für major.minor.build.CU ein. Die build.CU-Nummer muss der Version entsprechen, die durch den Befehl `ver` oder `winver` zurückgegeben wird.

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Minimal erforderliches Betriebssystem für mobile Geräte**: Geben Sie die Zahl für major.minor.build ein.

  Wenn ein Gerät eine frühere Version als die angegebene Betriebssystemversion aufweist, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Die Endbenutzer können ein Upgrade des Geräts durchführen und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximal erforderliches Betriebssystem für mobile Geräte**: Geben Sie die Zahl für major.minor.build ein.

  Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt, und der Benutzer wird gebeten, sich an den IT-Administrator zu wenden. Mit diesem Gerät kann solange nicht auf Unternehmensressourcen zugegriffen werden, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

- **Gültige Betriebssystembuilds**: Geben Sie einen Bereich für die zulässigen Betriebssystemversionen ein, einschließlich eines Minimums und eines Maximums.

### <a name="system-security-settings"></a>Einstellungen für die Systemsicherheit

#### <a name="password"></a>Kennwort

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
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl von vorherigen Kennwörtern an, die nicht erneut verwendet werden dürfen.
- **Kennwort anfordern, wenn Gerät aus Leerlaufzustand zurückkehrt (Mobile und Holographic)**: Erzwingen Sie die Eingabe des Kennworts, wenn das Gerät aus dem Leerlaufzustand zurückkehrt.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf einem Gerät**: Wählen Sie **Erforderlich**, um den Datenspeicher auf Ihren Geräten zu verschlüsseln.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business verwendet die Plattform **Windows 10 und höher**. Windows Holographic for Business unterstützt die folgende Einstellung:

- **Systemsicherheit** > **Verschlüsselung** > **Verschlüsselung des Datenspeichers auf dem Gerät**.

Informationen zur Überprüfung der Geräteverschlüsselung unter Microsoft HoloLens finden Sie unter [Überprüfen der Geräteverschlüsselung](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
Surface Hub verwendet die Plattform **Windows 10 und höher**. Surface Hub-Geräte werden sowohl für Konformität als auch für bedingten Zugriff unterstützt. Um diese Funktionen auf Surface Hub-Geräten zu aktivieren, wird empfohlen, die [automatische Registrierung von Windows 10](windows-enroll.md) in Intune zu aktivieren (erfordert auch Azure Active Directory (AAD)) und die Surface Hub-Geräte als Gerätegruppen anzusprechen. Surface Hub-Geräte müssen mit Azure Active Directory verbunden sein, um die Konformität und den bedingten Zugriff auf die Funktion zu gewährleisten.

Eine Anleitung finden Sie unter [Registrierung von Windows-Geräten](windows-enroll.md).

## <a name="assign-user-or-device-groups"></a>Zuweisen von Benutzer- oder Gerätegruppen

1. Wählen Sie eine Richtlinie, die Sie konfiguriert haben. Vorhandene Richtlinien befinden sich unter **Gerätekompatibilität** > **Richtlinien**.
2. Wählen Sie die Richtlinie und dann **Zuweisungen** aus. Sie können Azure AD-Sicherheitsgruppen ein- oder ausschließen.
3. Wählen Sie **Ausgewählte Gruppen**, um Ihre Azure AD-Sicherheitsgruppen anzuzeigen. Wählen Sie die Benutzer- oder Gerätegruppen aus, auf die diese Richtlinie angewendet werden soll, und wählen Sie dann **Speichern**, um die Richtlinie bereitzustellen.

Sie haben die Richtlinie angewendet. Die von den Benutzern verwendeten Geräte, denen die Richtlinie zugewiesen wurde, werden auf Konformität überprüft.

## <a name="next-steps"></a>Nächste Schritte
[Automatisieren von E-Mails und Hinzufügen von Aktionen für nicht konforme Geräte](actions-for-noncompliance.md)  
[Überwachen von Intune-Richtlinien zur Gerätekompatibilität](compliance-policy-monitor.md)
