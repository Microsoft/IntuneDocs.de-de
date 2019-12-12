---
title: Windows 8.1-Konformitätseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Windows 8.1- und Windows Phone 8.1-Geräte in Microsoft Intune festzulegen. Überprüfen Sie die Konformität mit der minimalen und maximalen Betriebssystemversion, legen Sie Kennwortbeschränkungen und -länge fest, aktivieren Sie die Verschlüsselung der Datenspeicherung und vieles mehr.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813215"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 8.1-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für Windows 8.1-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) können Sie mit diesen Einstellungen einfache Kennwörter blockieren, eine minimale oder maximale Betriebssystemversion festlegen und vieles mehr.

Diese Funktion gilt für:

- Windows Phone 8.1
- Windows 8.1 und höher

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **Windows Phone 8.1** oder **Windows 8.1 und höher**aus.

## <a name="device-properties"></a>Geräteeigenschaften

### <a name="operating-system-version"></a>Version des Betriebssystems

**Windows Phone (8.1 oder höher)**
- **Mindestversion des Betriebssystems für mobile Geräte**:  
  Geben Sie die zulässige Mindestversion ein. Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Gerätebenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximale Betriebssystemversion für mobile Geräte**:  
  Geben Sie die maximal zulässige Version ein. Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die in der Regel eingegebene Version, wird der Zugriff auf Organisationsressourcen gesperrt. Der Gerätebenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

**Windows 8.1 und höher**
- **Mindestversion des Betriebssystems**:  
  Geben Sie die zulässige Mindestversion ein. Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Gerätebenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.

- **Maximale Version des Betriebssystems**:  
  Geben Sie die maximal zulässige Version ein. Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die in der Regel eingegebene Version, wird der Zugriff auf Organisationsressourcen gesperrt. Der Gerätebenutzer wird aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann solange nicht auf Organisationsressourcen zugreifen, bis die Regel geändert und die betreffende Betriebssystemversion zugelassen wird.

Windows 8.1-PCs geben die Version **3** zurück. Wenn die Regel für die Betriebssystemversion für Windows auf Windows 8.1 festgelegt ist, wird das betreffende Gerät als nicht kompatibel gemeldet, selbst wenn auf ihm Windows 8.1 installiert ist.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

- **Anfordern eines Kennworts zum Entsperren mobiler Geräte:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Diese Einstellung wird nicht für die Konformitätsprüfung ausgewertet.
  - **Erforderlich**: Benutzer müssen ein Kennwort eingeben, bevor sie auf ihr Gerät zugreifen können.

- **Einfache Kennwörter:**  
  - **Nicht konfiguriert** (*Standardeinstellung*): Benutzer können einfache Kenn Wörter wie **1234** oder **1111**erstellen.
  - **Blockieren**: Benutzer können kein einfaches Kennwort wie **1234** oder **1111** erstellen.  

- **Minimale Kennwortlänge:**  
  Geben Sie die Mindestanzahl an Ziffern oder Zeichen ein, die das Kennwort enthalten muss.

  Bei Geräten, auf denen Windows ausgeführt wird und auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitäts Richtlinie nicht richtig ausgewertet, wenn eine der folgenden Bedingungen erfüllt ist:  
  - Minimale Kennwortlänge umfasst mehr als acht Zeichen.
  - Minimale Anzahl von Zeichensätzen ist mehr als zwei.

- **Kennworttyp**:  
  Wählen Sie aus, ob ein Kennwort nur aus **numerischen** Zeichen bestehen oder eine Kombination aus Zahlen und anderen Zeichen verwendet werden soll (**alphanumerisch**).

  Wenn *alphanumerisch*festgelegt ist, ist die folgende Einstellung verfügbar.  

  - **Anzahl nicht alphanumerischer Zeichen im Kennwort:**  
    Wenn der Kenn *Worttyp* auf **alphanumerisch**festgelegt ist, geben Sie die Mindestanzahl von Zeichensätzen an, die das Kennwort enthalten muss. Zu den Optionen gehören **0** bis **4** Sätze, der Standardwert ist **1**.
    
    Es gibt vier Zeichensätze:
    - Kleinbuchstaben
    - Großbuchstaben
    - Symbole
    - Zahlen

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen. Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Kompatibilitäts Richtlinie nicht richtig ausgewertet, wenn eine der folgenden Bedingungen zutrifft:

    - Minimale Kennwortlänge umfasst mehr als acht Zeichen.
    - Minimale Anzahl von Zeichensätzen ist mehr als zwei.

- **Minuten der Inaktivität vor Anforderung des Kennworts:**  
  Geben Sie die Leerlaufzeit ein, nach der ein Benutzer sein Kennwort erneut eingeben muss.

- **Kennwortablauf (Tage):**  
  Wählen Sie die Anzahl der Tage aus, nach der das Kennwort abläuft und Benutzer ein neues erstellen müssen.

- **Anzahl vorheriger Kennwörter zum Verhindern der Wiederverwendung:**  
  Geben Sie die Anzahl der zuvor verwendeten Kennwörter ein, die nicht erneut verwendet werden können.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung des Datenspeichers auf dem Gerät**:  
  - **Nicht konfiguriert** (*Standardeinstellung*)
  - **Erforderlich**: Verwenden Sie diese Einstellung, um die Datenspeicher auf Ihren Geräten zu verschlüsseln.


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](../fundamentals/scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für Geräte mit Windows 10 und höher](compliance-policy-create-windows.md).