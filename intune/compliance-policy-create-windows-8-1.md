---
title: Windows 8.1-Konformitätseinstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Liste aller Einstellungen, die Sie verwenden können, um Konformität für Ihre Windows 8.1- und Windows Phone 8.1-Geräte in Microsoft Intune festzulegen. Überprüfen Sie die Konformität mit der minimalen und maximalen Betriebssystemversion, legen Sie Kennwortbeschränkungen und -länge fest, aktivieren Sie die Verschlüsselung der Datenspeicherung und vieles mehr.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57a860edd99bfbbd41ff7df8fd98d0343f4f5ba6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "71304118"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Windows 8.1-Einstellungen, um Geräte mit Intune als konform oder nicht konform zu kennzeichnen

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen Konformitätseinstellungen aufgeführt und beschrieben, die Sie in Intune für Windows 8.1-Geräte festlegen können. Im Rahmen Ihrer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte) können Sie mit diesen Einstellungen einfache Kennwörter blockieren, eine minimale oder maximale Betriebssystemversion festlegen und vieles mehr.

Diese Funktion gilt für:

- Windows Phone 8.1
- Windows 8.1 und höher

Als Intune-Administrator verwenden Sie diese Konformitätseinstellungen, um die Ressourcen Ihrer Organisation zu schützen. Weitere Informationen zu Konformitätsrichtlinien und ihren Aufgaben finden Sie unter [Erste Schritte bei der Gerätekonformität](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen einer Konformitätsrichtlinie](create-compliance-policy.md#create-the-policy) Wählen Sie als **Plattform** die Option **Windows Phone 8.1** oder **Windows 8.1 und höher**aus.

## <a name="device-properties"></a>Geräteeigenschaften

- **Mindestversion des Betriebssystems erforderlich**: Geben Sie die zulässige Mindestversion ein. Wenn ein Gerät die Anforderung an die Mindestversion des Betriebssystems nicht erfüllt, wird es als nicht konform gemeldet. Ein Link zur Vorgehensweise zum Upgrade wird angezeigt. Der Endbenutzer kann ein Upgrade seines Geräts durchführen, und anschließend auf die Unternehmensressourcen zugreifen.
- **Maximale Version des Betriebssystems**: Geben Sie die zulässige maximale Version ein. Wenn auf einem Gerät eine neuere Betriebssystemversion verwendet wird, als die Regel erlaubt, wird der Zugriff auf Unternehmensressourcen gesperrt. Der Benutzer wird dazu aufgefordert, sich an den zuständigen IT-Administrator zu wenden. Das Gerät kann nicht auf Ressourcen der Organisation zugreifen, bis Sie die Regel dahingehend ändern, dass die betreffende Betriebssystemversion zugelassen wird.

Windows 8.1-PCs geben die Version **3** zurück. Wenn die Regel für die Betriebssystemversion für Windows auf Windows 8.1 festgelegt ist, wird das betreffende Gerät als nicht kompatibel gemeldet, selbst wenn auf ihm Windows 8.1 installiert ist.

## <a name="system-security"></a>Systemsicherheit

### <a name="password"></a>Kennwort

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

    Wenn Sie eine höhere Anzahl festlegen, muss der Benutzer ein komplexeres Kennwort erstellen. Für Geräte, auf die mit einem Microsoft-Konto zugegriffen wird, wird die Konformitätsrichtlinie in diesem Fall nicht korrekt ausgewertet:

    - Wenn die minimale Kennwortlänge mehr als acht Zeichen umfasst.
    - Oder wenn die minimale Anzahl von Zeichensätzen mehr als zwei ist.

- **Maximale Anzahl von Minuten der Inaktivität vor erneuter Anforderung des Kennworts**: Geben Sie die Leerlaufzeit an, nach der ein Benutzer sein Kennwort erneut eingeben muss.
- **Kennwortablauf (Tage):** Wählen Sie die Anzahl von Tagen aus, bevor das Kennwort abläuft und ein neues erstellt werden muss.
- **Anzahl der vorherigen Kennwörter zur Verhinderung von Wiederverwendung**: Geben Sie die Anzahl der bereits verwendeten Kennwörtern an, die nicht erneut verwendet werden dürfen.

### <a name="encryption"></a>Verschlüsselung

- **Verschlüsselung auf mobilem Gerät anfordern**: Sie können **Erforderlich** festlegen, sodass das Gerät verschlüsselt sein muss, um eine Verbindung mit Datenspeicherressourcen herstellen zu können.

Wählen Sie **OK** > **Erstellen** aus, um die Änderungen zu speichern.

## <a name="next-steps"></a>Nächste Schritte

- [Hinzufügen von Aktionen für nicht kompatible Geräte](actions-for-noncompliance.md) und [Verwenden von Bereichsmarkierungen zum Filtern von Richtlinien](scope-tags.md).
- [Überwachen Ihrer Konformitätsrichtlinien](compliance-policy-monitor.md).
- Siehe die [Einstellungen für Kompatibilitätsrichtlinien für Geräte mit Windows 10 und höher](compliance-policy-create-windows.md).